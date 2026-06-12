---
title: "Installing apps in offline"
date: 2012-01-08
forum: General Help
---

### Post by sinaphysics on 2012-01-08
Hi,
I backup my ex-softwares and now I restore them in my ubuntu, how can I Install them??
Is there anyway via Command Line for installing them?
I restore them /var/cache/apt/archives/ .

---

### Post by Paqman on 2012-01-08
If you've dumped them into the APT cache all you need to do is run an update and you'll be able to install them through the normal tools (eg: Ubuntu Software Centre, apt-get, etc)

---

### Post by sinaphysics on 2012-01-08
how can I update them??
is the command line: sudo apt-get update??
what does mean this command line??

---

### Post by Paqman on 2012-01-08
> **sinaphysics said:**
> how can I update them??
is the command line: sudo apt-get update??
what does mean this command line??

Yep, that's the one. It forces the package manager to check the repositories for updated versions of packages. If there's no connection it'll use the packages it already has in the cache.

sudo = Super User Do (gives the command enough privileges to run)
apt-get = Invokes APT, the Advanced Packaging Tool
update = Tells APT to look for updates

---

### Post by sinaphysics on 2012-03-14
After restoring when I install same apps in both way ( software center and sudo apt-get), starts to download the package freshly except in some cases like firefox!! (this is when the laptop is connected to internet and when is not connected nothing happen) 
I use ubuntu 11.10.
what do u suggest?

---

### Post by cortman on 2012-03-14
> **sinaphysics said:**
> After restoring when I install same apps in both way ( software center and sudo apt-get), starts to download the package freshly except in some cases like firefox!! (this is when the laptop is connected to internet and when is not connected nothing happen) 
I use ubuntu 11.10.
what do u suggest?

This would indicate that your offline copies in /var/cache/apt/archives are not the most up-to-date. APT won't grab from the cache if it finds a newer copy available on the repository.

---

### Post by raja.genupula on 2012-03-14
see this it have good information .
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by sinaphysics on 2012-03-14
To clarify the issue, in past i use some softwares like 'kile','parley' or 'calibre' which in that case i backuped my system and after restoring in same folder in offline mode when i use 'sudo apt-get update' and then 'sudo apt-get install (soft name)' i can't install the mentioned apps. And in terminam page it shows that there exist some packages and some packages must be downloaded which cause failed.( Because there's no connection). While i use them in past. I'm really confused and internet is so expensive here to download them again, please help me.

---

### Post by cortman on 2012-03-14
Ok, try running

```
sudo apt-get install calibre
```

Since you said you've used it before. Please post all output.

---

### Post by sinaphysics on 2012-03-16
The output is :

>    	 	 	 	 	 	   sina@sina-Vostro1510:~$ sudo apt-get install calibre  [sudo] password for sina:  Reading package lists... Done Building dependency tree        Reading state information... Done The following packages were automatically installed and are no longer required:   java-common icedtea-6-jre-cacao openjdk-6-jre-headless dkms tzdata-java   icedtea-6-jre-jamvm openjdk-6-jre-lib screen-resolution-extra patch   ca-certificates-java Use 'apt-get autoremove' to remove them. The following extra packages will be installed:   calibre-bin imagemagick libcdt4 libchm1 libgraph4 libgvc5 liblqr-1-0   libmagickcore3 libmagickcore3-extra libmagickwand3 libnetpbm10 libpathplan4   libpodofo0.9.0 libqt4-dbus libqt4-declarative libqt4-designer libqt4-help   libqt4-network libqt4-opengl libqt4-script libqt4-scripttools libqt4-sql   libqt4-sql-mysql libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns   libqtassistantclient4 libqtcore4 libqtgui4 netpbm python-beautifulsoup   python-cherrypy3 python-clientform python-cssutils python-cssutils-doc   python-django python-django-tagging python-dnspython python-encutils   python-lxml python-mechanize python-pyparsing python-qt4 python-routes   python-sip python-webob qdbus Suggested packages:   imagemagick-doc autotrace curl enscript ffmpeg gnuplot grads hp2xx html2ps   libwmf-bin povray radiance texlive-base-bin transfig ufraw-batch   libqt4-declarative-folderlistmodel libqt4-declarative-gestures   libqt4-declarative-particles libqt4-declarative-shaders qt4-qmlviewer   libqt4-dev qt4-qtconfig python-psycopg2 python-psycopg python-mysqldb   python-flup python-sqlite python-yaml python-lxml-dbg python-qt4-dbg   python-paste The following NEW packages will be installed:   calibre calibre-bin imagemagick libcdt4 libchm1 libgraph4 libgvc5 liblqr-1-0   libmagickcore3 libmagickcore3-extra libmagickwand3 libnetpbm10 libpathplan4   libpodofo0.9.0 libqt4-designer libqt4-help libqt4-scripttools libqt4-test   libqtassistantclient4 netpbm python-beautifulsoup python-cherrypy3   python-clientform python-cssutils python-cssutils-doc python-django   python-django-tagging python-dnspython python-encutils python-lxml   python-mechanize python-pyparsing python-qt4 python-routes python-sip   python-webob The following packages will be upgraded:   libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl libqt4-script   libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-xml libqt4-xmlpatterns   libqtcore4 libqtgui4 qdbus 13 upgraded, 36 newly installed, 0 to remove and 357 not upgraded. Need to get 30.7 MB/45.1 MB of archives. After this operation, 147 MB of additional disk space will be used. Do you want to continue [Y/n]? y Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main liblqr-1-0 i386 0.4.1-1ubuntu2   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libmagickcore3 i386 8:6.6.0.4-3ubuntu1   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libmagickwand3 i386 8:6.6.0.4-3ubuntu1   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main imagemagick i386 8:6.6.0.4-3ubuntu1   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libcdt4 i386 2.26.3-5ubuntu4   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe libchm1 i386 2:0.40-3   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libgraph4 i386 2.26.3-5ubuntu4   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libpathplan4 i386 2.26.3-5ubuntu4   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libgvc5 i386 2.26.3-5ubuntu4   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libmagickcore3-extra i386 8:6.6.0.4-3ubuntu1   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libnetpbm10 i386 2:10.0-12.2   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libqtassistantclient4 i386 4.6.3-3ubuntu1   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main netpbm i386 2:10.0-12.2   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main python-beautifulsoup all 3.2.0-2   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe python-cherrypy3 all 3.1.2-1   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe python-encutils all 0.9.8~a1-1   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe python-cssutils all 0.9.8~a1-1   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe python-cssutils-doc all 0.9.8~a1-1   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main python-django all 1.3-2ubuntu1.1   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe python-django-tagging all 0.3.1-1   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main python-dnspython all 1.9.4-0ubuntu2   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main python-lxml i386 2.3-0.1build1   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe python-pyparsing all 1.5.2-2   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main python-sip i386 4.12.4-1   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main python-qt4 i386 4.8.5-0ubuntu2   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main python-routes all 1.12.3-1   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe python-clientform all 0.2.10-2.1   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe python-mechanize all 0.1.11-1.1   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe libpodofo0.9.0 i386 0.9.0-1ubuntu2   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe calibre-bin i386 0.8.8+dfsg-1ubuntu1   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe calibre all 0.8.8+dfsg-1ubuntu1   Could not resolve 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main python-webob all 1.0.8-1   Could not resolve 'us.archive.ubuntu.com' Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security/main python-django all 1.3-2ubuntu1.1   Could not resolve 'security.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libl/liblqr/liblqr-1-0_0.4.1-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libl/liblqr/liblqr-1-0_0.4.1-1ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore3_6.6.0.4-3ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore3_6.6.0.4-3ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickwand3_6.6.0.4-3ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickwand3_6.6.0.4-3ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/imagemagick_6.6.0.4-3ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/imagemagick_6.6.0.4-3ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/graphviz/libcdt4_2.26.3-5ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/graphviz/libcdt4_2.26.3-5ubuntu4_i386.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/chmlib/libchm1_0.40-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/chmlib/libchm1_0.40-3_i386.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/graphviz/libgraph4_2.26.3-5ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/graphviz/libgraph4_2.26.3-5ubuntu4_i386.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/graphviz/libpathplan4_2.26.3-5ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/graphviz/libpathplan4_2.26.3-5ubuntu4_i386.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/graphviz/libgvc5_2.26.3-5ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/graphviz/libgvc5_2.26.3-5ubuntu4_i386.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore3-extra_6.6.0.4-3ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore3-extra_6.6.0.4-3ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/netpbm-free/libnetpbm10_10.0-12.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/netpbm-free/libnetpbm10_10.0-12.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt-assistant-compat/libqtassistantclient4_4.6.3-3ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt-assistant-compat/libqtassistantclient4_4.6.3-3ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/netpbm-free/netpbm_10.0-12.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/netpbm-free/netpbm_10.0-12.2_i386.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/beautifulsoup/python-beautifulsoup_3.2.0-2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/beautifulsoup/python-beautifulsoup_3.2.0-2_all.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cherrypy3/python-cherrypy3_3.1.2-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cherrypy3/python-cherrypy3_3.1.2-1_all.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cssutils/python-encutils_0.9.8~a1-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cssutils/python-encutils_0.9.8~a1-1_all.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cssutils/python-cssutils_0.9.8~a1-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cssutils/python-cssutils_0.9.8~a1-1_all.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cssutils/python-cssutils-doc_0.9.8~a1-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cssutils/python-cssutils-doc_0.9.8~a1-1_all.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/python-django/python-django_1.3-2ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python-django/python-django_1.3-2ubuntu1.1_all.deb)  Could not resolve 'security.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/p/python-django-tagging/python-django-tagging_0.3.1-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/p/python-django-tagging/python-django-tagging_0.3.1-1_all.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dnspython/python-dnspython_1.9.4-0ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dnspython/python-dnspython_1.9.4-0ubuntu2_all.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/lxml/python-lxml_2.3-0.1build1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/lxml/python-lxml_2.3-0.1build1_i386.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/p/pyparsing/python-pyparsing_1.5.2-2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/p/pyparsing/python-pyparsing_1.5.2-2_all.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/sip4/python-sip_4.12.4-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/sip4/python-sip_4.12.4-1_i386.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-qt4/python-qt4_4.8.5-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-qt4/python-qt4_4.8.5-0ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/r/routes/python-routes_1.12.3-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/r/routes/python-routes_1.12.3-1_all.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/p/python-clientform/python-clientform_0.2.10-2.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/p/python-clientform/python-clientform_0.2.10-2.1_all.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/p/python-mechanize/python-mechanize_0.1.11-1.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/p/python-mechanize/python-mechanize_0.1.11-1.1_all.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/libp/libpodofo/libpodofo0.9.0_0.9.0-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/libp/libpodofo/libpodofo0.9.0_0.9.0-1ubuntu2_i386.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/calibre/calibre-bin_0.8.8+dfsg-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/calibre/calibre-bin_0.8.8+dfsg-1ubuntu1_i386.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/calibre/calibre_0.8.8+dfsg-1ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/calibre/calibre_0.8.8+dfsg-1ubuntu1_all.deb)  Could not resolve 'us.archive.ubuntu.com' Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-webob/python-webob_1.0.8-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-webob/python-webob_1.0.8-1_all.deb)  Could not resolve 'us.archive.ubuntu.com' E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?   
so??

---

### Post by sinaphysics on 2012-03-16
Is there any other effective way to install apps in offline mode without CD. because my DVD-ROM is corrupted.

---

### Post by raja.genupula on 2012-03-16
are you sure with your name server in ```
/etc/resolv.conf
``` . check it out is there any wrong . and give the output of 
```
sudo apt-get update
```

---

### Post by sinaphysics on 2012-03-16
```
/etc/resolv.conf 
```

when I did this the result was
> bash: /etc/resolv.conf: Permission denied

even when I enter it as the root.

And when I enter the 
```
sudo apt-get update 
```
the result is
> Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric InRelease
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                             
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                           
  Could not resolve 'extras.ubuntu.com'
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric Release
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main TranslationIndex
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted TranslationIndex
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                          
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease                  
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease                
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                        
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/InRelease](http://archive.ubuntu.com/ubuntu/dists/oneiric/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease](http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease](http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Could not resolve 'extras.ubuntu.com'

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.



---

### Post by raja.genupula on 2012-03-16
no if you wanna edit it , you can by
```
sudo gedit /etc/resolv.conf
```

open update manager -> settings -> in that at 1st TAB uncheck the CD-ROM .

---

### Post by sinaphysics on 2012-03-29
the result is:
```

sudo gedit /etc/resolv.conf


```> 
# Generated by NetworkManager



I'm waiting for your response.

---

### Post by sinaphysics on 2012-04-08
Hey, I'm waiting for you.

---

