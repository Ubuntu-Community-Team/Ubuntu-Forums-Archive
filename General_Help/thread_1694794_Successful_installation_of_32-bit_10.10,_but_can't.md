---
title: "Successful installation of 32-bit 10.10, but can't perform updates."
date: 2011-02-24
forum: General Help
---

### Post by Kirabaen on 2011-02-24
I just installed Ubuntu 10.10 32-bit on my laptop and successfully completed the installation. However, I attempted to install the recommended updates but have been unsuccessful. The updates downloaded just fine, but when I attempt to install the downloaded updates, I get a package operation failed with the following text:

installArchives() failed:  Extracting templates from packages: 10% Extracting templates from packages: 21% Extracting templates from packages: 32% Extracting templates from packages: 43% Extracting templates from packages: 54% Extracting templates from packages: 65% Extracting templates from packages: 76% Extracting templates from packages: 87% Extracting templates from packages: 98% Extracting templates from packages: 100% 
Preconfiguring packages ... 
 Extracting templates from packages: 10% Extracting templates from packages: 21% Extracting templates from packages: 32% Extracting templates from packages: 43% Extracting templates from packages: 54% Extracting templates from packages: 65% Extracting templates from packages: 76% Extracting templates from packages: 87% Extracting templates from packages: 98% Extracting templates from packages: 100% 
Preconfiguring packages ... 
Setting up tzdata (2011b-0ubuntu0.10.10) ... 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109. 
dpkg: error processing tzdata (--configure): 
 subprocess installed post-installation script returned error exit status 128 
Errors were encountered while processing: 
 tzdata 
Setting up tzdata (2011b-0ubuntu0.10.10) ... 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109. 
dpkg: error processing tzdata (--configure): 
 subprocess installed post-installation script returned error exit status 128 


If anyone could shed some light on this I would greatly appreciate it. Thanks.


Edit: I'm installing this on a Toshiba Satellite L305-S5921 Laptop

---

### Post by thefasterblueone on 2011-02-24
```
sudo dpkg --configure -a && sudo apt-get install -f
```


Post any errors.

---

### Post by Kirabaen on 2011-02-25
Thanks. I ran this in the terminal and then tried installing the updates again. It took forever reconfiguring all the updates, but it worked =). Thanks!
 
Edit: Fixed a typo =P

---

