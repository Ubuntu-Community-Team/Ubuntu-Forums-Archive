---
title: "Continuous Loop Login"
date: 2009-11-03
forum: General Help
---

### Post by brimano on 2009-11-03
I was using 9.04 and updated via the update manager to 9.10.

After it done it's downloading/updating/installing stuff it rebooted and then it asked for my password as usual. I noticed it had my username already written (i dont know if thats a new feature) . I typed my password, it started to load, went black for a second, showed it loading again with the ubuntu screen then it went and asked for a password again. It done it 6-7 times then it let me in. My password is only 3 letters so I wasn't getting it wrong

I rebooted again just to test and it done the same again. Has this happened to anyone else? Not sure what to do!

---

### Post by P4man on 2009-11-03
if the password is wrong it looks different as what you describe, so it looks like it logs you in and immediately out again. There used to be an error popup  that read:
> 
"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem."

If you google on that error (first line) you will find a ton of information on what could be the cause or how to fix it.

---

### Post by brimano on 2009-11-04
Thanks for the reply, I tried several methods, the latest one was some sudo chown command and an Ice one but it still done the same thing on boot up.

The whole Ubuntu seems painfully slow, opening programs it seems to just hang. The login still takes 5-6 attempts before I'm in. I really don't know what to do

---

### Post by P4man on 2009-11-04
did you verify your / partition is not full ?

---

### Post by Malcolm on 2009-11-10
I hope this can still be useful. I had the exact same issue after upgrading to Ubuntu 9.10. I soon discovered that I could log into the Gnome desktop after deleting the ~/.config directory from the console. I was then able to reboot and login again.

Ubuntu doesn't detect my screen's refresh rate correctly (resulting in a slightly shifted and shrinked image on my LCD monitor), so I changed that setting in Gnome, rebooted... and the "infinite loop login" issue was back.

I ended up editing xorg.conf (shouldn't Ubuntu not be using that anymore? I guess I'd got that wrong), so I wouldn't have to change that setting in Gnome, and deleted the ~/.config directory again, and the problem was solved; I can now log in and out and use my system normally as I did before the upgrade, but I suppose I'd be in trouble if I needed to change resolution/refresh rate.

---

### Post by markweaver on 2009-11-15
I am also having this problem. Karmic worked fine until an update I installed about a week ago. If I use ctrl-alt-F1 to get a text login, I can login, but if I try to run the graphical interface using startx, it says X is already running. /etc/init.d/gdm stop does not close X. /etc/init.d/xdm stop says xdm is not running. I can log in from the recovery option and run startx to get to the graphical interface. The computer has an Nvidia GeForce 256 video card. I deleted the xorg Nvidia video card drivers using the mark for complete removal option in the  synaptic package manager, and the login loop problem stopped. However, that leaves a maximum of 1024X768 for the display. Reinstalling the xorg Nvidia video card drivers brings the login loop problem back. I don't know what to do at this point.

I should add that doing a clean install of Karmic stops the login loop, until updates are installed. I did notice an Nvidia update in the package, but highlighting the xorg nv drivers  in the synaptic package manager, package pulldown menu, does not give the option to force a version; that option is grayed out. The xorg nv drivers are version 1.2.1.14-2ubuntu3, and are the latest version.

---

### Post by popnowlin on 2009-11-21
I started to get the same problem as brimano after updating about a week ago.  My koala had worked just fine up to that point.  I have an nvidia card and have the correct drivers installed so I can use the full 1920x1200 resolution.  I have a triple boot system with Vista, 8.04 and 9.10 on it.  The 8.04 system works fine with the nvidia drivers.

I can't pin down what triggered the problem, but it's sure annoying.  I've tried most of the fixes I've seen in this and other forums, short of reinstalling from the CD.  Nothing seems to fix the problem for me.

The easiest workaround I know is to boot on the recovery image.  When it starts up in the CLI, login and execute **startx**.  That works for me every time.  I'd love to find a real solution but that's the best I have to offer.

---

### Post by j_neish on 2010-02-02
Try looking at my similar/same problem here
[http://ubuntuforums.org/showpost.php?p=8726825&postcount=44](http://ubuntuforums.org/showpost.php?p=8726825&postcount=44)
maybe you can also patch over the cracks in Ubuntu.

---

### Post by johnnycasher on 2010-04-21
i have this exact problem:
 
Acer 6930G / ati hd 4650
 
installed Karmic
 
Everything's fine
 
i installed the propriety drivers from ATI 
 
And suddenly i have this loop problem i can't stuck out of this..

---

