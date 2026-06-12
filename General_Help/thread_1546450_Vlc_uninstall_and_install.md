---
title: "Vlc uninstall and install"
date: 2010-08-05
forum: General Help
---

### Post by vagelism on 2010-08-05
Hello to all.
I am a newbie.
I tried to update the VLC in my eee pc.
I manage to uninstall it instead and now I can not reinstall it.
Any help?
Thank you for your help.

---

### Post by elliotn on 2010-08-05
sudo apt-get install vlc

---

### Post by snowpine on 2010-08-05
The usual method would be to install it from the Ubuntu Software Center or from the terminal with the following commands:

```
sudo apt-get update 
sudo apt-get install vlc
```

If you are getting error messages, please copy & paste them here so we can help. :)

---

### Post by elliotn on 2010-08-05
> **elliotn said:**
> sudo apt-get install vlc

Oh do that in terminal

---

### Post by vagelism on 2010-08-05
> **snowpine said:**
> The usual method would be to install it from the Ubuntu Software Center or from the terminal with the following commands:

```
sudo apt-get update 
sudo apt-get install vlc
```

If you are getting error messages, please copy & paste them here so we can help. :)


HERE IS THE UPDATE COMMAND RESULTS


vagelism@unknown:~$ sudo apt-get update 
[sudo] password for vagelism: 
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy Release.gpg
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [197B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/main Translation-en_US                  
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg [307B]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-en_US                      
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg [307B]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US             
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Get:7 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [11.7kB]                     
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/restricted Translation-en_US            
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [65.9kB]                       
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release [65.9kB]                         
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [65.9kB]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release                                     
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Get:12 [http://dl.google.com](http://dl.google.com) stable Release [2544B]                             
Get:13 [http://www.array.org](http://www.array.org) hardy Release.gpg [197B]                           
Get:14 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates Release.gpg [189B]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]              
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Get:16 [http://dl.google.com](http://dl.google.com) stable/main Packages [1067B]                       
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                      
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Ign [http://www.array.org](http://www.array.org) hardy/eeepc Translation-en_US                         
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy Release                                 
Get:17 [http://www.array.org](http://www.array.org) hardy Release [1549B]                              
Get:18 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates Release [58.5kB]             
Get:19 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates Release [58.5kB]
Get:20 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates Release [58.5kB]
Get:21 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates Release [58.5kB]
Get:22 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates Release [58.5kB]
Get:23 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates Release [58.5kB]
Get:24 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates Release [58.5kB]
Get:25 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates Release [58.5kB]
Get:26 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates Release [58.5kB]
Get:27 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates Release [58.5kB]
Get:28 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates Release [58.5kB]
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/main Packages                           
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/restricted Packages                     
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/main Sources                            
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/restricted Sources                                                                                                             
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [278kB]                                                                                                
Get:30 [http://www.array.org](http://www.array.org) hardy/eeepc Packages [4240B]                                                                                                              
Err [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates Release                                                                                                                
  
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/universe Packages                                                                                                              
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/universe Sources                                                                                                               
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/multiverse Packages                                                                                                            
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/multiverse Sources                                                                                                             
Err [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/main Sources                                                                                                                   
  404 Not Found
Err [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/universe Sources                                                                                                               
  404 Not Found
Err [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/multiverse Sources                                                                                                             
  404 Not Found
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [11.3kB]                                                                                         
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [86.3kB]                                                                                                
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [935B]                                                                                            
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [131kB]                                                                                            
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [26.1kB]                                                                                            
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [14.6kB]                                                                                         
Get:37 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [1742B]                                                                                           
Fetched 674kB in 16s (41.4kB/s)                                                                                                                                       
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 638ABCA0FA3A1271
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 638ABCA0FA3A1271
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://gr.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
vagelism@unknown:~$

---

### Post by snowpine on 2010-08-05
Your software sources are an absolute mess. :( You have software repositories for 3 different Ubuntu releases, plus a whole bunch of unsupported 3rd party repositories. 

I'm sorry but I don't know how to fix this (maybe another user can help you). I would recommend a fresh reinstall, and in the future, install applications from the tested and trusted Ubuntu repositories using the Ubuntu Software Center. Don't add anything to your software sources unless you are 100% certain you know what you're doing. :(

---

### Post by vagelism on 2010-08-05
> **snowpine said:**
> The usual method would be to install it from the Ubuntu Software Center or from the terminal with the following commands:

```
sudo apt-get update 
sudo apt-get install vlc
```

If you are getting error messages, please copy & paste them here so we can help. :)

HERE IS THE INSTALL VLC COMMAND

vagelism@unknown:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdvbpsi4 libebml0 libiso9660-5 libmatroska0 libtar libvcdinfo0 libvlc0
  libwxbase2.6-0 libwxgtk2.6-0 libxosd2 vlc-nox vlc-plugin-pulse
Suggested packages:
  xfonts-base-transcoded mozilla-plugin-vlc
Recommended packages:
  videolan-doc
The following NEW packages will be installed:
  libdvbpsi4 libebml0 libiso9660-5 libmatroska0 libtar libvcdinfo0 libvlc0
  libwxbase2.6-0 libwxgtk2.6-0 libxosd2 vlc vlc-nox vlc-plugin-pulse
0 upgraded, 13 newly installed, 0 to remove and 1 not upgraded.
Need to get 5939kB/10.7MB of archives.
After this operation, 30.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/universe libdvbpsi4 0.1.5-3
  404 Not Found
Err [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/universe libebml0 0.7.7-3.1
  404 Not Found
Err [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/main libiso9660-5 0.78.2+dfsg1-2ubuntu1
  404 Not Found
Err [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/universe libmatroska0 0.8.1-1
  404 Not Found
Err [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/universe libtar 1.2.11-4
  404 Not Found
Err [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/universe libvcdinfo0 0.7.23-4ubuntu1
  404 Not Found
Err [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy-updates/multiverse libvlc0 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.3
  404 Not Found
Err [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/universe libwxbase2.6-0 2.6.3.2.2-2ubuntu4
  404 Not Found
Err [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/universe libwxgtk2.6-0 2.6.3.2.2-2ubuntu4
  404 Not Found
Err [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) hardy/universe libxosd2 2.2.14-1.4            
  404 Not Found
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse libvlc0 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.3 [827kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse vlc-plugin-pulse 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.3 [6962B]                              
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse vlc 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.3 [1140kB]                                          
Fetched 1974kB in 3min45s (8760B/s)                                                                                                                                   
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/pool/universe/libd/libdvbpsi4/libdvbpsi4_0.1.5-3_i386.deb](http://gr.archive.ubuntu.com/ubuntu/pool/universe/libd/libdvbpsi4/libdvbpsi4_0.1.5-3_i386.deb)  404 Not Found
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/pool/universe/libe/libebml/libebml0_0.7.7-3.1_i386.deb](http://gr.archive.ubuntu.com/ubuntu/pool/universe/libe/libebml/libebml0_0.7.7-3.1_i386.deb)  404 Not Found
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/pool/main/libc/libcdio/libiso9660-5_0.78.2+dfsg1-2ubuntu1_i386.deb](http://gr.archive.ubuntu.com/ubuntu/pool/main/libc/libcdio/libiso9660-5_0.78.2+dfsg1-2ubuntu1_i386.deb)  404 Not Found
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/pool/universe/libm/libmatroska/libmatroska0_0.8.1-1_i386.deb](http://gr.archive.ubuntu.com/ubuntu/pool/universe/libm/libmatroska/libmatroska0_0.8.1-1_i386.deb)  404 Not Found
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/pool/universe/libt/libtar/libtar_1.2.11-4_i386.deb](http://gr.archive.ubuntu.com/ubuntu/pool/universe/libt/libtar/libtar_1.2.11-4_i386.deb)  404 Not Found
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/pool/universe/v/vcdimager/libvcdinfo0_0.7.23-4ubuntu1_i386.deb](http://gr.archive.ubuntu.com/ubuntu/pool/universe/v/vcdimager/libvcdinfo0_0.7.23-4ubuntu1_i386.deb)  404 Not Found
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/libwxbase2.6-0_2.6.3.2.2-2ubuntu4_i386.deb](http://gr.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/libwxbase2.6-0_2.6.3.2.2-2ubuntu4_i386.deb)  404 Not Found
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/libwxgtk2.6-0_2.6.3.2.2-2ubuntu4_i386.deb](http://gr.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/libwxgtk2.6-0_2.6.3.2.2-2ubuntu4_i386.deb)  404 Not Found
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/pool/universe/x/xosd/libxosd2_2.2.14-1.4_i386.deb](http://gr.archive.ubuntu.com/ubuntu/pool/universe/x/xosd/libxosd2_2.2.14-1.4_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
vagelism@unknown:~$

---

### Post by Irony on 2010-08-05
Go to synaptic and change your archives to another country.

---

### Post by vagelism on 2010-08-05
> **Irony said:**
> Go to synaptic and change your archives to another country.

How can I do it?
Thank you!

---

### Post by Irony on 2010-08-06
Just like I said; go to synaptic then repositories then change server to another server. Then hit reload and then see if vlc installs.

---

### Post by vagelism on 2010-08-06
> **irony said:**
> just like i said; go to synaptic then repositories then change server to another server. Then hit reload and then see if vlc installs.

great!!!
It works just great!!!
Thank you!

---

