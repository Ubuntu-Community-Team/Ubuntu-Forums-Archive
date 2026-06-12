---
title: "problem in 9.10"
date: 2009-11-01
forum: General Help
---

### Post by !! hack-back !! on 2009-11-01
hello ,
 i turned off the pc and when i turn on i found programs and pages i was opened open automatically but the system crashed then i go to 

System->Prefrences->Startup Applications 

then options 
 and i found mark on  

automatically remember running application when logging out

 i unmark then i restart the system  all thing okay but any program i open it didnt appear in the taskbar i go to 

visual effects 

i found it none i try to change it but i get msg   

desktop effects could not be enabled 

then i go to  System > Administration > Hardware Drives 

and no thing appear there is msg 

No proprietary drivers are in use on this system 

and this is what lspci command said


```
root@hackback:/home/hackback# lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
root@hackback:/home/hackback#


```


but before that happen i was putting the visual effects  to extra and every thing okay

and this pic for what iam talking about

[IMG]http://www.up-00.com/h4files/uKx28836.png[/IMG]

---

### Post by 133794m3r on 2009-11-02
Well what i can say is you almost definately need a gpu driver for your desktop effects and by that i mean a pretty decent one that can do some 3d rendering. What type of pc do you have? Maybe they don't have any linux drivers currently.

I read from another thread where someone had almost the same issue as you. And this is the exact command they used to get their video driver.

sudo apt-get update && sudo apt-get install xserver-xorg-video-intel

Also if that doesn't work apparently Super Ubuntu is working. So you may want to check that out.

[http://hacktolive.org/wiki/Super_OS](http://hacktolive.org/wiki/Super_OS)

They aparently got compiz to work by using super ubuntu but the other things didn't work try it out and tell me if it helps.

---

### Post by hossdozero on 2009-11-02
First, to fix the issue with your programs not being displayed in the task bar: Right-click on the task bar you want to display your programs, left click on  "Add to panel" scroll down until you see an item called "Window List" and left click on that. click the "Add" button. 

Next to fix your visual effects
Navigate to System >Administration >Hardware drivers. And click on the one that says "recommended" next to it then click activate.

After the drivers have finished installing,you should restart your computer.

Then you can go in and enable the visual effects.

On a side note I would also recommend adding compizconfig-settings-manager by opening a terminal and typing 

```
sudo apt-get install compizconfig-settings-manager
```

this will allow you to change a various number of visual effects by navigating to System >Preferences >Compizconfig settings manger.

I hope all of this helps you out.

---

### Post by !! hack-back !! on 2009-11-02
if the problem is in the driver installation so why it was working properly ?
and why the sound is working but no thing appear in hardware driver ?

and why when i open any program not appear in the task bar ?? look at the pic no thing down !

i make new user and files appear in the task bar but the same problem in visual efects and hardware drivers

but the most important now is to make files open appear down !

---

### Post by !! hack-back !! on 2009-11-02
thx for posting , i add the Window List and they appear now
but when i open Hardware drivers no thing said recommended

---

### Post by hossdozero on 2009-11-02
Sorry I misread your post, you can ignore what I said about the video drivers.:oops: 
You should follow 1337's advice and type

```
sudo apt-get update && sudo apt-get install xserver-xorg-video-intel
``` 

Hopefully that works 

and the reason the display works is because there are actually drivers running, They just happen to be the open source drivers that ubuntu uses by default, until a proprietary (from the manufacturer) driver is installed.

hope that helps.

---

### Post by !! hack-back !! on 2009-11-02
[IMG]http://www.up-00.com/h4files/t0X42191.png[/IMG]

---

### Post by !! hack-back !! on 2009-11-02
i did the command 

sudo apt-get update && sudo apt-get install xserver-xorg-video-intel



and that what i got 


```
hackback@hackback:~$ sudo apt-get update && sudo apt-get install xserver-xorg-video-intel
Hit http://lb.archive.ubuntu.com karmic Release.gpg
Get:1 http://packages.medibuntu.org jaunty Release.gpg [197B]                  
Ign http://lb.archive.ubuntu.com karmic/main Translation-en_US                 
Ign http://packages.medibuntu.org jaunty/free Translation-en_US                
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Ign http://lb.archive.ubuntu.com karmic/restricted Translation-en_US           
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US            
Ign http://lb.archive.ubuntu.com karmic/universe Translation-en_US             
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Hit http://ppa.launchpad.net karmic Release.gpg                                
Get:2 http://packages.medibuntu.org jaunty Release [11.7kB]                    
Ign http://packages.medibuntu.org jaunty Release                               
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Ign http://lb.archive.ubuntu.com karmic/multiverse Translation-en_US           
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://lb.archive.ubuntu.com karmic-updates Release.gpg                    
Hit http://packages.medibuntu.org jaunty/free Packages                         
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://packages.medibuntu.org jaunty/non-free Packages                     
Hit http://ppa.launchpad.net karmic Release                                    
Ign http://lb.archive.ubuntu.com karmic-updates/main Translation-en_US         
Hit http://security.ubuntu.com karmic-security Release                         
Ign http://lb.archive.ubuntu.com karmic-updates/restricted Translation-en_US   
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://ppa.launchpad.net karmic/main Packages                              
Ign http://lb.archive.ubuntu.com karmic-updates/universe Translation-en_US     
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/main Sources                   
Ign http://lb.archive.ubuntu.com karmic-updates/multiverse Translation-en_US  
Hit http://lb.archive.ubuntu.com karmic Release                               
Hit http://security.ubuntu.com karmic-security/restricted Sources              
Hit http://security.ubuntu.com karmic-security/universe Packages              
Hit http://security.ubuntu.com karmic-security/universe Sources               
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Hit http://lb.archive.ubuntu.com karmic-updates Release                        
Hit http://lb.archive.ubuntu.com karmic/main Packages                          
Hit http://security.ubuntu.com karmic-security/multiverse Sources              
Hit http://lb.archive.ubuntu.com karmic/restricted Packages                    
Hit http://lb.archive.ubuntu.com karmic/main Sources                           
Hit http://lb.archive.ubuntu.com karmic/restricted Sources                     
Hit http://lb.archive.ubuntu.com karmic/universe Packages                      
Hit http://lb.archive.ubuntu.com karmic/universe Sources                       
Hit http://lb.archive.ubuntu.com karmic/multiverse Packages                    
Hit http://lb.archive.ubuntu.com karmic/multiverse Sources                     
Hit http://lb.archive.ubuntu.com karmic-updates/main Packages
Hit http://lb.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://lb.archive.ubuntu.com karmic-updates/main Sources
Hit http://lb.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://lb.archive.ubuntu.com karmic-updates/universe Packages
Hit http://lb.archive.ubuntu.com karmic-updates/universe Sources
Hit http://lb.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://lb.archive.ubuntu.com karmic-updates/multiverse Sources
Fetched 198B in 14s (14B/s)
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
The following packages were automatically installed and are no longer required:
  libwildmidi0 libdc1394-22 libsoundtouch1c2 libdca0 libopenspc0 libfftw3-3
  libass3 libenca0 freepats libkate1 libcdaudio1 libmimic0 libdirac0c2a
  libofa0 libiptcdata0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
hackback@hackback:~$ 

```

---

### Post by !! hack-back !! on 2009-11-02
well i put the command 

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get updat

```

and now that what i get after 

sudo apt-get update && sudo apt-get install xserver-xorg-video-intel


```
hackback@hackback:~$ sudo apt-get update && sudo apt-get install xserver-xorg-video-intel
Hit http://lb.archive.ubuntu.com karmic Release.gpg                            
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Hit http://packages.medibuntu.org karmic Release.gpg                           
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Ign http://lb.archive.ubuntu.com karmic/main Translation-en_US                 
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://lb.archive.ubuntu.com karmic/restricted Translation-en_US           
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Ign http://lb.archive.ubuntu.com karmic/universe Translation-en_US             
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Hit http://ppa.launchpad.net karmic Release                                    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Hit http://packages.medibuntu.org karmic Release                               
Ign http://lb.archive.ubuntu.com karmic/multiverse Translation-en_US           
Hit http://ppa.launchpad.net karmic Release                                    
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://packages.medibuntu.org karmic/free Packages                         
Hit http://lb.archive.ubuntu.com karmic-updates Release.gpg                    
Hit http://packages.medibuntu.org karmic/non-free Packages                     
Hit http://ppa.launchpad.net karmic/main Packages                              
Ign http://lb.archive.ubuntu.com karmic-updates/main Translation-en_US         
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://security.ubuntu.com karmic-security/main Packages         
Ign http://lb.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://lb.archive.ubuntu.com karmic-updates/universe Translation-en_US    
Hit http://security.ubuntu.com karmic-security/restricted Packages            
Hit http://security.ubuntu.com karmic-security/main Sources                   
Hit http://security.ubuntu.com karmic-security/restricted Sources             
Hit http://security.ubuntu.com karmic-security/universe Packages              
Ign http://lb.archive.ubuntu.com karmic-updates/multiverse Translation-en_US  
Hit http://lb.archive.ubuntu.com karmic Release                               
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://lb.archive.ubuntu.com karmic-updates Release
Hit http://lb.archive.ubuntu.com karmic/main Packages               
Hit http://security.ubuntu.com karmic-security/multiverse Sources             
Hit http://lb.archive.ubuntu.com karmic/restricted Packages                   
Hit http://lb.archive.ubuntu.com karmic/main Sources
Hit http://lb.archive.ubuntu.com karmic/restricted Sources
Hit http://lb.archive.ubuntu.com karmic/universe Packages
Hit http://lb.archive.ubuntu.com karmic/universe Sources
Hit http://lb.archive.ubuntu.com karmic/multiverse Packages
Hit http://lb.archive.ubuntu.com karmic/multiverse Sources
Hit http://lb.archive.ubuntu.com karmic-updates/main Packages
Hit http://lb.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://lb.archive.ubuntu.com karmic-updates/main Sources
Hit http://lb.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://lb.archive.ubuntu.com karmic-updates/universe Packages
Hit http://lb.archive.ubuntu.com karmic-updates/universe Sources
Hit http://lb.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://lb.archive.ubuntu.com karmic-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
The following packages were automatically installed and are no longer required:
  libwildmidi0 libdc1394-22 libsoundtouch1c2 libdca0 libopenspc0 libfftw3-3
  libass3 libenca0 freepats libkate1 libcdaudio1 libmimic0 libdirac0c2a
  libofa0 libiptcdata0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
hackback@hackback:~$ 

```

---

### Post by hossdozero on 2009-11-02
Okay it looks like there is a problem with your repository authentication

go ahead and right-click on this link and select "save link as" save it to your desktop (for easy access)

[http://packages.medibuntu.org/medibuntu-key.gpg]("http://packages.medibuntu.org/medibuntu-key.gpg")

Next go to System >Administration >Software sources and click the "Authentication" tab then click on the "Import Key File" button and go to where you saved the file, click on it, and click OK.

then try running the command again

```
sudo apt-get update && sudo apt-get install xserver-xorg-video-intel
```

if all goes well you should see much of the same output but without the "W: GPG error:"

EDIT: Sorry, I missed the "xserver-xorg-video-intel is already the newest version."

although you should still fix that authentication issue.

And that kind of puts us back at square one.

---

### Post by !! hack-back !! on 2009-11-02
and i made 
[FONT=monospace]apt-get autoremove

but the same problem !
[/FONT]

---

### Post by !! hack-back !! on 2009-11-02
man look up i solved the "W: GPG error:" with the command 

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get updat

---

### Post by !! hack-back !! on 2009-11-02
now when i put the command 

sudo apt-get update && sudo apt-get install xserver-xorg-video-intel



i got 

```
root@hackback:/home/hackback# sudo apt-get update && sudo apt-get install xserver-xorg-video-intel
Hit http://packages.medibuntu.org karmic Release.gpg
Hit http://lb.archive.ubuntu.com karmic Release.gpg                            
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://lb.archive.ubuntu.com karmic/main Translation-en_US                 
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Ign http://lb.archive.ubuntu.com karmic/restricted Translation-en_US           
Hit http://packages.medibuntu.org karmic Release                               
Ign http://lb.archive.ubuntu.com karmic/universe Translation-en_US             
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://packages.medibuntu.org karmic/free Packages                         
Ign http://lb.archive.ubuntu.com karmic/multiverse Translation-en_US           
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://packages.medibuntu.org karmic/non-free Packages                     
Hit http://lb.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Hit http://ppa.launchpad.net karmic Release                                    
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Ign http://lb.archive.ubuntu.com karmic-updates/main Translation-en_US         
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://security.ubuntu.com karmic-security Release               
Ign http://lb.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://security.ubuntu.com karmic-security/main Packages                   
Ign http://lb.archive.ubuntu.com karmic-updates/universe Translation-en_US
Hit http://security.ubuntu.com karmic-security/restricted Packages            
Hit http://security.ubuntu.com karmic-security/main Sources                   
Ign http://lb.archive.ubuntu.com karmic-updates/multiverse Translation-en_US  
Hit http://lb.archive.ubuntu.com karmic Release                               
Hit http://security.ubuntu.com karmic-security/restricted Sources             
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://lb.archive.ubuntu.com karmic-updates Release
Hit http://lb.archive.ubuntu.com karmic/main Packages               
Hit http://security.ubuntu.com karmic-security/universe Sources               
Hit http://security.ubuntu.com karmic-security/multiverse Packages            
Hit http://lb.archive.ubuntu.com karmic/restricted Packages
Hit http://lb.archive.ubuntu.com karmic/main Sources
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://lb.archive.ubuntu.com karmic/restricted Sources
Hit http://lb.archive.ubuntu.com karmic/universe Packages
Hit http://lb.archive.ubuntu.com karmic/universe Sources
Hit http://lb.archive.ubuntu.com karmic/multiverse Packages
Hit http://lb.archive.ubuntu.com karmic/multiverse Sources
Hit http://lb.archive.ubuntu.com karmic-updates/main Packages
Hit http://lb.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://lb.archive.ubuntu.com karmic-updates/main Sources
Hit http://lb.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://lb.archive.ubuntu.com karmic-updates/universe Packages
Hit http://lb.archive.ubuntu.com karmic-updates/universe Sources
Hit http://lb.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://lb.archive.ubuntu.com karmic-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
root@hackback:/home/hackback# 

```

---

### Post by !! hack-back !! on 2009-11-02
iam waiting some one can solve this problem :( :(

---

### Post by !! hack-back !! on 2009-11-03
up

---

### Post by !! hack-back !! on 2009-11-03
up

---

