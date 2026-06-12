---
title: "Software-Center Doesn't work"
date: 2011-07-26
forum: General Help
---

### Post by sthanheykel on 2011-07-26
Every time I try to open the Software-Center It doesn't works, I've tried to reinstall, but the problem still, and I can't find the solution anywhere :(
When I try to open it with the terminal, it shows this message:
root@linux-ubuntu:/home/linux# software-center
No protocol specified
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
/usr/share/software-center/softwarecenter/view/widgets/mkit.py:89: Warning: invalid (NULL) pointer instance
  w = gtk.Window()
/usr/share/software-center/softwarecenter/view/widgets/mkit.py:89: Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  w = gtk.Window()
/usr/share/software-center/softwarecenter/view/widgets/mkit.py:90: GtkWarning: IA__gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  pc = w.get_pango_context()
/usr/share/software-center/softwarecenter/view/widgets/mkit.py:90: PangoWarning: pango_context_set_font_description: assertion `context != NULL' failed
  pc = w.get_pango_context()
/usr/share/software-center/softwarecenter/view/widgets/mkit.py:90: PangoWarning: pango_context_set_base_dir: assertion `context != NULL' failed
  pc = w.get_pango_context()
/usr/share/software-center/softwarecenter/view/widgets/mkit.py:90: PangoWarning: pango_context_set_language: assertion `context != NULL' failed
  pc = w.get_pango_context()
Traceback (most recent call last):
  File "/usr/bin/software-center", line 88, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 43, in <module>
    from softwarecenter.view.widgets.mkit import floats_from_string
  File "/usr/share/software-center/softwarecenter/view/widgets/mkit.py", line 140, in <module>
    EM = get_em_value()
  File "/usr/share/software-center/softwarecenter/view/widgets/mkit.py", line 91, in get_em_value
    l = pango.Layout(pc)
TypeError: Pango.Layout.__init__() argument 1 must be pango.Context, not None

---

### Post by Paddy Landau on 2011-07-26
Why are you running it from root? The Software Centre should be run from a normal user. What version of Ubuntu are you using?

---

### Post by sthanheykel on 2011-07-26
I use ubuntu 10.10 version, I've tried to run it as normal user and this appeared:
linux@linux-ubuntu:~$ software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 90, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 379, in __init__
    self.config = get_config()
  File "/usr/share/software-center/softwarecenter/backend/config.py", line 43, in get_config
    _software_center_config = SoftwareCenterConfig(SOFTWARE_CENTER_CONFIG_FILE)
  File "/usr/share/software-center/softwarecenter/backend/config.py", line 30, in __init__
    self.read(self.configfile)
  File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
    self._read(fp, filename)
  File "/usr/lib/python2.6/ConfigParser.py", line 482, in _read
    raise MissingSectionHeaderError(fpname, lineno, line)
ConfigParser.MissingSectionHeaderError: File contains no section headers.
file: /home/linux/.config/software-center/softwarecenter.cfg, line: 1
'ction)[ 0/1, 2147483647/1 ]; video/x-raw-yuv, format=(fourcc)IYUV, width=(int)[ 1, 2147483647 ], height=(int)[ 1, 2147483647 ], framerate=(fraction)[ 0/1, 2147483647/1 ]\x00GstElementFactory\x00videobalance\x00\x00\x00\x00\x00\x00\x00\x00\x02\x00\x00\x00\x02\x00\x00\x00\x00\x00\x00\x00Video balance\x00Filter/Effect/Video\x00Adjusts brightness, contrast, hue, saturation on a video stream\x00David Schleef <ds@schleef.org>\x00\x00\x00\x00\x01'

---

### Post by Paddy Landau on 2011-07-26
I'm sorry, that error is beyond me.

The only thing that puzzles me is why you needed to install Software Centre in the first place? It comes by default with Ubuntu. When you installed, did you do it through Synaptic Package Manager using the default repositories, or did you download something and install that?

---

### Post by sthanheykel on 2011-07-26
It came with Ubuntu, it worked fine some days and then this problem, so I read on a forum that I could fix it by reinstalling it with Synaptic, but now the problem still. :(

---

### Post by lkjoel on 2011-07-26
> **sthanheykel said:**
> It came with Ubuntu, it worked fine some days and then this problem, so I read on a forum that I could fix it by reinstalling it with Synaptic, but now the problem still. :(
Try this in a Terminal window:
```
sudo add-apt-repository ppa:lkjoel/apt-undo
sudo apt-get update; sudo apt-get install apt-undo
apt-undo purge software-center
apt-undo undo

```
Then try running Software Center

---

### Post by sthanheykel on 2011-07-26
linux@linux-ubuntu:~$ sudo update-manager -d
[sudo] password for linux: 
No protocol specified
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
No protocol specified
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 41, in <module>
    gtk.init_check()
RuntimeError: could not open display
linux@linux-ubuntu:~$ sudo add-apt-repository ppa:lkjoel/apt-undo
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv B5BA6675C3C7E882049C5A0C20B1405FC2255669
gpg: requisitando chave C2255669 de servidor hkp - keyserver.ubuntu.com
gpg: chave C2255669: chave pública "Launchpad PPA for Joel Leclerc" importada
gpg: Número total processado: 1
gpg:               importados: 1  (RSA: 1)
linux@linux-ubuntu:~$ sudo apt-get update; sudo apt-get install apt-undo
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick Release.gpg                     
Ign [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Atingido [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick/main Translation-pt     
Atingido [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                         
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Atingido [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick/main Translation-pt_BR  
Ign [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Atingido [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-pt
Atingido [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-pt_BR
Ign [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Atingido [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-pt
Atingido [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-pt_BR
Ign [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Obter:1 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg [198B]        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-pt   
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-pt              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-pt_BR           
Atingido [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/lkjoel/apt-undo/ubuntu/](http://ppa.launchpad.net/lkjoel/apt-undo/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/lkjoel/apt-undo/ubuntu/](http://ppa.launchpad.net/lkjoel/apt-undo/ubuntu/) maverick/main Translation-pt
Atingido [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick/universe Translation-pt 
Atingido [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick/universe Translation-pt_BR
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick-updates Release.gpg             
Ign [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-pt  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-pt_BR
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-pt
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-pt_BR
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-pt
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-pt_BR
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-pt
Ign [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-pt_BR
Ign [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-pt
Ign [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-pt_BR
Ign [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Atingido [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                        
Ign [http://ppa.launchpad.net/lkjoel/apt-undo/ubuntu/](http://ppa.launchpad.net/lkjoel/apt-undo/ubuntu/) maverick/main Translation-pt_BR
Atingido [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                         
Ign [http://ppa.launchpad.net/silverwave/testing5/ubuntu/](http://ppa.launchpad.net/silverwave/testing5/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/silverwave/testing5/ubuntu/](http://ppa.launchpad.net/silverwave/testing5/ubuntu/) maverick/main Translation-pt
Ign [http://ppa.launchpad.net/silverwave/testing5/ubuntu/](http://ppa.launchpad.net/silverwave/testing5/ubuntu/) maverick/main Translation-pt_BR
Atingido [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                         
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-pt
Ign [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-pt
Ign [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-pt_BR
Ign [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-pt_BR
Obter:2 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release [31,4kB]          
Ign [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-pt
Ign [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-pt_BR
Atingido [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                  
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick Release                         
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick-updates Release                 
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-pt_BR
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Atingido [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                             
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick/main Sources                    
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick/restricted Sources              
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick/universe Sources                
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick/multiverse Sources              
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick/main i386 Packages              
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick/restricted i386 Packages        
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick/universe i386 Packages
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick/multiverse i386 Packages        
Atingido [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                             
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick-updates/main Sources            
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick-updates/restricted Sources      
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick-updates/universe Sources        
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick-updates/multiverse Sources      
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick-updates/main i386 Packages      
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick-updates/universe i386 Packages  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Atingido [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                        
Atingido [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                  
Atingido [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                        
Atingido [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
  404  Not Found
Obter:3 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources [46,2kB]     
Obter:4 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources [14B]  
Obter:5 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources [19,4kB] 
Obter:6 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources [1.758B]
Obter:7 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages [155kB]
Obter:8 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages [14B]
Obter:9 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages [76,3kB]
Obter:10 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages [3.746B]
Baixados 334kB em 2min 2s (2.735B/s)                                           
W: Falhou ao buscar [http://ppa.launchpad.net/lkjoel/apt-undo/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/lkjoel/apt-undo/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Falhou ao buscar [http://ppa.launchpad.net/lkjoel/apt-undo/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/lkjoel/apt-undo/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Alguns arquivos de índice falharam para baixar, eles foram ignorados ou os antigos foram usados no lugar.
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
E: Impossível encontrar o pacote apt-undo
linux@linux-ubuntu:~$ apt-undo purge software-center
apt-undo: command not found
linux@linux-ubuntu:~$ apt-undo undo
apt-undo: command not found
linux@linux-ubuntu:~$

---

### Post by sthanheykel on 2011-07-26
I use a Portuguese version of Ubuntu, if you want me to translate any phrase of the terminal, just ask and I will ;)

---

### Post by lkjoel on 2011-07-26
Type in a Terminal window:
```
sudo sed -i 's:maverick:natty:g' /etc/apt/sources.list.d/lkjoel-apt-undo-*
sudo apt-get update
sudo apt-get install apt-undo
apt-undo purge software-center
apt-undo undo
```

---

### Post by magdos on 2011-09-14
hello i seem to have the same problem with the ubuntu software-center 
and when i try to write the codes in the terminal it says 

 	Code:
 	markus@1337-HP-Mini-5103:~$ sudo apt-get install apt-undo
Indlæser pakkelisterne... Fejl!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: Pakkelisterne eller statusfilen kunne ikke tolkes eller åbnes.


translation:
markus@1337-HP-Mini-5103:~$ sudo apt-get install apt-undo
reading packlists... error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package-lists or the statusfile could not be interpreted or opened.

please help me

---

### Post by oldos2er on 2011-09-14
```
sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update
```

---

