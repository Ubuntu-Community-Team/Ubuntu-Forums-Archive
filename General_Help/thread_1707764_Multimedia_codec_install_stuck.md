---
title: "Multimedia codec install stuck"
date: 2011-03-15
forum: General Help
---

### Post by lsutiger on 2011-03-15
I just bought a new hard drive and decided to upgrade to 10.4.2 (I was running 9.10).
I started doing the normal customizations that come with a new install. I tried to play an mp3 file and the sstem offered to install the new gstreamer codecs(ffmpeg,fluendo-mp3, and plugins-ugly).
I click on install and it is stuck at preparing libavformat52. The terminal details state:```
dpkg:warning: files list file for package 'libavformat52' missing, assuming package has no files currently installed.
Preparing to replace libavformat52 4:0.5.1-1ubuntu1 (using.../libavformat52_4%3a0.5.1-1ubuntu1_i386.deb)...
Unpacking replacement libavformat52
```

It was stuck so long and I could not kill it (did not know what to kill), so I rebooted once before this message.

What should I do?

Thank you in advance!

---

### Post by Krytarik on 2011-03-15
Please run the following commands in a terminal and post error messages, if you get any:
```

sudo dpkg --configure -a
sudo apt-get --fix-broken install
sudo apt-get --fix-missing install
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by lsutiger on 2011-03-16
Thank you for the reply!
Here's the whole session:
```
complexity@complexity-laptop:~$ sudo dpkg --configure -a
[sudo] password for complexity: 
complexity@complexity-laptop:~$ sudo apt-get --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libavformat52
The following packages will be upgraded:
  libavformat52
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/719kB of archives.
After this operation, 1,573kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `libavformat52' missing, assuming package has no files currently installed.
(Reading database ... 158295 files and directories currently installed.)
Preparing to replace libavformat52 4:0.5.1-1ubuntu1 (using .../libavformat52_4%3a0.5.1-1ubuntu1_i386.deb) ...
Unpacking replacement libavformat52 ...
Setting up libavformat52 (4:0.5.1-1ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
complexity@complexity-laptop:~$ sudo apt-get --fix-missing install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
complexity@complexity-laptop:~$ sudo apt-get update
Hit http://ppa.launchpad.net jaunty Release.gpg
Ign http://ppa.launchpad.net/bogdanb/amarok14/ubuntu/ jaunty/main Translation-en_US
Get:1 http://security.ubuntu.com lucid-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US  
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://ppa.launchpad.net jaunty Release    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:2 http://us.archive.ubuntu.com lucid-updates Release.gpg [198B]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release 
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:3 http://security.ubuntu.com lucid-security Release [44.7kB]
Get:4 http://us.archive.ubuntu.com lucid-updates Release [44.7kB]          
Hit http://ppa.launchpad.net jaunty/main Packages                              
Hit http://ppa.launchpad.net jaunty/main Sources                               
Hit http://us.archive.ubuntu.com lucid/main Packages                   
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Get:5 http://security.ubuntu.com lucid-security/main Packages [157kB]
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Get:6 http://us.archive.ubuntu.com lucid-updates/main Packages [458kB]
Get:7 http://security.ubuntu.com lucid-security/restricted Packages [14B]   
Get:8 http://security.ubuntu.com lucid-security/main Sources [48.4kB]          
Get:9 http://us.archive.ubuntu.com lucid-updates/restricted Packages [3,240B]  
Get:10 http://us.archive.ubuntu.com lucid-updates/main Sources [182kB]         
Get:11 http://security.ubuntu.com lucid-security/restricted Sources [14B]      
Get:12 http://security.ubuntu.com lucid-security/universe Packages [62.9kB]    
Get:13 http://security.ubuntu.com lucid-security/universe Sources [19.3kB]     
Get:14 http://security.ubuntu.com lucid-security/multiverse Packages [1,995B]  
Get:15 http://security.ubuntu.com lucid-security/multiverse Sources [651B]
Get:16 http://us.archive.ubuntu.com lucid-updates/restricted Sources [1,443B]  
Get:17 http://us.archive.ubuntu.com lucid-updates/universe Packages [187kB]    
Get:18 http://us.archive.ubuntu.com lucid-updates/universe Sources [69.7kB]    
Get:19 http://us.archive.ubuntu.com lucid-updates/multiverse Packages [8,427B] 
Get:20 http://us.archive.ubuntu.com lucid-updates/multiverse Sources [4,369B]  
Fetched 1,293kB in 9s (133kB/s)                                                
Reading package lists... Done
complexity@complexity-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libgssapi-krb5-2 libk5crypto3 libkrb5-3 libkrb5support0 libtiff4
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 748kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libk5crypto3 1.8.1+dfsg-2ubuntu0.8 [96.8kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.8 [121kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libkrb5-3 1.8.1+dfsg-2ubuntu0.8 [351kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libkrb5support0 1.8.1+dfsg-2ubuntu0.8 [42.8kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libtiff4 3.9.2-2ubuntu0.5 [137kB]
Fetched 748kB in 9s (80.4kB/s)                                                 
(Reading database ... 158308 files and directories currently installed.)
Preparing to replace libk5crypto3 1.8.1+dfsg-2ubuntu0.6 (using .../libk5crypto3_1.8.1+dfsg-2ubuntu0.8_i386.deb) ...
Unpacking replacement libk5crypto3 ...
Preparing to replace libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.6 (using .../libgssapi-krb5-2_1.8.1+dfsg-2ubuntu0.8_i386.deb) ...
Unpacking replacement libgssapi-krb5-2 ...
Preparing to replace libkrb5-3 1.8.1+dfsg-2ubuntu0.6 (using .../libkrb5-3_1.8.1+dfsg-2ubuntu0.8_i386.deb) ...
Unpacking replacement libkrb5-3 ...
Preparing to replace libkrb5support0 1.8.1+dfsg-2ubuntu0.6 (using .../libkrb5support0_1.8.1+dfsg-2ubuntu0.8_i386.deb) ...
Unpacking replacement libkrb5support0 ...
Preparing to replace libtiff4 3.9.2-2ubuntu0.4 (using .../libtiff4_3.9.2-2ubuntu0.5_i386.deb) ...
Unpacking replacement libtiff4 ...
Setting up libkrb5support0 (1.8.1+dfsg-2ubuntu0.8) ...

Setting up libk5crypto3 (1.8.1+dfsg-2ubuntu0.8) ...

Setting up libkrb5-3 (1.8.1+dfsg-2ubuntu0.8) ...

Setting up libgssapi-krb5-2 (1.8.1+dfsg-2ubuntu0.8) ...

Setting up libtiff4 (3.9.2-2ubuntu0.5) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by Krytarik on 2011-03-16
Nice to see that at least the upgrades worked. But "libavformat52" didn't get fixed.
Try to re-install it:
```
sudo apt-get install --reinstall libavformat52
```
But I'm afraid that will not work, neither would 'remove' work then.

---

### Post by lsutiger on 2011-03-16
Well, it seemed to do something...```
complexity@complexity-laptop:~$ sudo apt-get install --reinstall libavformat52
[sudo] password for complexity: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/719kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 158308 files and directories currently installed.)
Preparing to replace libavformat52 4:0.5.1-1ubuntu1 (using .../libavformat52_4%3a0.5.1-1ubuntu1_i386.deb) ...
Unpacking replacement libavformat52 ...
Setting up libavformat52 (4:0.5.1-1ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```


What do I do from here to get the codecs working?

---

### Post by Krytarik on 2011-03-16
Wow, that's great! :D

As for the codecs, make sure you have at least the following packages installed (output of "dpkg -l|grep gstreamer"):
```
ii  bluez-gstreamer                        4.60-0ubuntu8                                   Bluetooth GStreamer support
ii  gstreamer0.10-alsa                     0.10.28-1                                       GStreamer plugin for ALSA
ii  gstreamer0.10-ffmpeg                   0.10.11-1~ppa1~lucid1                           FFmpeg plugin for GStreamer
ii  gstreamer0.10-fluendo-mp3              0.10.12.debian-2                                Fluendo mp3 decoder GStreamer plugin
ii  gstreamer0.10-gnonlin                  0.10.15-1                                       non-linear editing module for GStreamer
ii  gstreamer0.10-nice                     0.0.10-2build1                                  ICE library (GStreamer plugin)
ii  gstreamer0.10-plugins-bad              0.10.18-1ubuntu1                                GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-multiverse   0.10.18-0ubuntu1                                GStreamer plugins from the "bad" set (Multiv
ii  gstreamer0.10-plugins-base             0.10.28-1                                       GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps        0.10.28-1                                       GStreamer helper programs from the "base" se
ii  gstreamer0.10-plugins-good             0.10.21-1ubuntu3                                GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly             0.10.14-1                                       GStreamer plugins from the "ugly" set
ii  gstreamer0.10-plugins-ugly-multiverse  0.10.14-0ubuntu2                                GStreamer plugins from the "ugly" set (Multi
ii  gstreamer0.10-pulseaudio               0.10.21-1ubuntu3                                GStreamer plugin for PulseAudio
ii  gstreamer0.10-tools                    0.10.28-1                                       Tools for use with GStreamer
ii  gstreamer0.10-x                        0.10.28-1                                       GStreamer plugins for X11 and Pango
ii  libgstreamer-plugins-base0.10-0        0.10.28-1                                       GStreamer libraries from the "base" set
ii  libgstreamer0.10-0                     0.10.28-1                                       Core GStreamer libraries and elements

```Unfortunately, I don't know where to check which packages were initially selected for installation, if it is possible at all.

---

### Post by mastablasta on 2011-03-16
the easiest way to install all codecs (except for DVD decoding) is to simply install restricted-extras from the software center (or synaptics or kpackagekit).

---

### Post by Krytarik on 2011-03-16
> **mastablasta said:**
> the easiest way to install all codecs (except for DVD decoding) is to simply install restricted-extras from the software center (or synaptics or kpackagekit).
Thanks for the tip, nice meta-package! The actual names would be "ubuntu-restricted-extras" or "kubuntu-restricted-extras" respectively. However it wants to install the "extra" versions of the ffmpeg lib packages, which seem to be slimmed down versions, but I didn't ever get a definitive info which one is to prefer. So, like you said, "the easiest way", I leave it to the OP. ;)

EDIT: I somehow expect that the package "gstreamer0.10-ffmpeg" would do the same, since it is just pulled by "*ubuntu-restricted-extras".

---

### Post by lsutiger on 2011-03-16
Thank you all for the replies! I now can listen to music!

---

