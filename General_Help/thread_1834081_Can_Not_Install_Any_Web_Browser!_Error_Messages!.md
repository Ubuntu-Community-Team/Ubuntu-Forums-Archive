---
title: "Can Not Install Any Web Browser! Error Messages!"
date: 2011-08-27
forum: General Help
---

### Post by tito-dutta on 2011-08-27
I have only one browser, [FF 6.0] :(  in Operating System [Ubuntu 11.04] I tried to download Chrome and Opera 
Downloaded successfully,
**For installation of Opera got this error message:**
_Selecting previously deselected package opera.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 129488 files and directories currently installed.)
Unpacking opera (from .../opera_11.50.1074_i386.deb) ...
Setting up opera (11.50.1074) ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.
Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109.
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.
dpkg: error processing opera (--install):
 subprocess installed post-installation script returned error exit status 128
Processing triggers for shared-mime-info ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Rebuilding /usr/share/applications/desktop.en_IN.ISO8859-1.cache...
WARNING: System locale is invalid
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.
Processing triggers for software-center ...

(process:2731): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
/usr/lib/pymodules/python2.7/gtk-2.0/gtk/_*init_*.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
No handlers could be found for logger "__main__"
Updating software catalog...this may take a moment.
Software catalog update was successful.
Processing triggers for python-support ...
Processing triggers for python-central ..._

**For Chrome, I got this error message:**
[https://lh3.googleusercontent.com/-0oE_-X2t-70/TldafhlRMDI/AAAAAAAAEYk/F_8L2E34Ytk/s800/Google_Chrome_Download_Error.png](https://lh3.googleusercontent.com/-0oE_-X2t-70/TldafhlRMDI/AAAAAAAAEYk/F_8L2E34Ytk/s800/Google_Chrome_Download_Error.png)
I have mobile broadband Internet connection, Tata Photon, India, and Internet Connection is fine.

---

### Post by raja.genupula on 2011-08-27
open ubuntu software center and then try  to install from there .

---

### Post by tito-dutta on 2011-08-27
Yes, that worked. Thanks!  :popcorn:
But, I am interested to learn why the installation failed when I tried it by double clicking on the file in download folder?
[If anyone needs it later: I need to search the browser in Ubuntu Software center and re-install the browsers]

---

### Post by raja.genupula on 2011-08-27
i am glad  to hear this . my guess is its looking that your packages are crashed . always use software center or synaptic manager to install . that is safe , simple and secure .

---

### Post by tito-dutta on 2011-08-27
Thanks!
> **raja.genupula said:**
>  always use software center or synaptic manager to install . that is safe , simple and secure .
Yes, I have spent some time in that section today. But, as a big supporter of open source softwares, I worry, how will one install softwares if (s)he does not have internet connection and faces problem like this! :-k:-k:-k

---

### Post by grahammechanical on 2011-08-27
Synaptic and the Ubuntu Software Centre will let you install from CD ROM. In the Software Centre go the the edit menu and select Software Sources. Under the Other Software tab you can click Add Volume. But remember, if the package does not have all the files and libraries needed by the program then you will get installation errors such as those that you have seen.

It is possible to do a distribution upgrade of Ubuntu in this way. Put the CD in the drive and Ubuntu will recognize that it has a distribution on it and will offer to use it to upgrade.

Regards.

---

### Post by tito-dutta on 2011-08-27
Sorry, but, where is 'edit menu'? I am attaching a screenshot.
Thanks!

---

### Post by raja.genupula on 2011-08-27
go to Edit--> software sources --> check the cd-rom option  at the bottom of the window .

---

