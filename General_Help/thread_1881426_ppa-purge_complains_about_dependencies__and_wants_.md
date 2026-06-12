---
title: "ppa-purge complains about dependencies  and wants to remove half my system"
date: 2011-11-15
forum: General Help
---

### Post by mutley89 on 2011-11-15
Yesterday I upgraded my graphics  drivers with this ppa (before everything graphics related was the  default ubuntu, which worked but performance with openGL related  programs was poor): 

[https://launchpad.net/~oibaf/+archive/graphics-drivers/]("https://launchpad.net/%7Eoibaf/+archive/graphics-drivers/") 

Anyway I want to revert it. The linked page suggests using ppa-purge to  remove it.  When I try this It complains about dependencies and suggests  removing 300 odd unrelated and important packages to solve this:
```

$ sudo ppa-purge ppa:oibaf/graphics-drivers
Updating packages lists
PPA to be removed: oibaf graphics-drivers
comm: file 2 is not in sorted order
Package revert list generated:
 libdrm-dev/oneiric libdrm-intel1/oneiric libdrm-nouveau1a/oneiric 
libdrm-radeon1/oneiric libdrm2/oneiric libgl1-mesa-dev/oneiric 
libgl1-mesa-dri/oneiric libgl1-mesa-dri-dbg/oneiric libgl1-mesa-glx/oneiric 
libglapi-mesa/oneiric libglu1-mesa/oneiric libglu1-mesa-dev/oneiric 
libkms1/oneiric libtxc-dxtn-dev/oneiric libtxc-dxtn0/oneiric libvpx0/oneiric 
mesa-common-dev/oneiric xserver-xorg-video-ati/oneiric 
xserver-xorg-video-intel/oneiric xserver-xorg-video-nouveau/oneiric 
xserver-xorg-video-radeon/oneiric

Disabling oibaf PPA from 
/etc/apt/sources.list.d/oibaf-graphics-drivers-oneiric.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Release &#8216;oneiric&#8217; for &#8216;libtxc-dxtn-dev&#8217; was not found
E: Release &#8216;oneiric&#8217; for &#8216;libtxc-dxtn0&#8217; was not found
Unable to find an archive "oneiric" for the package "libtxc-dxtn-dev"
Unable to find an archive "oneiric" for the package "libtxc-dxtn0"
Unable to find an archive "oneiric" for the package "libtxc-dxtn-dev"
Unable to find an archive "oneiric" for the package "libtxc-dxtn0"
The following packages will be DOWNGRADED:
  libdrm-dev libdrm-intel1{b} libdrm-nouveau1a{b} libdrm-radeon1{b}  libdrm2{b} libgl1-mesa-dev libgl1-mesa-dri{b} libgl1-mesa-dri-dbg  libgl1-mesa-glx{b} libglapi-mesa{b} libglu1-mesa 
  libglu1-mesa-dev libkms1 libvpx0 mesa-common-dev  xserver-xorg-video-ati xserver-xorg-video-intel  xserver-xorg-video-nouveau xserver-xorg-video-radeon 
0 packages upgraded, 0 newly installed, 19 downgraded, 0 to remove and 0 not upgraded.
Need to get 14.4 MB of archives. After unpacking 9,761 kB will be freed.
The following packages have unmet dependencies:
  libdrm-radeon1: Breaks: libdrm-radeon1 (!= 2.4.26-1ubuntu1) but 2.4.27+git1111021237.961bf9~gd~o is installed.
  libdrm-radeon1: Breaks: libdrm-radeon1 (!= 2.4.27+git1111021237.961bf9~gd~o) but 2.4.26-1ubuntu1 is to be installed.
  libgl1-mesa-dri: Breaks: libgl1-mesa-dri (!= 7.11-0ubuntu3) but 7.12~git1111141129.b04d19~gd~o is installed.
  libgl1-mesa-dri: Breaks: libgl1-mesa-dri (!= 7.12~git1111141129.b04d19~gd~o) but 7.11-0ubuntu3 is to be installed.
  libgl1-mesa-glx: Breaks: libgl1-mesa-glx (!= 7.11-0ubuntu3) but 7.12~git1111141129.b04d19~gd~o is installed.
  libgl1-mesa-glx: Breaks: libgl1-mesa-glx (!= 7.12~git1111141129.b04d19~gd~o) but 7.11-0ubuntu3 is to be installed.
  libglapi-mesa: Breaks: libglapi-mesa (!= 7.11-0ubuntu3) but 7.12~git1111141129.b04d19~gd~o is installed.
  libglapi-mesa: Breaks: libglapi-mesa (!= 7.12~git1111141129.b04d19~gd~o) but 7.11-0ubuntu3 is to be installed.
  libdrm2: Breaks: libdrm2 (!= 2.4.26-1ubuntu1) but 2.4.27+git1111021237.961bf9~gd~o is installed.
  libdrm2: Breaks: libdrm2 (!= 2.4.27+git1111021237.961bf9~gd~o) but 2.4.26-1ubuntu1 is to be installed.
  libdrm-nouveau1a: Breaks: libdrm-nouveau1a (!= 2.4.26-1ubuntu1) but 2.4.27+git1111021237.961bf9~gd~o is installed.
  libdrm-nouveau1a: Breaks: libdrm-nouveau1a (!= 2.4.27+git1111021237.961bf9~gd~o) but 2.4.26-1ubuntu1 is to be installed.
  libdrm-intel1: Breaks: libdrm-intel1 (!= 2.4.26-1ubuntu1) but 2.4.27+git1111021237.961bf9~gd~o is installed.
  libdrm-intel1: Breaks: libdrm-intel1 (!= 2.4.27+git1111021237.961bf9~gd~o) but 2.4.26-1ubuntu1 is to be installed.
open: 59; closed: 695; defer: 52; conflict: 165                                                                                                                                                    .The following actions  will resolve these dependencies:

       Remove the following packages:                                     
1)       akonadi-server                                                   
2)       akregator                                                        
3)       amarok                                                           
4)       amarok-utils                                                     
5)       amor                                                             
6)       apper                                                            
7)       appmenu-qt                                                       
8)       apport-kde                                                       
9)       apturl-kde                                                       
10)      ark                                                              
11)      bluedevil                                                        
12)      dolphin                                                          
13)      dragonplayer                                                     
14)      freespacenotifier                                                
15)      gdebi-kde                                                        
16)      gstreamer0.10-qapt                                               
17)      gwenview                                                         
18)      ia32-libs-multiarch                                              
19)      ibus-qt4                                                         
20)      jockey-kde                                                       
21)      k3b                                                              
22)      kaccessible                                                      
23)      kaddressbook                                                     
24)      kamera                                                           
25)      kate                                                             
26)      katepart                                                         
27)      kbounce                                                          
28)      kcalc                                                            
29)      kde-baseapps-bin                                                 
30)      kde-config-gtk                                                   
31)      kde-config-touchpad                                              
32)      kde-runtime                                                      
33)      kde-window-manager                                               
34)      kde-workspace                                                    
35)      kde-workspace-bin                                                
36)      kde-workspace-kgreet-plugins                                     
37)      kde-zeroconf                                                     
38)      kdebase-bin                                                      
39)      kdebase-runtime                                                  
40)      kdebase-workspace                                                
41)      kdegraphics-mobipocket                                           
42)      kdegraphics-strigi-plugins                                       
43)      kdegraphics-thumbnailers                                         
44)      kdelibs-bin                                                      
45)      kdelibs5-plugins                                                 
46)      kdemultimedia-kio-plugins                                        
47)      kdenetwork-filesharing                                           
48)      kdepasswd                                                        
49)      kdepim-groupware                                                 
50)      kdepim-kresources                                                
51)      kdepim-runtime                                                   
52)      kdepim-strigi-plugins                                            
53)      kdepim-wizards                                                   
54)      kdepimlibs-kio-plugins                                           
55)      kdesudo                                                          
56)      kdm                                                              
57)      kdoctools                                                        
58)      khelpcenter4                                                     
59)      kinfocenter                                                      
60)      kiriki                                                           
61)      klipper                                                          
62)      kmag                                                             
63)      kmail                                                            
64)      kmix                                                             
65)      kmousetool                                                       
66)      knotes                                                           
67)      konqueror                                                        
68)      konsole                                                          
69)      kontact                                                          
70)      kopete                                                           
71)      kopete-message-indicator                                         
72)      korganizer                                                       
73)      kpat                                                             
74)      kppp                                                             
75)      kscreensaver                                                     
76)      kscreensaver-xsavers                                             
77)      ksnapshot                                                        
78)      ksysguard                                                        
79)      ksystemlog                                                       
80)      ktorrent                                                         
81)      kubuntu-debug-installer                                          
82)      kubuntu-desktop                                                  
83)      kubuntu-firefox-installer                                        
84)      kubuntu-notification-helper                                      
85)      kvkbd                                                            
86)      kwalletmanager                                                   
87)      language-selector-kde                                            
88)      language-selector-qt                                             
89)      libacl1                                                          
90)      libakonadi-calendar4                                             
91)      libakonadi-contact4                                              
92)      libakonadi-kcal4                                                 
93)      libakonadi-kde4                                                  
94)      libakonadi-kmime4                                                
95)      libakonadiprotocolinternals1                                     
96)      libattica0                                                       
97)      libattr1                                                         
98)      libaudio2                                                        
99)      libavahi-client3                                                 
100)     libavahi-common3                                                 
101)     libbluedevil1                                                    
102)     libc6                                                            
103)     libcalendarsupport4                                              
104)     libcomerr2                                                       
105)     libcups2                                                         
106)     libcupsimage2                                                    
107)     libcurl3                                                         
108)     libdb5.1                                                         
109)     libdbus-1-3                                                      
110)     libdbusmenu-qt2                                                  
111)     libdebconf-kde0                                                  
112)     libdrm-intel1                                                    
113)     libdrm-nouveau1a                                                 
114)     libdrm-radeon1                                                   
115)     libdrm2                                                          
116)     libeventviews4                                                   
117)     libexpat1                                                        
118)     libffi6                                                          
119)     libfontconfig1                                                   
120)     libfreetype6                                                     
121)     libgcc1                                                          
122)     libgcrypt11                                                      
123)     libgdbm3                                                         
124)     libgl1-mesa-dri                                                  
125)     libgl1-mesa-glx                                                  
126)     libglapi-mesa                                                    
127)     libglib2.0-0                                                     
128)     libgnutls26                                                      
129)     libgpg-error0                                                    
130)     libgrantlee-core0                                                
131)     libgssapi-krb5-2                                                 
132)     libibus-qt1                                                      
133)     libice6                                                          
134)     libidn11                                                         
135)     libincidenceeditorsng4                                           
136)     libindicate-qt1                                                  
137)     libjpeg62                                                        
138)     libk3b6                                                          
139)     libk3b6-extracodecs                                              
140)     libk5crypto3                                                     
141)     libkabc4                                                         
142)     libkateinterfaces4                                               
143)     libkatepartinterfaces4                                           
144)     libkblog4                                                        
145)     libkcal4                                                         
146)     libkcalcore4                                                     
147)     libkcalutils4                                                    
148)     libkcddb4                                                        
149)     libkcmutils4                                                     
150)     libkdcraw20                                                      
151)     libkde3support4                                                  
152)     libkdecorations4                                                 
153)     libkdecore5                                                      
154)     libkdegames5a                                                    
155)     libkdepim4                                                       
156)     libkdepimdbusinterfaces4                                         
157)     libkdesu5                                                        
158)     libkdeui5                                                        
159)     libkdewebkit5                                                    
160)     libkdgantt2                                                      
161)     libkdnssd4                                                       
162)     libkemoticons4                                                   
163)     libkephal4abi1                                                   
164)     libkexiv2-10                                                     
165)     libkeyutils1                                                     
166)     libkfile4                                                        
167)     libkholidays4                                                    
168)     libkhtml5                                                        
169)     libkidletime4                                                    
170)     libkimap4                                                        
171)     libkio5                                                          
172)     libkipi8                                                         
173)     libkjsapi4                                                       
174)     libkjsembed4                                                     
175)     libkldap4                                                        
176)     libkleo4                                                         
177)     libkmanagesieve4                                                 
178)     libkmbox4                                                        
179)     libkmediaplayer4                                                 
180)     libkmime4                                                        
181)     libknewstuff2-4                                                  
182)     libknewstuff3-4                                                  
183)     libknotifyconfig4                                                
184)     libkntlm4                                                        
185)     libkonq-common                                                   
186)     libkonq5abi1                                                     
187)     libkonqsidebarplugin4a                                           
188)     libkontactinterface4                                             
189)     libkopete4                                                       
190)     libkparts4                                                       
191)     libkpgp4                                                         
192)     libkpimidentities4                                               
193)     libkpimtextedit4                                                 
194)     libkpimutils4                                                    
195)     libkprintutils4                                                  
196)     libkpty4                                                         
197)     libkrb5-3                                                        
198)     libkrb5support0                                                  
199)     libkresources4                                                   
200)     libkrosscore4                                                    
201)     libkscreensaver5                                                 
202)     libksgrd4                                                        
203)     libksieve4                                                       
204)     libksieveui4                                                     
205)     libksignalplotter4                                               
206)     libktexteditor4                                                  
207)     libktnef4                                                        
208)     libktorrent-l10n                                                 
209)     libktorrent3                                                     
210)     libkunitconversion4                                              
211)     libkutils4                                                       
212)     libkwineffects1abi2                                              
213)     libkworkspace4                                                   
214)     libkxmlrpcclient4                                                
215)     liblastfm0                                                       
216)     liblcms1                                                         
217)     libldap-2.4-2                                                    
218)     libllvm2.9                                                       
219)     libmailcommon4                                                   
220)     libmailtransport4                                                
221)     libmessagecomposer4                                              
222)     libmessagecore4                                                  
223)     libmessagelist4                                                  
224)     libmessageviewer4                                                
225)     libmicroblog4                                                    
226)     libmng1                                                          
227)     libmuonprivate1                                                  
228)     libnepomuk4                                                      
229)     libnepomukquery4a                                                
230)     libnepomukutils4                                                 
231)     libnspr4                                                         
232)     libnss3                                                          
233)     libokularcore1                                                   
234)     libpackagekit-qt2-2                                              
235)     libpciaccess0                                                    
236)     libpcre3                                                         
237)     libphonon4                                                       
238)     libplasma3                                                       
239)     libplasmaclock4abi2                                              
240)     libplasmagenericshell4                                           
241)     libpng12-0                                                       
242)     libpolkit-qt-1-1                                                 
243)     libpoppler-qt4-3                                                 
244)     libprison0                                                       
245)     libprocesscore4abi1                                              
246)     libprocessui4a                                                   
247)     libqapt-runtime                                                  
248)     libqapt1                                                         
249)     libqimageblitz4                                                  
250)     libqt4-dbus                                                      
251)     libqt4-dbus                                                      
252)     libqt4-declarative                                               
253)     libqt4-declarative                                               
254)     libqt4-designer                                                  
255)     libqt4-designer                                                  
256)     libqt4-help                                                      
257)     libqt4-network                                                   
258)     libqt4-network                                                   
259)     libqt4-opengl                                                    
260)     libqt4-opengl                                                    
261)     libqt4-qt3support                                                
262)     libqt4-qt3support                                                
263)     libqt4-script                                                    
264)     libqt4-script                                                    
265)     libqt4-scripttools                                               
266)     libqt4-scripttools                                               
267)     libqt4-sql                                                       
268)     libqt4-svg                                                       
269)     libqt4-svg                                                       
270)     libqt4-test                                                      
271)     libqt4-xml                                                       
272)     libqt4-xmlpatterns                                               
273)     libqt4-xmlpatterns                                               
274)     libqtassistantclient4                                            
275)     libqtcore4                                                       
276)     libqtgui4                                                        
277)     libqtgui4                                                        
278)     libqtscript4-core                                                
279)     libqtscript4-gui                                                 
280)     libqtscript4-network                                             
281)     libqtscript4-sql                                                 
282)     libqtscript4-uitools                                             
283)     libqtscript4-xml                                                 
284)     libqtwebkit4                                                     
285)     libreoffice-kde                                                  
286)     librtmp0                                                         
287)     libsasl2-2                                                       
288)     libsasl2-modules                                                 
289)     libselinux1                                                      
290)     libsm6                                                           
291)     libsolid4                                                        
292)     libsolidcontrol4abi2                                             
293)     libsoprano4                                                      
294)     libsqlite3-0                                                     
295)     libssl1.0.0                                                      
296)     libstdc++6                                                       
297)     libsyndication4                                                  
298)     libtaskmanager4abi2                                              
299)     libtasn1-3                                                       
300)     libtemplateparser4                                               
301)     libtiff4                                                         
302)     libtxc-dxtn0                                                     
303)     libuuid1                                                         
304)     libweather-ion6                                                  
305)     libx11-6                                                         
306)     libxau6                                                          
307)     libxcb1                                                          
308)     libxdamage1                                                      
309)     libxdmcp6                                                        
310)     libxext6                                                         
311)     libxfixes3                                                       
312)     libxi6                                                           
313)     libxrender1                                                      
314)     libxss1                                                          
315)     libxt6                                                           
316)     libxxf86vm1                                                      
317)     mozilla-plugin-vlc                                               
318)     muon                                                             
319)     muon-installer                                                   
320)     muon-notifier                                                    
321)     muon-updater                                                     
322)     okular                                                           
323)     okular-extra-backends                                            
324)     openoffice.org-kde                                               
325)     partitionmanager                                                 
326)     phonon                                                           
327)     phonon-backend-gstreamer                                         
328)     pinentry-qt4                                                     
329)     plasma-dataengines-addons                                        
330)     plasma-dataengines-workspace                                     
331)     plasma-desktop                                                   
332)     plasma-netbook                                                   
333)     plasma-scriptengine-javascript                                   
334)     plasma-scriptengine-python                                       
335)     plasma-widget-facebook                                           
336)     plasma-widget-folderview                                         
337)     plasma-widget-kimpanel                                           
338)     plasma-widget-kimpanel-backend-ibus                              
339)     plasma-widget-menubar                                            
340)     plasma-widget-message-indicator                                  
341)     plasma-widget-networkmanagement                                  
342)     plasma-widget-quickaccess                                        
343)     plasma-widgets-addons                                            
344)     plasma-widgets-workspace                                         
345)     polkit-kde-1                                                     
346)     printer-applet                                                   
347)     python-kde4                                                      
348)     python-qt4                                                       
349)     qapt-batch                                                       
350)     qapt-deb-installer                                               
351)     qdbus                                                            
352)     quassel                                                          
353)     rekonq                                                           
354)     software-properties-kde                                          
355)     soprano-daemon                                                   
356)     system-config-printer-kde                                        
357)     systemsettings                                                   
358)     unetbootin                                                       
359)     update-manager-kde                                               
360)     usb-creator-kde                                                  
361)     userconfig                                                       
362)     vidalia                                                          
363)     virtualbox                                                       
364)     virtualbox-dkms                                                  
365)     virtualbox-ose-qt                                                
366)     virtualbox-qt                                                    
367)     vlc                                                              
368)     zlib1g                                                           

       Leave the following dependencies unresolved:                       
369)     akonadi-backend-mysql recommends akonadi-server                  
370)     amarok-common recommends amarok (>= 2:2.4.3-1ubuntu2)            
371)     indicator-appmenu recommends appmenu-qt                          
372)     kontact recommends kmail                                         
373)     kontact recommends knotes                                        
374)     kontact recommends akregator                                     
375)     kontact recommends kaddressbook                                  
376)     ktorrent-data recommends ktorrent (>= 4.1.1-2ubuntu5)            
377)     kubuntu-desktop recommends akregator                             
378)     kubuntu-desktop recommends amarok                                
379)     kubuntu-desktop recommends bluedevil                             
380)     kubuntu-desktop recommends k3b                                   
381)     kubuntu-desktop recommends kaddressbook                          
382)     kubuntu-desktop recommends kdepim-kresources                     
383)     kubuntu-desktop recommends kdepim-runtime                        
384)     kubuntu-desktop recommends kdepim-strigi-plugins                 
385)     kubuntu-desktop recommends kdepim-wizards                        
386)     kubuntu-desktop recommends kmail                                 
387)     kubuntu-desktop recommends knotes                                
388)     kubuntu-desktop recommends kontact                               
389)     kubuntu-desktop recommends korganizer                            
390)     kubuntu-desktop recommends ktorrent                              
391)     muon-updater recommends muon-notifier                            
392)     soprano-daemon recommends libsoprano4 (= 2.7.0+dfsg.1-0ubuntu2)  
393)     ia32-libs recommends ia32-libs-multiarch                         
394)     unetbootin-translations recommends unetbootin                    
395)     virtualbox recommends libqt4-opengl (>= 4:4.5.3)                 
396)     kubuntu-restricted-addons recommends libk3b6-extracodecs         
397)     apport-kde recommends kubuntu-notification-helper                
398)     kde-runtime recommends kubuntu-debug-installer                   
399)     kdelibs5-plugins recommends kdebase-runtime (>= 4:4.6)           
400)     kdenetwork-filesharing recommends qapt-batch                     
401)     konqueror recommends dolphin                                     
402)     kopete recommends kopete-message-indicator                       
403)     libkhtml5 recommends kdelibs5-plugins (= 4:4.7.2-0ubuntu2)       
404)     libkio5 recommends kdelibs5-plugins (= 4:4.7.2-0ubuntu2)         
405)     libkopete4 recommends kopete (= 4:4.7.2-0ubuntu1)                
406)     okular-extra-backends recommends okular                          
407)     plasma-desktop recommends kde-workspace                          
408)     plasma-netbook recommends kde-workspace                          
409)     apper recommends software-properties-kde                         
410)     kscreensaver recommends kde-window-manager                       
411)     kscreensaver-xsavers recommends kde-window-manager               
412)     kscreensaver-xsavers recommends kscreensaver (= 4:4.7.2-0ubuntu1)
413)     libgl1-mesa-dri recommends libtxc-dxtn0                          
414)     libgl1-mesa-glx recommends libgl1-mesa-dri (>= 7.2)              


Accept this solution? [Y/n/q/?] n

```When I type n it comes back with a smaller but still unrelated and  important list of packages it wants to remove. Typing no again gives a  'no more solutions' message then repeats the previous list.  Typing q  does nothing but comment out the  /etc/apt/sources.list.d/oibaf-graphics-drivers-oneiric.list.  
I've not  had any dependency problems before when installing/upgrading/etc and  apt-get install -f gives nothing.  Looking at the ppa-purge script the  'comm: file 2 is not in sorted order' error seems to be triggered by  this code 
```

# Make list of all packages in PPA
PPA_LIST=/var/lib/apt/lists/${PPAHOST}_${PPAOWNER}_${PPANAME}_*_Packages
for LIST in $PPA_LIST; do
    if [ -e $LIST ]; then
        grep "^Package: " $LIST | cut -d " " -f2 | sort >> $PPA_PKGS
    fi
done

```according to the man page comm requires a sorted list, however the  PPA_LIST= line above would evaluate to two files, (the 64 and 32 bit  lists),  which it greps for the package line, sorts and appends separately to PPA_PKGS.   Modifying it to only use the 64 bit list (i would think the only packages installed from this ppa would be 64 bit, is there any way to check this?) gets rid of the comm error, then gives the same list  of packages to remove.  entering q gives:
```

Abandoning all efforts to resolve these dependencies.
Abort.
PPA purged successfully using aptitude fallback

```
Not sure if it did that before, however it doesn't seem to have made any difference.

Any ideas on what causes this, how it relates to trying to remove most of kde, or how to fix it?

Thanks

---

### Post by mutley89 on 2011-11-16
Also, I have tried using ppa-purge with other ppas, consisting of only 1 or 2 packages.  This does complain about dependencies, it just gives similar errors about 'E: Release 'oneiric for <package> was not found', comments out the ppa and does nothing else.

---

### Post by raja.genupula on 2011-11-16
i think you can do it like as opening your update manager -> settings -> other software and uncheck the PPA ehich you dont want and then update again or from there you can remove that PPA.

---

### Post by mutley89 on 2011-11-16
Thanks for responding.  

The problem is the packages in the ppa are at a higher version than the standard ubuntu repos, plus there are some extra packages, so apt will think it's already updated.  I'm wanting to downgrade the packages from the ones in the oibaf ppa to the defaults, hence the need for the ppa-purge script.

---

### Post by mutley89 on 2011-11-19
Any ideas?

---

### Post by tartalo on 2011-11-19
In synaptic you can force a certain version, select the package and press ctrl+E

---

### Post by mutley89 on 2011-11-19
Sort of solved by going through the packages upgraded through the ppa, downgrading or removing them, letting them remove the supposed dependencies (mostly a bunch of graphics related libs), breaking my system, then putting everything back from a dpkg --get-selections list taken a week ago.  

If anyone has any ideas, I'd still like to know what caused the 'unable to find archive...' errors.

---

### Post by Cadeyrn on 2013-03-25
This exact same thing happened to me, all of it. When I pressed n, ppa-purge kept doing something that involved internal errors and many lines that looked like "open: 2176; closed: 9089; defer: 493; conflict: 1332". I panicked and CTRL+C'ed it. I have yet to know whether it destroyed my system. apt-get update worked fine just now and my apt history.log suggests purge did not edit my system (probably because I kept saying no).

EDIT: Well, it isn't ppa-purge's fault. I'm trying to do it manually now and it looks like downgrading mesa drivers wants my computer to uninstall my entire system. Great. Maybe just downgrading the intel drivers will fix my problem...

---

