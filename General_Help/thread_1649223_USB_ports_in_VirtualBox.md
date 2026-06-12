---
title: "USB ports in VirtualBox"
date: 2010-12-19
forum: General Help
---

### Post by Dangerzone812 on 2010-12-19
Hey guys, I'm running Windows 7 through VirtualBox on my laptop that runs Ubuntu 10.10. 

Does any one know how to configure VirtualBox so that when I plug in something through the USB ports Windows 7 will pick up on it and read it as if its the native OS on my computer?

Thanks in advance,

Danger

---

### Post by wilee-nilee on 2010-12-19
> **Dangerzone812 said:**
> Hey guys, I'm running Windows 7 through VirtualBox on my laptop that runs Ubuntu 10.10. 

Does any one know how to configure VirtualBox so that when I plug in something through the USB ports Windows 7 will pick up on it and read it as if its the native OS on my computer?

Thanks in advance,

Danger

Did you install Vbox from synaptic or the web link to Oracle

---

### Post by Dangerzone812 on 2010-12-19
> **wilee-nilee said:**
> Did you install Vbox from synaptic or the web link to Oracle

Oracle I believe.

---

### Post by techunit on 2010-12-19
It is Oracle Virtualbox yes, but did you install it from the software center or did you install it from website. If you did the first then you need to install the one from the website. I use Virtualbox on a daily basis as I am a screencast video tutorial producer so I need it. I recommend you use the OSE program only if you don't need the USB connectivity, Otherwise use the normal edition. Best regards,

---

### Post by wilee-nilee on 2010-12-19
> **Dangerzone812 said:**
> Oracle I believe.

If its the Oracle puel you just need to add your self to the users in Vbox and add any usb through the OS settings usb.
[ATTACH]178928[/ATTACH]

---

### Post by Torombolo on 2010-12-19
Settings/USB

[[IMG]http://img443.imageshack.us/img443/1303/screenshotleb.th.png[/IMG]](http://img443.imageshack.us/i/screenshotleb.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by Dangerzone812 on 2010-12-19
@ willie -  I don't see that listed under my groups...

ALso Torombolo, I don't see USB listed under VirtualBox, only Serial...

---

### Post by Dangerzone812 on 2010-12-19
@ willie -  I don't see that listed under my groups...

ALso Torombolo, I don't see USB listed under VirtualBox, only Serial...

---

### Post by Torombolo on 2010-12-20
what version u got?

---

### Post by wilee-nilee on 2010-12-20
When you installed Vbox it should have been from here, was it?
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by Dangerzone812 on 2010-12-20
I downloaded it from the Ubuntu Software center, and its version 3.2.8

---

### Post by wilee-nilee on 2010-12-20
> **Dangerzone812 said:**
> I downloaded it from the Ubuntu Software center, and its version 3.2.8

Remove it the OS will still be in the .virtualbox folder install the web version load the original OS and follow the add to users and the usb picture, crack a beer and enjoy the fun.

---

### Post by Dangerzone812 on 2010-12-20
I tried to download it off their site, I downloaded the file, hit open, and it took me directly to the Ubuntu Software Center...

---

### Post by wilee-nilee on 2010-12-20
> **Dangerzone812 said:**
> I tried to download it off their site, I downloaded the file, hit open, and it took me directly to the Ubuntu Software Center...

Did you remove the original install as suggested first.

Did you download from here?
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by Dangerzone812 on 2010-12-20
Yes, I did. 

Also, thanks for all your help and dealing with me!

---

### Post by wilee-nilee on 2010-12-20
> **Dangerzone812 said:**
> Yes, I did. 

Also, thanks for all your help and dealing with me!

Hey Vbox is a bit of a challenge the first times around. So you downloaded a debi, right click it and use gdebi to run it.

Also before installing go to synaptic and install dkms this will have the kernel upgrades keeping the guest correct.

---

### Post by Dangerzone812 on 2010-12-20
Yeah, I'm a first timer.

And I haven't a clue what you just asked me to do. O.O

---

### Post by wilee-nilee on 2010-12-20
> **Dangerzone812 said:**
> Yeah, I'm a first timer.

And I haven't a clue what you just asked me to do. O.O

No problem go to the menu-acessories-terminal in the terminal run this.
```
sudo apt-get install dkms
```

You will be asked for the password, it doesn't show in the terminal widow when you type it.

Then go to the Vbox download looks like this right.
[ATTACH]178939[/ATTACH]

Right click on this and click on gdebi it is a installer.

---

### Post by Dangerzone812 on 2010-12-20
Ok, everything worked up until the right click instructions....poop.

---

### Post by Dangerzone812 on 2010-12-20
Oh, I think I may have gotten it.

---

### Post by wilee-nilee on 2010-12-20
> **Dangerzone812 said:**
> Oh, I think I may have gotten it.

I think you can, I think you can.;)

---

### Post by Dangerzone812 on 2010-12-20
Ok, I thought I had it, false alarm,I ran it under the gdebi program, but now i don't see the Virtual box option under options :O

---

### Post by wilee-nilee on 2010-12-20
> **Dangerzone812 said:**
> Ok, I thought I had it, false alarm,I ran it under the gdebi program, but now i don't see the Virtual box option under options :O

In Ubuntu it is tools. Don't remember the equivalent in Xubuntu.

Not sure why I thought you are running Xubuntu.;) which desktop are you running, not sure what options is.

---

### Post by Dangerzone812 on 2010-12-20
It works! Thank you so, so much!

---

### Post by wilee-nilee on 2010-12-20
> **Dangerzone812 said:**
> It works! Thank you so, so much!

good deal.

---

