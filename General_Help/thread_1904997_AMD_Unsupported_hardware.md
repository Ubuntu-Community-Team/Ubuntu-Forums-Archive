---
title: "AMD Unsupported hardware"
date: 2012-01-05
forum: General Help
---

### Post by ugotboxed on 2012-01-05
At the bottom right corner of my screen there is a transperant image that says "AMD Unsupported hardware" I dont know how to get this off of my screen. I have a Powercolor Radeon HD 6790. This is my first time using Ubuntu or any form of linux. Please help.

---

### Post by collisionystm on 2012-01-05
> **ugotboxed said:**
> At the bottom right corner of my screen there is a transperant image that says "AMD Unsupported hardware" I dont know how to get this off of my screen. I have a Powercolor Radeon HD 6790. This is my first time using Ubuntu or any form of linux. Please help.


open a terminal

sudo apt-get install fglrx-updates

reboot

---

### Post by larrypg on 2012-01-05
Hello,

For me at least with a 6770 the flgrx-upgrade(updates) did not work but the flgrx did.

---

### Post by Cr125f150ba on 2012-03-10
> **collisionystm said:**
> open a terminal

sudo apt-get install fglrx-updates

reboot


Thankyou!!!. I had this watermark in my lower right corner and this command fixed it. Then after i typed in the command I installed the flash player and everything works now. Thankyou.

---

### Post by jwflammer on 2012-07-25
E: Unable to locate package fglrx-updates

this is the error i get when i type this in terminal have same issue with my ATI 6450

---

### Post by collisionystm on 2012-07-28
> **jwflammer said:**
> E: Unable to locate package fglrx-updates

this is the error i get when i type this in terminal have same issue with my ATI 6450


Check your software sources .

To do this, open the software center. Mouse up to the top bar and go to Edit, Software Sources.

Make sure the box is checked for "Proprietary drivers for devices"

Go to the "Other Software" tab and make sure Canonical Partners is checked.

Then...

Try a 

sudo apt-get update

sudo apt-get install fglrx-updates

---

### Post by shockfi3nd on 2012-08-14
I'm having the same watermark issue.  I am using a Radeon HD 7850.  I've tried the other suggestions (sudo apt-get update; sudo apt-get install fglrx-updates), I still have the watermark in the lower right-hand corner.  Any other workarounds, fixes?  I've downloaded the driver from AMD, but don't know how to install it...

---

### Post by yoyomau on 2012-10-31
I also have the HD 7850, I simply went to the ATI website and downloaded the latest linux catalyst drivers.  You'll need to uninstall  fglrx before installing. I used synaptic package manager to remove it or you can use sudo remove. I then unzipped the AMD driver installer, it's a .run so you will need to right click on it go to properties>permissions and check the box allow executing as a program.

---

### Post by QIII on 2012-10-31
If, after installing from AMD's website, you want to uninstall the driver, apt-get will not work.

Use```
sudo amdconfig --uninstall
```

---

### Post by Carlos Araujo on 2012-11-10
Hibryd Graphics INTEL(HD 4000) / AMD HD 7570M - Unsupported card, Unsupported AMD!!!

---

### Post by ronnoc on 2013-01-14
I also have a 6770 and am on Raring. I also just started getting this message. fglrx-updates is already installed and is the latest version. I'm also running the latest drivers via the Xorg-edgers PPA. That watermark is driving me crazy.

---

### Post by oldos2er on 2013-01-14
Raring has its own forum [http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427) so you should probably post there.

---

### Post by RogerDavis on 2013-08-09
> **collisionystm said:**
> Check your software sources .

To do this, open the software center. Mouse up to the top bar and go to Edit, Software Sources.

Make sure the box is checked for "Proprietary drivers for devices"

Go to the "Other Software" tab and make sure Canonical Partners is checked.

Then...

Try a 

sudo apt-get update

sudo apt-get install fglrx-updates

Worked for me!  All boxes were already properly checked.  I'd had this problem in the past, like about 8 months ago, fixed it then, and it came back with the automatic updates today (8/9/13).

---

### Post by nafo11 on 2014-03-05
Thanks a lot!!

---

### Post by mimomi on 2014-04-19
Thank you. It works on my HP Pavilion. I used update manager and "AMD Unsupported hardware" appears. After I do what these guys said, it disappears.

---

