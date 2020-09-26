# raventeam
Merhaba ben ravnxlord

dan  os . yol  içe aktarma  var
dan  lib . bruter  ithalatı  Bruter
dan  lib . oturum  içe aktarma  Oturumu 
dan  lib . görüntüleme  içe aktarma  Ekran
dan  lib . const  içe aktarma  kimlik bilgileri , modlar
dan  argparse  ithalat  ArgumentParser , ArgumentTypeError


sınıf  Motor ( nesne ):

    def  __init__ ( self , username , thread , passlist_path , is_color ):  
        öz . bruter  =  Yok 
        öz . resume  =  False 
        öz . is_alive  =  Doğru 
        öz . thread  =  thread
        öz . kullanıcı adı  =  kullanıcı adı
        öz . passlist_path  =  passlist_path
        öz . display  =  Ekran ( is_color = is_color )
        öz . session  =  Session ( kullanıcı adı , passlist_path )
    
    def  passlist_path_exists ( self ):
        eğer  değil  var ( öz . passlist_path ):
            öz . ekran . uyarı ( 'Şifre listesine giden geçersiz yol' )
             Yanlış dönüş
        dönüş  Doğru 
    
    def  session_exists ( kendi ):
         kendine dön . oturum . var
    
    def  create_bruter ( self ):
        öz . Bruter  =  Bruter ( öz . adı , kendi kendine . parçacığı , kendi kendine . passlist_path , kendi kendine . devam )
    
    def  get_user_resp ( öz ):
         kendine dön . ekran . komut istemi ( 'Saldırıya devam etmek ister misiniz? [y / n]:' )
    
    def  write_to_file ( self , password ):
        ile  açık ( kimlik bilgileri , 'kısmındaki' ) olarak  f :
            data  =  'Kullanıcı Adı: {} \ n Şifre: {} \ n \ n ' . biçimi ( öz . kullanıcı adı . Başlık (), şifre )
            f . yazma ( veri )

    def  start ( self ):
        eğer  değil  kendini . passlist_path_exists ():
            öz . is_alive  =  False 
        
        eğer  öz . session_exists () ve  self . is_alive :
            resp  =  Yok 

            dene :
                resp  =  öz . get_user_resp ()
            hariç :
                öz . is_alive  =  False 
                        
            eğer  respin  ve  öz . is_alive :
                eğer  resp . şerit (). alt () ==  'y' :
                    öz . resume  =  True 
        
        eğer  öz . is_alive :
            öz . create_bruter ()

            dene :
                öz . bruter . başlangıç ()
             KeyboardInterrupt hariç :
                öz . bruter . durdur ()
                öz . bruter . ekran . shutdown ( self . bruter . last_password ,
                                            öz . bruter . password_manager . girişimleri , len ( öz . Bruter . tarayıcılar ))
            nihayet :
                öz . durdur ()
    
    def  stop ( kendi kendine ):
        eğer  öz . is_alive :

            öz . bruter . durdur ()
            öz . is_alive  =  False 

            eğer  öz . bruter . password_manager . is_read  ve  self değil  . bruter . is_found ve self değil . bruter . password_manager . list_size :   
                öz . bruter . ekran . stats_not_found ( self . bruter . last_password ,
                                                    öz . bruter . password_manager . girişimleri , len ( öz . Bruter . tarayıcılar ))
            
            eğer  öz . bruter . is_found :
                öz . write_to_file ( self . bruter . parola )
                öz . bruter . ekran . stats_found ( kendine . bruter . şifre ,
                                                öz . bruter . password_manager . girişimleri , len ( öz . Bruter . tarayıcılar ))
                

def  valid_int ( n ):
    eğer  değil  n . isdigit ():
        yükseltmek  ArgumentTypeError ( 'mod bir sayı olmalıdır' )

    n  =  int ( n )

    eğer  n  >  3 :
        yükseltmek  ArgumentTypeError ( 'bir mod için en fazla 3 konumundadır' )

    eğer  n  <  0 :
         ArgumentTypeError değerini yükseltin ( 'bir mod için minimum 0'dır' )

    dönüş  n

def  args ():
    args  =  ArgumentParser ()
    args . add_argument ( 'kullanıcı adı' , yardım = 'e-posta veya kullanıcı adı' )
    args . add_argument ( 'passlist' , help = 'şifre listesi' )
    args . add_argument ( '-nc' , '--no-color' , dest = 'color' , action = 'store_true' , help = 'renkleri devre dışı bırak' )
    args . add_argument ( '-m' , '--mode' , default = 2 , type = valid_int , help = 'modlar: 0 => 16 bot; 1 => 8 bot; 2 => 4 bot; 3 => 2 bot' )
    dönmek  args . parse_args ()


eğer  __name__  ==  '__main__' :
    arugments  =  args ()
    mod  =  arugments . mod 
    kullanıcı adı  =  tartışmalar . Kullanıcı adı
    passlist  =  arugments . geçiş listesi
    is_color  =  Doğru  eğer  değil  arugments . başka renk  Yanlış  
    Motor ( kullanıcı adı , modlar [ mod ], şifre listesi , is_color ). başlangıç ()
