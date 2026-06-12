---
title: "Installing FileOpenInstaller for adobe reader"
date: 2011-06-22
forum: General Help
---

### Post by Trudhilda on 2011-06-22
Hi all,

i recently installed ubuntu natty 64bit-version. Now, i need to install FileOpenInstaller since many pdfs that i receive are only to be decrypted with this plugin. The .tar.gz-file is available here:

[http://plugin.fileopen.com/all.aspx](http://plugin.fileopen.com/all.aspx)

Unfortunately, this plugin does not work with the latest adobe reader available, although under system requirements Adobe Reader or Adobe Acrobat 7.0 or later is required. Having extracted the .tar.gz-file it becomes obvious that only adobe reader 7 and adobe reader 8 is being supported by the plugin. (Nevertheless, i tried to install the plugin in combination with **acroread** **9.4.2** without success. After installing acroread I did 

sudo ./commandline_installer.sh

but the process stopped since a wrong version of adobe reader has been detected.

I could imagine 2 different kind of solutions:

1. Installing an older version of acroread, which I could not find on the web. So please tell me, where I can find an older version of acroread.

2. Installing **adobe reader 8.1.7** (deb) from 
    [http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/)
    Unfortunately, there are only 32bit-versions available for linux users.
    There are some threads concerning this problem but I could not figure out how to run a 32bit version on 
    64bit system:    
    [http://www.ubuntugeek.com/install-acrobat-reader-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/install-acrobat-reader-in-ubuntu-9-10-karmic.html)
    
    I tried 
    sudo dpkg -i --force-architecture AdobeReader_deu-8.1.7-1.i386.deb
   which gives
   dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 148729 files and directories currently installed.)
Preparing to replace adobereader-deu:i386 8.1.7 (using AdobeReader_deu-8.1.7-1.i386.deb) ...
Unpacking replacement adobereader-deu:i386 ...
dpkg: dependency problems prevent configuration of adobereader-deu:i386:
 adobereader-deu:i386 depends on libgtk2.0-0 (>= 2.4).
dpkg: error processing adobereader-deu:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 adobereader-deu:i386
  
 How do I solve this dependency problem? I checked on synaptic if libgtk2.0-0 (>= 2.4) is installed.

Thank you.

regards

Trudhilda

---

