---
title: "HPLIP no duplex and some pdf files distorted"
date: 2010-11-11
forum: General Help
---

### Post by bertmung on 2010-11-11
To solve problems with duplex printing I installed the latest HPLIP (3.10.9) from the autoinstaller at

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

This does nothing for the missing duplex problem.

Most pdf files print fine. Files that were a problem before upgrading to 10.10 print without a hitch.

However, I came across pdf files today that won't print. Some lines print perfectly. Others appear to have most of the right characters, but in a random order and some on top of each other.

There's a proposed upgrade to HPLIP that I'd like to try, but I have to get rid of HPLIP 3.10.9 first. Probably because I didn't use the Synaptic Package Manager to install it Synaptic doesn't see it. I know what directory HPLIP 3.10.9 is in. What is the safest way to uninstall it?

---

### Post by bertmung on 2010-11-12
> **bertmung said:**
> 
 missing duplex problem.


System-->Administration-->Printing  
Printer-->Properties
Click on the change button beside Make and Model
select the hpijs driver
select double sided printing under options
reboot
double sided printing now works.

> 
distorted printing

reboot (duhh!!!) Why didn't I try that before posting to the forum?

---

### Post by Quarkrad on 2010-12-07
I need help on this one - I have seen this solution before but when I try it I do not get option to select the hpijs driver.  I have sudo apt-get install hpijs and it seems to me that it installs itself.  However, the option is not there - is there something I am not doing?

---

