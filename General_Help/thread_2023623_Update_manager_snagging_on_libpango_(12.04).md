---
title: "Update manager snagging on libpango (12.04)"
date: 2012-07-12
forum: General Help
---

### Post by alexander750 on 2012-07-12
I have had some problems during the last two updates. Update Manager has failed when encountering the libpango packages. The first time I was able to fix it by running 'sudo apt-get install -f' as suggested, but this time, no go.

---

### Post by drs305 on 2012-07-12
Please post the error messages generated. You can expand the details window in Update Manager or run the commands from the terminal:
```

sudo apt-get update
sudo apt-get upgrade
```
and the ... install -f command as well if it still isn't working.

---

### Post by alexander750 on 2012-07-14
Near as I can tell, it looks like there's a version mismatch between the 32- and 64-bit versions of libpango. Is there a way to fix this?

estraven@BeigeBombshell:~$ sudo apt-get update
[sudo] password for estraven: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                            
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                                        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease           
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]            
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                 
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                 
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]                         
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]                             
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                                           
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]                                         
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                                                                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                                                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                                                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                                                    
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [26.1 kB]                                             
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]                                
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [14 B]                                                
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [7,832 B]                                     
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [713 B]                                      
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [75.8 kB]                                   
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [934 kB]                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US                                                            
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US                                              
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                                                 
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [14 B]                                           
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [20.5 kB]                                          
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [1,155 B]                                        
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [78.4 kB]                                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                                                      
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [14 B]                                            
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [20.7 kB]                                           
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [1,394 B]                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en                                                       
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources [5,470 B]                                                      
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [5,019 kB]                                                       
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources [155 kB]                                                       
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages [1,273 kB]                                                    
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages [8,452 B]                                               
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages [4,786 kB]                                                
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages [119 kB]                                                
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]                                                     
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B]                                                
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]                                                 
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex                                                            
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [128 kB]                                                     
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [1,379 B]                                              
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [33.0 kB]                                                
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [1,058 B]                                              
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [319 kB]                                              
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [2,417 B]                                       
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [88.8 kB]                                         
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [1,829 B]                                       
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [321 kB]                                               
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [2,439 B]                                        
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [89.3 kB]                                          
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [2,047 B]                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en                                                      
Fetched 19.9 MB in 2min 26s (136 kB/s)                                                                                        
Reading package lists... Done
estraven@BeigeBombshell:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libpango1.0-0
Suggested packages:
  ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp
The following packages will be upgraded:
  libpango1.0-0
1 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
2 not fully installed or removed.
Need to get 0 B/363 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libpango1.0-0 (--configure):
 libpango1.0-0:amd64 1.30.0-0ubuntu3 cannot be configured because libpango1.0-0:i386 is in a different version (1.30.0-0ubuntu3.1)
dpkg: error processing libpango1.0-0:i386 (--configure):
 libpango1.0-0:i386 1.30.0-0ubuntu3.1 cannot be configured because libpango1.0-0:amd64 is in a different version (1.30.0-0ubuntu3)
Errors were encountered while processing:
 libpango1.0-0
 libpango1.0-0:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
estraven@BeigeBombshell:~$

---

### Post by drs305 on 2012-07-14
Open this file as root and see if there are listings for the i386 version (if using 64-bit) of libpango1.0. If so, remove the references and see if that fixes things. We'll make a backup of the file first and put it on root's Desktop.

```
sudo cp /var/lib/dpkg/triggers/File /root/Desktop/
gksu gedit /var/lib/dpkg/triggers/File
```

If there are no references in the triggers file, repeat the process (including copying the file) for /var/lib/dpkg/status. If you find dual listing for the i386 and amd64 listings, remove the i386 section for libpango.

---

### Post by alexander750 on 2012-07-16
Since I don't have root login enabled (Mac OS X habit :-P), I just used sudo -s for root access, and backed up the files to my own desktop.

I didn't find any references in /var/lib/dpkg/trigger/File to libpango.

I did find the following packages in /var/lib/dpkg/status that referenced the i386 version of libpango as a dependency:
gtk2-engines-murrine
gtk2-engines-oxygen
ibus-gtk
libgtk2.0-0
librsvg2-2
libgail18
libgail-common
gstreamer0.10-x
In all cases, there were duplicate listings for "amd64" and "i386" architectures. All other packages were amd64 only.

When you say "remove the i386 section for libpango", do you mean the entire package listing(s) that reference it, or just the references themselves?

---

### Post by drs305 on 2012-07-16
What I had in mind would be removing the entire listing for a specific package:
> 
Package: libpango1.0-0
Status: install ok installed
Multi-Arch: same
Priority: optional
Section: libs
Installed-Size: 1045
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
[B]Architecture: i386
[/B]Source: pango1.0
Version: 1.30.0-0ubuntu3.1
Provides: pango1.0-multiarch-modver-1.6.0
Depends: libc6 (>= 2.14), libcairo2 (>= 1.8.10-3), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1), libglib2.0-0 (>= 2.31.8), libthai0 (>= 0.1.12), libx11-6, libxft2 (>> 2.1.1), libxrender1, fontconfig (>= 2.1.91)
Pre-Depends: multiarch-support
Suggests: ttf-baekmuk, ttf-arphic-gbsn00lp, ttf-arphic-bsmi00lp, ttf-arphic-gkai00mp, ttf-arphic-bkai00mp
Breaks: plymouth (<< 0.8.2-2ubuntu19)
Conflicts: pango-libthai
Description: Layout and rendering of internationalized text
 Pango is a library for layout and rendering of text, with an emphasis
 on internationalization. Pango can be used anywhere that text layout is
 needed. however, most of the work on Pango-1.0 was done using the GTK+
 widget toolkit as a test platform. Pango forms the core of text and
 font handling for GTK+-2.0.
 .
 Pango is designed to be modular; the core Pango layout can be used with
 four different font backends:
  - Core X windowing system fonts
  - Client-side fonts on X using the Xft library
  - Direct rendering of scalable fonts using the FreeType library
  - Native fonts on Microsoft backends
 .
 This package contains the shared libraries.
Original-Maintainer: Sebastien Bacher <seb128@debian.org>

Don't remove references to libpango in other package listings. And make a copy of the status file before editing it.

Note that my status file also contains a duplicate listing for libpango in amd64 and i386 versions, so having both on the machine is not the problem. The issue on your system is that they are different versions. If you remove the listing for the i386 version (if you have one), your system may update and if you reinstall libpango it probably would reinstall the correct, and matching versions, for both architectures.

---

### Post by alexander750 on 2012-07-16
OK...I removed just the listing for the i386 libpango package (*not* those of any that depended on it, nor any other references thereof) from /var/lib/dpkg/status and re-ran the "sudo apt-get install -f" command. The result:

estraven@BeigeBombshell:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libpango1.0-0 libpango1.0-0:i386
Suggested packages:
  ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp ttf-baekmuk:i386
  ttf-arphic-gbsn00lp:i386 ttf-arphic-bsmi00lp:i386 ttf-arphic-gkai00mp:i386 ttf-arphic-bkai00mp:i386
The following NEW packages will be installed:
  libpango1.0-0:i386
The following packages will be upgraded:
  libpango1.0-0
1 upgraded, 1 newly installed, 0 to remove and 39 not upgraded.
1 not fully installed or removed.
Need to get 0 B/724 kB of archives.
After this operation, 1,023 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package libpango1.0-0:i386.
(Reading database ... 413390 files and directories currently installed.)
Unpacking libpango1.0-0:i386 (from .../libpango1.0-0_1.30.0-0ubuntu3.1_i386.deb) ...
dpkg: unrecoverable fatal error, aborting:
 fork failed: Cannot allocate memory
E: Sub-process /usr/bin/dpkg returned an error code (2)

Also, the package gtk2-engines-oxygen was listed only as i386; there was no corresponding amd64 entry. From this, I'm assuming I need both, as oxygen is needed for compatibility with Qt-based applications in GNOME.

Should I try to install the other "suggested packages" (all fonts, I'm guessing) along with libpango?

---

### Post by drs305 on 2012-07-17
It appears that the system is now willing to reinstall libpango. I'm not familiar with the 'forking' error message. My search didn't reveal definitive suggestions other than to check your memory (free -m). Do you have swap space set up and working (look for all zeros in the swap line, which would mean it probably isn't). 

Hopefully someone else can shed some light on this error. I'd give it some time and if you get no more responses in this thread start a new one for the forking message and link to this one.

---

### Post by alexander750 on 2012-07-18
Thanks for the help...It turns out I don't have swap enabled! :oops:

(Long story short: this was the result of a drive swap. Although I have a swap partition on the hard drive, for some reason, I've not been able to get the system to recognize it. *This* explains the "can't find swap space" errors I was getting at boot time.)

---

### Post by drs305 on 2012-07-18
> **alexander750 said:**
> Thanks for the help...It turns out I don't have swap enabled! :oops:

(Long story short: this was the result of a drive swap. Although I have a swap partition on the hard drive, for some reason, I've not been able to get the system to recognize it. *This* explains the "can't find swap space" errors I was getting at boot time.)

Please enable swap. If you need help take a look at threads on the subject or start a new thread about it. 

And if your libpango problem is resolved after enabling swap please come back here and mark the thread SOLVED via the 'Thread Tools' link.

---

### Post by alexander750 on 2012-07-18
Got the swap problem fixed (took a look at the UUIDs and then edited /etc/fstab) but still having problems with (re)installing libpango: :confused:

estraven@BeigeBombshell:~$ **sudo apt-get install -f**
[sudo] password for estraven: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libpango1.0-0 libpango1.0-0:i386
Suggested packages:
  ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp ttf-baekmuk:i386
  ttf-arphic-gbsn00lp:i386 ttf-arphic-bsmi00lp:i386 ttf-arphic-gkai00mp:i386 ttf-arphic-bkai00mp:i386
The following packages will be upgraded:
  libpango1.0-0 libpango1.0-0:i386
2 upgraded, 0 newly installed, 0 to remove and 79 not upgraded.
2 not fully installed or removed.
Need to get 0 B/724 kB of archives.
After this operation, 1,023 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: libpango1.0-0:i386: dependency problems, but removing anyway as you requested:
 gstreamer0.10-x:i386 depends on libpango1.0-0 (>= 1.18.0).
 libgail-common:i386 depends on libpango1.0-0 (>= 1.28.3).
 libgail18:i386 depends on libpango1.0-0 (>= 1.28.3).
 librsvg2-2:i386 depends on libpango1.0-0 (>= 1.18.0).
 libgtk2.0-0:i386 depends on libpango1.0-0 (>= 1.28.3).
 gtk2-engines-oxygen:i386 depends on libpango1.0-0 (>= 1.18.0).
 ibus-gtk:i386 depends on libpango1.0-0 (>= 1.14.0).
 gtk2-engines-murrine:i386 depends on libpango1.0-0 (>= 1.14.0).
dpkg: error processing libpango1.0-0:i386 (--remove):
 [I]Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.[/I]
Errors were encountered while processing:
 libpango1.0-0:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)

estraven@BeigeBombshell:~$ **sudo apt-get install libpango1.0-0:i386**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libpango1.0-0 : Breaks: libpango1.0-0:i386 (!= 1.30.0-0ubuntu3) but 1.30.0-0ubuntu3.1 is to be installed
 libpango1.0-0:i386 : Breaks: libpango1.0-0 (!= 1.30.0-0ubuntu3.1) but 1.30.0-0ubuntu3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

estraven@BeigeBombshell:~$ **sudo apt-get install libpango1.0-0:i386=1.30.0-0ubuntu3.1 libpango1.0-0=1.30.0-0ubuntu3.1**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp ttf-baekmuk:i386
  ttf-arphic-gbsn00lp:i386 ttf-arphic-bsmi00lp:i386 ttf-arphic-gkai00mp:i386 ttf-arphic-bkai00mp:i386
The following packages will be upgraded:
  libpango1.0-0 libpango1.0-0:i386
2 upgraded, 0 newly installed, 0 to remove and 79 not upgraded.
2 not fully installed or removed.
Need to get 0 B/724 kB of archives.
After this operation, 1,023 kB of additional disk space will be used.
dpkg: libpango1.0-0:i386: dependency problems, but removing anyway as you requested:
 gstreamer0.10-x:i386 depends on libpango1.0-0 (>= 1.18.0).
 libgail-common:i386 depends on libpango1.0-0 (>= 1.28.3).
 libgail18:i386 depends on libpango1.0-0 (>= 1.28.3).
 librsvg2-2:i386 depends on libpango1.0-0 (>= 1.18.0).
 libgtk2.0-0:i386 depends on libpango1.0-0 (>= 1.28.3).
 gtk2-engines-oxygen:i386 depends on libpango1.0-0 (>= 1.18.0).
 ibus-gtk:i386 depends on libpango1.0-0 (>= 1.14.0).
 gtk2-engines-murrine:i386 depends on libpango1.0-0 (>= 1.14.0).
dpkg: error processing libpango1.0-0:i386 (--remove):
 [I]Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.[/I]
Errors were encountered while processing:
 libpango1.0-0:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
estraven@BeigeBombshell:~$

---

### Post by drs305 on 2012-07-19
> **alexander750 said:**
> 
dpkg: error processing libpango1.0-0:i386 (--remove):
 [I]Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.[/I]
Errors were encountered while processing:
 libpango1.0-0:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
estraven@BeigeBombshell:~$

Did you try reinstalling it, or 'sudo apt-get install -f' again? That's about all I can recommend at this point.

---

### Post by alexander750 on 2012-07-19
I had thought about using the "purge" option with apt-get, but that would require reinstalling all the stuff that depends on libpango as well...Is there a way to fix this manually, by deleting/editing the offending file(s)?

---

### Post by drs305 on 2012-07-20
> **alexander750 said:**
> I had thought about using the "purge" option with apt-get, but that would require reinstalling all the stuff that depends on libpango as well...Is there a way to fix this manually, by deleting/editing the offending file(s)?

Have you tried a simple reinstall yet? Here are the steps I'd initially take:
```

sudo apt-get clean autoclean autoremove  # Remove unnecessary and archived packages, in case they are corrupt
sudo apt-get install --reinstall libpango1.0-0:i386

```

---

### Post by jseabold on 2012-07-24
I was able to fix this problem by doing

```
sudo dpkg -i /var/cache/apt/archives/libpango1.0-0_1.30.0-0ubuntu3.1_i386.deb 
```

Then

```
sudo apt-get -f install
```

---

### Post by alexander750 on 2012-07-24
> 
I was able to fix this problem by doing

```

sudo dpkg -i /var/cache/apt/archives/libpango1.0-0_1.30.0-0ubuntu3.1_i386.deb

```Then

```

sudo apt-get -f install

```I had to do this for both the amd64 and i386 versions (to correct the version mismatch that started this issue in the first place). But it worked. :)

---

