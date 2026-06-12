---
title: "I cant pen any EXE files?"
date: 2010-12-02
forum: General Help
---

### Post by joelkat on 2010-12-02
I get errors like this, All the time  


End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /tmp/wlsetup-web.exe or
          /tmp/wlsetup-web.exe.zip, and cannot find /tmp/wlsetup-web.exe.ZIP, period.

---

### Post by WorMzy on 2010-12-02
You're not using Windows, .exe files won't work.

You can install Windows software using Wine, but it's best to isntall native software from the Software Centre. (Applications -> Ubuntu Software Centre)

---

### Post by joelkat on 2010-12-02
Ok thank lord I thought I screwed my new system up how do I get wine?

---

### Post by bowens44 on 2010-12-02
> **joelkat said:**
> Ok thank lord I thought I screwed my new system up how do I get wine?

Just search for it in synaptic or the software center. Also , be aware that most windows software will not run under wine.

to find out whether or not your application will run, go here:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by joelkat on 2010-12-02
So my system is working fine?

---

### Post by bowens44 on 2010-12-02
> **joelkat said:**
> So my system is working fine?

Probably, unless it's crashing or something but not being able to run exe files is not an indication that your system is messed up.  Just keep in mind that Linux isn't windows and you can't expect software written for windows to function or even run as it would in windows. Luckily, there are linux equivalents for the vast majority of windows software.  

There are tens of thousands of free software packages available through the repositories.

---

### Post by philinux on 2010-12-02
> **joelkat said:**
> So my system is working fine?

Yes. Please see this resource. 

[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

And this.

[http://psychocats.net/ubuntu/wine](http://psychocats.net/ubuntu/wine)

---

### Post by TBABill on 2010-12-02
> **joelkat said:**
> I get errors like this, All the time 
 
 
End-of-central-directory signature not found. Either this file is not
a zipfile, or it constitutes one disk of a multi-part archive. In the
latter case the central directory and zipfile comment will be found on
the last disk(s) of this archive.
zipinfo: cannot find zipfile directory in one of /tmp/wlsetup-web.exe or
/tmp/wlsetup-web.exe.zip, and cannot find /tmp/wlsetup-web.exe.ZIP, period.
 
More importantly than finding out about Wine, perhaps some reading up on Linux would be of some assistance in order to better understand how you install additional software, where that software is stored (repositories), why that software is free and the benefits of using software available from the repositories or from trusted sources only.
 
As a brief overview, software for Ubuntu is free (mostly...not getting into the paid stuff here). The repositories are filled with literally thousands of applications you may download and install free of charge for just about anything you can think of. If you click APPLICATIONS on the top left menu, at the bottom is the Ubuntu Software Center. Navigating through the categories you will find all that software you are free to install and uninstall as you wish. Additionally, under SYSTEM>>ADMINISTRATION>>PACKAGE MANAGER (called Synaptic), you can do the same things as the Ubuntu Software Center, just with a bit more archaic look and feel if you are a new user. 
 
Software in Ubuntu often has what are called dependencies, files required in addition to the files you select in order to pull in everything required for that application to run. That is handled for you for anything in the repositories.
 
If you find additional files online, you will know they are double-click installable if they have a .deb file extension. The .deb is short for Debian, which is the base system Ubuntu is built from. However, .deb files outside the repositories can contain anything so you  would need to know it is a safe source you are downloading from (no different than knowing if you can trust a .exe in Windows).
 
There are also source files you can install from, but sticking to the repos and .deb files is a good start for a new user. And in my opinion, just sticking to the repos is the best bet until you learn more and understand how the system is managed.
 
I hope this helps a bit. There is a wealth of knowledge to be gained at [https://help.ubuntu.com](https://help.ubuntu.com) and even more via search engine. Good luck!

---

