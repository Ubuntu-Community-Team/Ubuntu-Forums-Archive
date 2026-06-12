---
title: "boot up options getting bigger. whats going on?"
date: 2011-03-05
forum: General Help
---

### Post by surfmonkee on 2011-03-05
meerkat installed on a fujitsu laptop.

what on earth is going on here, as ubuntu updates i am getting more and more choices at the log in screen and now i have around 11 choices and its driving me nuts

ubuntu, with linux 2.6.35-27 generic
ubuntu, with linux 2.6.35-27 recovery

ditto 

2.6.35-26,
2.6.35-25,
2.6.35-24,
2.6.35-22 

plus the windows partition  

and mem text and mem test console.

11 options to choose from, of course the thing boots automatically in to the newest version but why on earth after updates am i left with 11 boot in options and how much bigger is this list going to get?

can i remove some of the older versions? if so how?

why does it do this? in six months time i could have 100 options! its driving me nuts. maybe its my OCD but this many options at boot up is a joke for me and i want to tidy it up!

---

### Post by TopEnder on 2011-03-05
> **surfmonkee said:**
> meerkat installed on a fujitsu laptop.

what on earth is going on here, as ubuntu updates i am getting more and more choices at the log in screen and now i have around 11 choices and its driving me nuts

ubuntu, with linux 2.6.35-27 generic
ubuntu, with linux 2.6.35-27 recovery

ditto 

2.6.35-26,
2.6.35-25,
2.6.35-24,
2.6.35-22 

plus the windows partition  

and mem text and mem test console.

11 options to choose from, of course the thing boots automatically in to the newest version but why on earth after updates am i left with 11 boot in options and how much bigger is this list going to get?

can i remove some of the older versions? if so how?

why does it do this? in six months time i could have 100 options! its driving me nuts. maybe its my OCD but this many options at boot up is a joke for me and i want to tidy it up!
surfmonkee,  The easy way to remove the kernals you do not want is to install ubuntu-tweak , it is in Synaptic Package manager.

---

### Post by surfmonkee on 2011-03-05
thanks, i shall investigate, is there anything i should know before i go removing kernels?  

of course i realise i have to keep the latest version, but what would be sensible to dump and keep?

thanks for the fast response btw, appreciated.

---

### Post by TopEnder on 2011-03-05
surfmonkee,  Use caution, I would leave to two latest kernels [I]f you go through ubuntu-tweak, I think you will find it helpful I think most of it is straight forward but if not sure on any part  -  ask the forum.

---

### Post by surfmonkee on 2011-03-05
done, thanks.

go to ubuntu tweak dot com and get the tool then its easy:

install Ubunt tweak


Once you have installed ubuntu tweak use the following procedure to remove old kernels

Step 1 - Select “Package Cleaner” on the left and “”Clean Kernel” from the right panel.

Step 2 - Press the “Unlock” button at the lower right, enter your password.

Step 3 - Select from the displayed list the kernel images and headers you wish to remove. The kernel in use is not listed.

step 4 -  Press the “Cleanup” button at the lower right to remove the selected kernel images and headers.

---

### Post by domu on 2011-03-06
While Ubuntu Tweak may be easier for those with a GUI, I have a bash script which allows easy removal of old kernels and works without a GUI (for instance, if you have Ubuntu Server), and may also work with other non-Ubuntu Debian-derived distros.

See [remove-kernel here]("http://www.timedicer.co.uk/remove-kernel").

Dominic

---

### Post by magnatron on 2011-03-08
Since upgrading to the newer 2.6.35-27-generic kernel I've noticed an a few odd changes.  The screen brightness buttons no longer work, when the AC power is not plugged in I loose the default splash I have setup in Plymouth and it reverts to a blinking cursor and text ergo no splashy unless I plug the AC back in.  

I tried all of the following fixes to no avail;  

sudo dpkg-reconfigure plymouth 
sudo echo FRAMEBUFFER=y >/etc/initramfs-tools/conf.d/splash 
sudo update-initramfs -u 

I'm using the following graphics chipset in a dell inspiron 11z  

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)  

Ubuntu tweak has the option to adjust the screen brightness also but I found if its on the AC power the screen is bright, but even if I set the brightness to 100% in ubuntu-tweak and then remove the AC power and reboot it reverts to 50% brightness with ubuntu-tweak insisting it's set at 100%  
Buggy.. (Sys-V & Debian is looking tempting right about now after one whole hour of chasing this issue):lolflag:

---

