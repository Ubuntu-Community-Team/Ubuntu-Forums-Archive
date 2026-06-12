---
title: "won't boot after hibernation"
date: 2011-10-18
forum: General Help
---

### Post by spicyfish on 2011-10-18
Hi, I hibernated my laptop, and now whenever I try to boot up, it fails.
It goes through BIOS, grub (I choose the first option, which is my ubuntu 10.04.3 partition), and then it gets to the black screen with the blinking underscore. After 10 seconds or so, it will say "resume: libgcrypt version: 1.4.4", then the ubuntu startup screen appears for a second or two, and then instead of going to the login menu, the screen will go all black and there is nothing I can do but do a hard reboot.

I don't care about what I saved during hibernation (It is okay to lose  that unsaved information. I think I lost it in 3) below anyway). I just want to boot up normally.

May be related information: 
1) Hibernation used to not work, so I followed this guide to get it to work: [http://disi.unitn.it/~ferro/index.php/linux/8-suspendhibernate-in-ubuntu-1004-ubs3-problem]("http://disi.unitn.it/%7Eferro/index.php/linux/8-suspendhibernate-in-ubuntu-1004-ubs3-problem")
I have been using this solution for about 2 months with no problems, up till now.
2) There is nothing wrong with my hard drive according to fsck
3)Some stuff i've tried: 
[http://www.mattcutts.com/blog/ubuntu-freeze-no-resume-image/](http://www.mattcutts.com/blog/ubuntu-freeze-no-resume-image/)
[http://superuser.com/questions/121397/how-to-get-rid-of-resume-information-on-ubuntu-9-10-karmic](http://superuser.com/questions/121397/how-to-get-rid-of-resume-information-on-ubuntu-9-10-karmic)
[http://ubuntuforums.org/archive/index.php/t-1489818.html](http://ubuntuforums.org/archive/index.php/t-1489818.html)
Also tried formatting and shredding my swap
4) I can get it to boot by choosing recovery mode in grub and and choosing failsafeX (Run in failsafe graphic mode)

---

### Post by spicyfish on 2011-10-19
bump

---

### Post by kriegoamigo on 2011-10-19
Hey spicy fish I wanna ask you one question.....

Did you use Wubi installer to install Ubuntu ?

---

### Post by spicyfish on 2011-10-19
nope, i used live cd

---

### Post by spicyfish on 2011-10-19
bump

---

### Post by spicyfish on 2011-10-19
i've solved the issue!
tldr: reinstall video card driver.

background: when i first bought my laptop, ubuntu used a generic video card driver, and I had to download one from the ati site to allow 1920x1080 and other stuff

the problem was actually that when i chose to boot into ubuntu from grub, after it attempts to look for hibernated image, it's supposed to go to the login screen, but I guess it "forgot" the video card driver i installed, and did not know to try the generic one. Thus, it would not be able to display the login screen and just be stuck in a black screen forever.

however, when i chose recovery mode in grub /failsafeX, it automatically assumed the generic driver, so it worked fine. here, i reinstalled the new driver and normal bootup worked again. good times

---

