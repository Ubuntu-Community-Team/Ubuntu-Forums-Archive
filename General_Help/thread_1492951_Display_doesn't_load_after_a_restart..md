---
title: "Display doesn't load after a restart."
date: 2010-05-25
forum: General Help
---

### Post by Veren on 2010-05-25
Hello everyone
I have a huge problem I can't move with.
I bought an Asus N61JV laptop and put Ubuntu on it. There was a  proprietry software (graphic card booster from nvidia) that asked me to  restart the laptop afterwards. I did so, however, the laptop won't boot  at all not. It doesn't respond to anyhing, I only hear it working. All I  can do is turn it on and off. I'm getting desperate, I've had it for  like 2 hours! Please help me, I'm almost crying. I'm not an experienced UNIX user and I  totally don't know what to do. It boots until the point where I see  Ubuntu writen and then the display like turns off. I can't even put windows there, it dosn't react to f9 or anyhing.

---

### Post by dino99 on 2010-05-25
at the end of bios process, hold "shift" key down to be able to see the grub menu. There, select the boot line, edit it (e) and add video=vesa before quiet splash. Then press "x" to boot.

we will see what to do after

---

### Post by Veren on 2010-05-25
Ok, I did that.

---

### Post by dino99 on 2010-05-25
i cant believe you cant see the bios process: check its settings first, see the manual to know how to do.

uncheck the logo to popup and check verbose mode to see the details on boot time.

if you cant do anything more, reinstall lucid from scratch using this :

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

and dont use the nvidia marketing crap

---

### Post by Veren on 2010-05-25
MY friend
I apologize for being such a noob. 
But all I need to do is get my laptop to factory settings.
I installed Ubuntu on it as the first OS and I've had it for 1 hour before I couldn't use it anymore. All I want is to get my laptop work. Is there any way I can remove it without actually loading it ? Becouse the parted magic doesn't load.
I got into some menu when I pressed shif after bios. There were 2 recovery options which do nothing and 2 normal options where I added the video=vesa line. nothing happened.

---

