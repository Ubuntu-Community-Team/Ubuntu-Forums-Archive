---
title: "HDMI and IPOD"
date: 2012-02-13
forum: General Help
---

### Post by thunder_god on 2012-02-13
Hello!

I have two questions.

I use the latest version of linux but i cannot connect my computer to my television with HDMI cabel. I tryed to search for new screens but nothing happened. Does anyone has a solution?
The other thing is how to synchronize music from my computer to my ipod touch. Is that possible?How?

Thanks for the help.
Regards

---

### Post by cortman on 2012-02-13
Hi!
Addressing your HDMI issue: 
With the TV plugged in: open a terminal (Ctrl+Alt+t) and type

```
xrandr
```

and paste the output. It may be as simple as running

```
xrandr --output HDMI1
```.

On your iPod issue, I forget if Rhythmbox or Banshee supports iPod synchronization, I believe one of them does. Google might find some results for you.

---

### Post by thunder_god on 2012-02-16
The HDMI is still not working.
It show up this message when i did that:

bruno@bruno-M740TU-N-M760TU-N-W7X0TUN:~$ xrandr --output HDMI1
xrandr: Failed to get size of gamma for output default
warning: output HDMI1 not found; ignoring
bruno@bruno-M740TU-N-M760TU-N-W7X0TUN:~$

---

### Post by cortman on 2012-02-16
Sounds like your HDMI ports aren't recognized. Run plain old

```
xrandr
```

and post output. Also

```
lspci
```

and post it. You probably need a driver.

---

### Post by thunder_god on 2012-02-17
bruno@bruno-M740TU-N-M760TU-N-W7X0TUN:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G98M [GeForce G 105M] (rev a1)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
07:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
bruno@bruno-M740TU-N-M760TU-N-W7X0TUN:~$

---

### Post by cortman on 2012-02-17
You may need an updated driver. Here's a [blog post]("http://mygeekopinions.blogspot.com/2011/06/how-to-install-nvidia-2750907-driver-in.html") that explains how to get it. Follow the instructions given there, and post back with what happens.
Good luck!

---

### Post by thunder_god on 2012-02-17
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

bruno@bruno-M740TU-N-M760TU-N-W7X0TUN:~$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
[sudo] password for bruno: 
You are about to add the following PPA to your system:
 X Updates
 Updated versions of X.org drivers, libraries, etc. for Ubuntu.

This PPA is for stable upstream releases of X.org components.  If you're looking for something even more bleeding-edge, please see the xorg-edgers PPA.  Or, if you're actually wanting backports of the current stable X stack to an older Ubuntu release, see the x-backports PPA.

While Ubuntu-X does not officially support these packages, if you discover problems when installing these debs please feel free to report bugs to launchpad.  However, please make sure to clearly state that you are running packages from this PPA so we know the fixes need to come here.

If you are uprading from one release to another with this PPA activated, please install the ppa-purge package and use it to downgrade everything in here beforehand. sudo ppa-purge ppa:ubuntu-x-swat/x-updates will do it.
 More info: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.HkmbcP9JTs --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9
gpg: requisitando chave AF1CDFA9 de servidor hkp - keyserver.ubuntu.com
gpg: chave AF1CDFA9: chave pública "Launchpad PPA for Ubuntu-X" importada
gpg: ultimamente não encontradas chaves confiáveis
gpg: Número total processado: 1
gpg:               importados: 1  (RSA: 1)
bruno@bruno-M740TU-N-M760TU-N-W7X0TUN:~$ sudo apt-get update
Ign [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric InRelease
Ign [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports InRelease                   
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric Release.gpg                           
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Obter:1 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]       
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports Release.gpg                 
Obter:2 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg [198 B]               
Obter:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                   
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric Release                               
Obter:4 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates Release [40,8 kB]         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Obter:5 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release [5922 B]                  
Obter:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9747 B]                      
Obter:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                    
Obter:8 [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages [3939 B]    
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports Release                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Obter:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources [3384 B]                 
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/universe TranslationIndex             
Obter:10 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/main Sources [123 kB]    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Obter:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages [6625 B]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Obter:12 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Obter:13 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release [40,8 kB]         
Obter:14 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/restricted Sources [1337 B]
Obter:15 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/universe Sources [42,8 kB]
Obter:16 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/multiverse Sources [3662 B]
Obter:17 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/main i386 Packages [288 kB]
Obter:18 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [2968 B]
Obter:19 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/universe i386 Packages [96,0 kB]
Obter:20 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [6355 B]
Obter:21 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/main TranslationIndex [74 B]
Obter:22 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Obter:23 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [71 B]
Obter:24 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/main Sources                
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/restricted Sources          
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/universe Sources            
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/multiverse Sources          
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/main i386 Packages          
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/restricted i386 Packages    
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/universe i386 Packages      
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages    
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/main TranslationIndex       
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex 
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex 
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/universe TranslationIndex   
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/main Translation-pt                   
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/main Translation-pt_BR                
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/multiverse Translation-pt             
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/multiverse Translation-pt_BR          
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/restricted Translation-pt             
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/restricted Translation-pt_BR          
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/universe Translation-pt               
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/universe Translation-pt_BR            
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/universe Translation-en               
Obter:25 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/main Translation-en [135 kB]
Obter:26 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/multiverse Translation-en [3524 B]
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Obter:27 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/universe Translation-en [57,7 kB]
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/main Translation-en         
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/multiverse Translation-en   
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/restricted Translation-en   
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/universe Translation-en     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-pt_PT             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-pt                
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-pt_BR             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Obter:28 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources [29,3 kB]    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-pt_PT                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-pt                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-pt_BR      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en         
Obter:29 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources [14 B]
Obter:30 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources [10,8 kB]
Obter:31 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources [1645 B]
Obter:32 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [80,1 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt_PT                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt_BR
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Obter:33 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]
Obter:34 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages [28,8 kB]
Obter:35 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages [3355 B]
Obter:36 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex [73 B]
Obter:37 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex [72 B]
Obter:38 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex [70 B]
Obter:39 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex [73 B]
Obter:40 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en [43,5 kB]
Obter:41 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en [1494 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
Obter:42 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en [20,1 kB]
Obtidos 1092 kB em 3s (303 kB/s)         
A ler as listas de pacotes... Pronto
bruno@bruno-M740TU-N-M760TU-N-W7X0TUN:~$ sudo apt-get install nvidia-current
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
Serão actualizados os seguintes pacotes:
  nvidia-current
1 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 39 não actualizados.
É necessário obter 33,4 MB de arquivos.
Após esta operação, serão utilizados 6033 kB adicionais de espaço em disco.
Obter:1 [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) oneiric/main nvidia-current i386 295.20-0ubuntu1~oneiric~xup1 [33,4 MB]
Obtidos 33,4 MB em 3min 14s (172 kB/s)                                         
(A ler a base de dados ... 249618 ficheiros e directórios actualmente instalados.)
A preparar para substituir nvidia-current 280.13-0ubuntu6 (a usar .../nvidia-current_295.20-0ubuntu1~oneiric~xup1_i386.deb) ...
Removing all DKMS Modules
Done.
A descompactar substituto nvidia-current ...
A processar 'triggers' para man-db ...
A instalar nvidia-current (295.20-0ubuntu1~oneiric~xup1) ...
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.0.0-16-generic-pae
Loading new nvidia-current-295.20 DKMS files...
Building only for 3.0.0-16-generic-pae
Building for architecture i686
Building initial module for 3.0.0-16-generic-pae
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-16-generic-pae/updates/dkms/

depmod....

DKMS: install Completed.
A processar 'triggers' para bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
A processar 'triggers' para gnome-menus ...
A processar 'triggers' para initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-16-generic-pae
bruno@bruno-M740TU-N-M760TU-N-W7X0TUN:~$

---

### Post by thunder_god on 2012-02-17
Still not working. what i should try now?

---

### Post by cortman on 2012-02-17
Hi, sorry that didn't fix it... Can you run

```
xrandr
```

In the terminal and post the output?

---

### Post by thunder_god on 2012-02-18
bruno@bruno-M740TU-N-M760TU-N-W7X0TUN:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1366 x 768, maximum 1366 x 768
default connected 1366x768+0+0 0mm x 0mm
   1366x768       50.0* 
   1360x768       51.0  
   1024x768       52.0     53.0     54.0  
   960x540        55.0  
   840x525        56.0     57.0  
   832x624        58.0  
   800x600        59.0     60.0     61.0     62.0     63.0  
   800x512        64.0  
   720x450        65.0  
   720x400        66.0  
   700x525        67.0     68.0  
   680x384        69.0     70.0  
   640x512        71.0     72.0  
   640x480        73.0     74.0     75.0     76.0     77.0     78.0  
   640x400        79.0  
   640x350        80.0  
   576x432        81.0     82.0     83.0     84.0     85.0     86.0     87.0  
   512x384        88.0     89.0     90.0     91.0     92.0  
   416x312        93.0  
   400x300        94.0     95.0     96.0     97.0     98.0  
   360x200        99.0  
   320x240       100.0    101.0    102.0    103.0  
   320x200       104.0  
   320x175       105.0  
bruno@bruno-M740TU-N-M760TU-N-W7X0TUN:~$

---

### Post by cortman on 2012-02-18
It looks as though the HDMI isn't recognized or enabled. Installing the nvidia drivers should also have installed the nvidia configuration application. See if you can detect/enable with it.

---

### Post by thunder_god on 2012-02-19
I’m a beginner. How can i do that?

---

### Post by cortman on 2012-02-19
It's a GUI app that should have installed with your drivers- try finding it in your applications menu? Not sure what DE you're running, so I can't get much more specific.

---

### Post by gordintoronto on 2012-02-19
I think you are running Ubuntu 11.10? Click on the Dash, and type "nvidia". It should show you "NVIDIA Server Settings, or something like that. Run it.

Click on the second line on the left side,tell us what you see.

---

### Post by thunder_god on 2012-02-23
chi mei optoelectronics corp. 
  1366*768

---

### Post by Ms. Daisy on 2012-02-23
> **thunder_god said:**
> The other thing is how to synchronize music from my computer to my ipod touch. Is that possible?How? 
I'll leave cortman to help you with the HDMI cable issue. (I have nothing to add on that front)

But in regards to the ipod,

Here's a link for a bunch of possible solutions for itunes on Linux.
[http://www.ubuntuka.com/itunes-ubuntu-linux/](http://www.ubuntuka.com/itunes-ubuntu-linux/)

---

### Post by ojlnx on 2012-02-25
I've got the same problem with the HDMI output after I upgraded to 11.10 ( 3.0.0-16-generic-pae). it's definitely not caused by a faulty cable (it works with other device). I tried different kernel and updated the video driver but still no luck. :confused:

---

### Post by thunder_god on 2012-02-25
Ok. So im not the only one.
Can it be a fail on the OS?

---

