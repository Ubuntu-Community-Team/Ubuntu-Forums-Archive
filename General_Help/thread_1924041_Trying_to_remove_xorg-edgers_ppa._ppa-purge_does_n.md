---
title: "Trying to remove xorg-edgers ppa. ppa-purge does not work."
date: 2012-02-11
forum: General Help
---

### Post by jschall1 on 2012-02-11
How do I resolve this?

```
jschall@jon-laptop:/etc/apt/sources.list.d$ sudo ppa-purge xorg-edgers
Updating packages lists
PPA to be removed: xorg-edgers ppa
comm: file 2 is not in sorted order
Package revert list generated:
 ia32-libs/oneiric lib32ffi6/oneiric libcairo2/oneiric libcairo2-dev/oneiric 
libcairo-gobject2/oneiric libcairo-script-interpreter2/oneiric libdrm2/oneiric 
libdrm-dev/oneiric libdrm-intel1/oneiric libdrm-nouveau1a/oneiric 
libdrm-radeon1/oneiric libegl1-mesa/oneiric libegl1-mesa-drivers/oneiric 
libffi6/oneiric libgbm1/oneiric libgl1-mesa-dev/oneiric libgl1-mesa-dri/oneiric 
libgl1-mesa-glx/oneiric libglapi-mesa/oneiric libgles2-mesa/oneiric 
libglu1-mesa/oneiric libglu1-mesa-dev/oneiric libkms1/oneiric 
libllvm3.0/oneiric libopenvg1-mesa/oneiric libpciaccess0/oneiric 
libpixman-1-0/oneiric libpixman-1-dev/oneiric libva1/oneiric 
libva-x11-1/oneiric libwayland0/oneiric libxatracker1/oneiric 
linux-libc-dev/oneiric mesa-common-dev/oneiric nvidia-current/oneiric 
nvidia-settings/oneiric x11-common/oneiric x11proto-input-dev/oneiric 
xorg/oneiric xserver-common/oneiric xserver-xorg/oneiric 
xserver-xorg-core/oneiric xserver-xorg-input-all/oneiric 
xserver-xorg-input-evdev/oneiric xserver-xorg-input-mouse/oneiric 
xserver-xorg-input-synaptics/oneiric xserver-xorg-input-vmmouse/oneiric 
xserver-xorg-input-wacom/oneiric xserver-xorg-video-all/oneiric 
xserver-xorg-video-ati/oneiric xserver-xorg-video-cirrus/oneiric 
xserver-xorg-video-fbdev/oneiric xserver-xorg-video-intel/oneiric 
xserver-xorg-video-mach64/oneiric xserver-xorg-video-mga/oneiric 
xserver-xorg-video-neomagic/oneiric xserver-xorg-video-nouveau/oneiric 
xserver-xorg-video-openchrome/oneiric xserver-xorg-video-qxl/oneiric 
xserver-xorg-video-r128/oneiric xserver-xorg-video-radeon/oneiric 
xserver-xorg-video-s3/oneiric xserver-xorg-video-savage/oneiric 
xserver-xorg-video-siliconmotion/oneiric xserver-xorg-video-sis/oneiric 
xserver-xorg-video-sisusb/oneiric xserver-xorg-video-tdfx/oneiric 
xserver-xorg-video-trident/oneiric xserver-xorg-video-vesa/oneiric 
xserver-xorg-video-vmware/oneiric

Disabling xorg-edgers PPA from 
/etc/apt/sources.list.d/xorg-edgers-ppa-oneiric.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Release 'oneiric' for 'libllvm3.0' was not found
E: Release 'oneiric' for 'libxatracker1' was not found
Unable to find an archive "oneiric" for the package "libllvm3.0"
Unable to find an archive "oneiric" for the package "libxatracker1"
Unable to find an archive "oneiric" for the package "libllvm3.0"
Unable to find an archive "oneiric" for the package "libxatracker1"
The following packages will be DOWNGRADED:
  ia32-libs lib32ffi6 libcairo-gobject2 libcairo-script-interpreter2 libcairo2{b} libcairo2-dev libdrm-dev 
  libdrm-intel1{b} libdrm-nouveau1a{b} libdrm-radeon1{b} libdrm2{b} libegl1-mesa libegl1-mesa-drivers libffi6{b} 
  libgbm1 libgl1-mesa-dev libgl1-mesa-dri{b} libgl1-mesa-glx{b} libglapi-mesa{b} libgles2-mesa libglu1-mesa 
  libglu1-mesa-dev libkms1 libopenvg1-mesa libpciaccess0{b} libpixman-1-0{b} libpixman-1-dev libwayland0 
  linux-libc-dev mesa-common-dev nvidia-current nvidia-settings x11-common x11proto-input-dev xorg 
  xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev 
  xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom 
  xserver-xorg-video-all xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev 
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic 
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128 
  xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion 
  xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident 
  xserver-xorg-video-vesa xserver-xorg-video-vmware 
The following packages will be REMOVED:
  libllvm3.0{u} libxatracker1{u} libxcb-glx0{u} 
0 packages upgraded, 0 newly installed, 66 downgraded, 3 to remove and 1 not upgraded.
Need to get 8,778 kB/102 MB of archives. After unpacking 14.1 MB will be freed.
The following packages have unmet dependencies:
  libdrm-radeon1: Breaks: libdrm-radeon1 (!= 2.4.26-1ubuntu1) but 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric is installed.
  libdrm-radeon1: Breaks: libdrm-radeon1 (!= 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric) but 2.4.26-1ubuntu1 is to be installed.
  libgl1-mesa-dri: Breaks: libgl1-mesa-dri (!= 7.11-0ubuntu3) but 8.0.0~git20120209+8.0.7aef8397-0ubuntu0sarvatt~oneiric is installed.
  libgl1-mesa-dri: Breaks: libgl1-mesa-dri (!= 8.0.0~git20120209+8.0.7aef8397-0ubuntu0sarvatt~oneiric) but 7.11-0ubuntu3 is to be installed.
  libgl1-mesa-glx: Breaks: libgl1-mesa-glx (!= 7.11-0ubuntu3) but 8.0.0~git20120209+8.0.7aef8397-0ubuntu0sarvatt~oneiric is installed.
  libgl1-mesa-glx: Breaks: libgl1-mesa-glx (!= 8.0.0~git20120209+8.0.7aef8397-0ubuntu0sarvatt~oneiric) but 7.11-0ubuntu3 is to be installed.
  libcairo2: Breaks: libcairo2 (!= 1.10.2-6ubuntu3) but 1.11.3+git20120210.f7eaf37f-0ubuntu0ricotz~oneiric0 is installed.
  libcairo2: Breaks: libcairo2 (!= 1.11.3+git20120210.f7eaf37f-0ubuntu0ricotz~oneiric0) but 1.10.2-6ubuntu3 is to be installed.
  libglapi-mesa: Breaks: libglapi-mesa (!= 7.11-0ubuntu3) but 8.0.0~git20120209+8.0.7aef8397-0ubuntu0sarvatt~oneiric is installed.
  libglapi-mesa: Breaks: libglapi-mesa (!= 8.0.0~git20120209+8.0.7aef8397-0ubuntu0sarvatt~oneiric) but 7.11-0ubuntu3 is to be installed.
  libffi6: Breaks: libffi6 (!= 3.0.11~rc1-2) but 3.0.11~rc1-5~oneiric1 is installed.
  libffi6: Breaks: libffi6 (!= 3.0.11~rc1-5~oneiric1) but 3.0.11~rc1-2 is to be installed.
  libdrm2: Breaks: libdrm2 (!= 2.4.26-1ubuntu1) but 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric is installed.
  libdrm2: Breaks: libdrm2 (!= 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric) but 2.4.26-1ubuntu1 is to be installed.
  libpixman-1-0: Breaks: libpixman-1-0 (!= 0.22.2-1) but 0.24.2-1~oneiric1 is installed.
  libpixman-1-0: Breaks: libpixman-1-0 (!= 0.24.2-1~oneiric1) but 0.22.2-1 is to be installed.
  libdrm-nouveau1a: Breaks: libdrm-nouveau1a (!= 2.4.26-1ubuntu1) but 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric is installed.
  libdrm-nouveau1a: Breaks: libdrm-nouveau1a (!= 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric) but 2.4.26-1ubuntu1 is to be installed.
  libdrm-intel1: Breaks: libdrm-intel1 (!= 2.4.26-1ubuntu1) but 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric is installed.
  libdrm-intel1: Breaks: libdrm-intel1 (!= 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric) but 2.4.26-1ubuntu1 is to be installed.
  libpciaccess0: Breaks: libpciaccess0 (!= 0.12.1-2) but 0.12.902-1~oneiric1 is installed.
  libpciaccess0: Breaks: libpciaccess0 (!= 0.12.902-1~oneiric1) but 0.12.1-2 is to be installed.
The following actions will resolve these dependencies:

       Remove the following packages:                                    
1)       flashplugin-downloader                                          
2)       ia32-libs-multiarch                                             
3)       libacl1                                                         
4)       libasound2                                                      
5)       libasound2-plugins                                              
6)       libasyncns0                                                     
7)       libatk1.0-0                                                     
8)       libattr1                                                        
9)       libaudio2                                                       
10)      libavahi-client3                                                
11)      libavahi-common3                                                
12)      libc6                                                           
13)      libcairo2                                                       
14)      libcomerr2                                                      
15)      libcups2                                                        
16)      libcupsimage2                                                   
17)      libcurl3                                                        
18)      libdatrie1                                                      
19)      libdb5.1                                                        
20)      libdbus-1-3                                                     
21)      libdrm-intel1                                                   
22)      libdrm-nouveau1a                                                
23)      libdrm-radeon1                                                  
24)      libdrm2                                                         
25)      libexpat1                                                       
26)      libffi6                                                         
27)      libflac8                                                        
28)      libfontconfig1                                                  
29)      libfreetype6                                                    
30)      libgcc1                                                         
31)      libgcrypt11                                                     
32)      libgdbm3                                                        
33)      libgdk-pixbuf2.0-0                                              
34)      libgl1-mesa-dri                                                 
35)      libgl1-mesa-glx                                                 
36)      libglapi-mesa                                                   
37)      libglib2.0-0                                                    
38)      libgnutls26                                                     
39)      libgpg-error0                                                   
40)      libgssapi-krb5-2                                                
41)      libgtk2.0-0                                                     
42)      libice6                                                         
43)      libidn11                                                        
44)      libjack-jackd2-0                                                
45)      libjasper1                                                      
46)      libjpeg62                                                       
47)      libjson0                                                        
48)      libk5crypto3                                                    
49)      libkeyutils1                                                    
50)      libkrb5-3                                                       
51)      libkrb5support0                                                 
52)      liblcms1                                                        
53)      libldap-2.4-2                                                   
54)      libllvm2.9                                                      
55)      libllvm3.0                                                      
56)      libmng1                                                         
57)      libnspr4                                                        
58)      libnspr4-0d                                                     
59)      libnss3                                                         
60)      libnss3-1d                                                      
61)      libogg0                                                         
62)      libpango1.0-0                                                   
63)      libpciaccess0                                                   
64)      libpcre3                                                        
65)      libpixman-1-0                                                   
66)      libpng12-0                                                      
67)      libpulse0                                                       
68)      libqt4-dbus                                                     
69)      libqt4-declarative                                              
70)      libqt4-designer                                                 
71)      libqt4-network                                                  
72)      libqt4-opengl                                                   
73)      libqt4-qt3support                                               
74)      libqt4-script                                                   
75)      libqt4-scripttools                                              
76)      libqt4-sql                                                      
77)      libqt4-svg                                                      
78)      libqt4-test                                                     
79)      libqt4-xml                                                      
80)      libqt4-xmlpatterns                                              
81)      libqtcore4                                                      
82)      libqtgui4                                                       
83)      librtmp0                                                        
84)      libsamplerate0                                                  
85)      libsasl2-2                                                      
86)      libsasl2-modules                                                
87)      libselinux1                                                     
88)      libsm6                                                          
89)      libsndfile1                                                     
90)      libspeexdsp1                                                    
91)      libsqlite3-0                                                    
92)      libssl1.0.0                                                     
93)      libstdc++6                                                      
94)      libtasn1-3                                                      
95)      libthai0                                                        
96)      libtiff4                                                        
97)      libuuid1                                                        
98)      libvorbis0a                                                     
99)      libvorbisenc2                                                   
100)     libwrap0                                                        
101)     libx11-6                                                        
102)     libx11-xcb1                                                     
103)     libxau6                                                         
104)     libxcb-glx0                                                     
105)     libxcb-render0                                                  
106)     libxcb-shm0                                                     
107)     libxcb1                                                         
108)     libxcomposite1                                                  
109)     libxcursor1                                                     
110)     libxdamage1                                                     
111)     libxdmcp6                                                       
112)     libxext6                                                        
113)     libxfixes3                                                      
114)     libxft2                                                         
115)     libxi6                                                          
116)     libxinerama1                                                    
117)     libxrandr2                                                      
118)     libxrender1                                                     
119)     libxss1                                                         
120)     libxt6                                                          
121)     libxxf86vm1                                                     
122)     nspluginviewer                                                  
123)     nspluginwrapper                                                 
124)     zlib1g                                                          

       Leave the following dependencies unresolved:                      
125)     ia32-libs recommends ia32-libs-multiarch                        
126)     libqtgui4 recommends libcups2                                   
127)     flashplugin-downloader recommends libasound2-plugins (>= 1.0.16)
128)     ia32-libs-multiarch recommends libgl1-mesa-dri                  
129)     libgl1-mesa-glx recommends libgl1-mesa-dri (>= 7.2)
```

Specifically, the problem is these:
```
  libdrm-radeon1: Breaks: libdrm-radeon1 (!= 2.4.26-1ubuntu1) but 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric is installed.
  libdrm-radeon1: Breaks: libdrm-radeon1 (!= 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric) but 2.4.26-1ubuntu1 is to be installed.
  libgl1-mesa-dri: Breaks: libgl1-mesa-dri (!= 7.11-0ubuntu3) but 8.0.0~git20120209+8.0.7aef8397-0ubuntu0sarvatt~oneiric is installed.
  libgl1-mesa-dri: Breaks: libgl1-mesa-dri (!= 8.0.0~git20120209+8.0.7aef8397-0ubuntu0sarvatt~oneiric) but 7.11-0ubuntu3 is to be installed.
  libgl1-mesa-glx: Breaks: libgl1-mesa-glx (!= 7.11-0ubuntu3) but 8.0.0~git20120209+8.0.7aef8397-0ubuntu0sarvatt~oneiric is installed.
  libgl1-mesa-glx: Breaks: libgl1-mesa-glx (!= 8.0.0~git20120209+8.0.7aef8397-0ubuntu0sarvatt~oneiric) but 7.11-0ubuntu3 is to be installed.
  libcairo2: Breaks: libcairo2 (!= 1.10.2-6ubuntu3) but 1.11.3+git20120210.f7eaf37f-0ubuntu0ricotz~oneiric0 is installed.
  libcairo2: Breaks: libcairo2 (!= 1.11.3+git20120210.f7eaf37f-0ubuntu0ricotz~oneiric0) but 1.10.2-6ubuntu3 is to be installed.
  libglapi-mesa: Breaks: libglapi-mesa (!= 7.11-0ubuntu3) but 8.0.0~git20120209+8.0.7aef8397-0ubuntu0sarvatt~oneiric is installed.
  libglapi-mesa: Breaks: libglapi-mesa (!= 8.0.0~git20120209+8.0.7aef8397-0ubuntu0sarvatt~oneiric) but 7.11-0ubuntu3 is to be installed.
  libffi6: Breaks: libffi6 (!= 3.0.11~rc1-2) but 3.0.11~rc1-5~oneiric1 is installed.
  libffi6: Breaks: libffi6 (!= 3.0.11~rc1-5~oneiric1) but 3.0.11~rc1-2 is to be installed.
  libdrm2: Breaks: libdrm2 (!= 2.4.26-1ubuntu1) but 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric is installed.
  libdrm2: Breaks: libdrm2 (!= 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric) but 2.4.26-1ubuntu1 is to be installed.
  libpixman-1-0: Breaks: libpixman-1-0 (!= 0.22.2-1) but 0.24.2-1~oneiric1 is installed.
  libpixman-1-0: Breaks: libpixman-1-0 (!= 0.24.2-1~oneiric1) but 0.22.2-1 is to be installed.
  libdrm-nouveau1a: Breaks: libdrm-nouveau1a (!= 2.4.26-1ubuntu1) but 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric is installed.
  libdrm-nouveau1a: Breaks: libdrm-nouveau1a (!= 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric) but 2.4.26-1ubuntu1 is to be installed.
  libdrm-intel1: Breaks: libdrm-intel1 (!= 2.4.26-1ubuntu1) but 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric is installed.
  libdrm-intel1: Breaks: libdrm-intel1 (!= 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric) but 2.4.26-1ubuntu1 is to be installed.
  libpciaccess0: Breaks: libpciaccess0 (!= 0.12.1-2) but 0.12.902-1~oneiric1 is installed.
  libpciaccess0: Breaks: libpciaccess0 (!= 0.12.902-1~oneiric1) but 0.12.1-2 is to be installed.
```
And then it wigs out and wants to remove everything.

---

### Post by moustaki on 2012-02-18
Hello!

Looks like the same issue as mentioned in [https://bugs.launchpad.net/ubuntu/+source/ppa-purge/+bug/892886](https://bugs.launchpad.net/ubuntu/+source/ppa-purge/+bug/892886) (ppa-purge is not multiarch aware).

Comment #7 did the trick for me.

y

---

