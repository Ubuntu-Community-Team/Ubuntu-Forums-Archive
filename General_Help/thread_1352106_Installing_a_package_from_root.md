---
title: "Installing a package from root"
date: 2009-12-11
forum: General Help
---

### Post by cjwescott on 2009-12-11
Need help with the basics.

I am looking to install a driver for a dongle.  I have the file "dinst" located in /home/chris/haspdongle and the instructions call for the following:

Open a terminal window and type **./dinst .** as root (note that the final "**.**" is required for the file location).

Based on the above I am typing the following and it doesn't work:

./dinst /home/chris/haspdongle

What am I doing incorrectly?

Chris

---

### Post by MelDJ on 2009-12-11
type sudo  ./dinst /home/chris/haspdongle

---

### Post by Physical Hook on 2009-12-11
```
sudo -i
[COLOR=DarkOrange]<commands>[/COLOR]
exit

```

---

### Post by cjwescott on 2009-12-11
Thank you I'll try that tonight.
 
I'm still getting through the UbuntuPocketGuide V1-1 and haven't gotten to the commands section yet.  
 
Thx again.
 
Chris

---

### Post by SlugSlug on 2009-12-11
> **cjwescott said:**
> Need help with the basics.

I am looking to install a driver for a dongle.  I have the file "dinst" located in /home/chris/haspdongle and the instructions call for the following:

Open a terminal window and type **./dinst .** as root (note that the final "**.**" is required for the file location).

Based on the above I am typing the following and it doesn't work:

./dinst /home/chris/haspdongle

What am I doing incorrectly?

Chris

I think you more likely need to do the following
 cd /home/chris/haspdongle
sudo ./dinst

---

### Post by xifer on 2009-12-11
or even

su - 
cd /home/chris/haspdongle
./dinst .

---

### Post by cjwescott on 2009-12-11
O.K. well SlugSlug's suggestion for the command line seems to have worked.

I now have to install something else based on the information that followed after the dinst.  I ran the application which requires the dongle and it still doesn't recognize the presence of a dongle.  I am running the app through Wine.  Based on this I believe I need to install the winehasp package also.  See screen shot attached.

How do I install this (i.e winehasp), which also happens to be located in the /home/chris/haspdongle folder?

Chris

---

### Post by fancypiper on 2009-12-11
Perhaps these guides will help.

[How To Install Software in Linux](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html)

[How to install ANYTHING in Ubuntu!](http://amitech.50webs.com/installing/index.php.html)

---

### Post by cjwescott on 2009-12-11
Thx for the link.  I tried a few things but still nothing.

Attached are the directions I was following.  I'm confused a little still .  It states to open the HASP SRM control center.  I do not know what they are referring to here or where this is.  Also Ref#10113 does state that ia32 needs to be installed if a 32 bit program is to run on 64bit.  My Ubuntu version is 64 bit and the app is a 32 bit program.  I did try the following at the prompt but it could not find ia32: sudo apt-get install ia32.

Can someone explain the steps I should be taking to get this dongle driver installed correctly?  Again I am trying to run a windows app through Wine which needs to recognize a hardware dongle.

Chris

---

### Post by SlugSlug on 2009-12-12
$ apt-cache search ia32
elilo - Bootloader for systems using EFI-based firmware
ia32-libs - ia32 shared libraries for use on amd64 and ia64 systems
libasm0 - Disassembling engine provided to the ERESI framework


so I guess you want
sudo apt-get install ia32-libs

---

