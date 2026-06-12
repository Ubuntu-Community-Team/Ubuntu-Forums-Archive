---
title: "Grub2 default boot options?"
date: 2011-08-27
forum: General Help
---

### Post by Lutcikaur on 2011-08-27
Ive been searching around for the last few hours, and i cant exactly find out what people are doing when they are changing around their 40_custom file, (because i dont have a menu.lst)

Basically what im trying to do is so that if i turn on my laptop and walk away, it boots into windows, but i have the option of going into linux if i want to, basically making the default windows (6th down on the list)..

i already went into boot/grub/grub.cfg and changed default at the top to 6. which changed nothing and im kinda scared at what i changed.. 

But, Yea basically i just want the selector to be over windows 7 by default. 

Thanks in advance.

---

### Post by grahammechanical on 2011-08-27
You need to study these two links

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

[http://ubuntuforums.org/showthread.php?p=10340183]("http://ubuntuforums.org/showthread.php?p=10340183")

You are not supposed to edit grub.cfg directly. It gets updated by running sudo update-grub. This process examines what is written in those other grub files, such as 40_custom, which we can edit and then writes out a new grub.cfg. This also happens whenever you do a system update that installs a new kernel. 

I recommend that you install Grub Customizer and use that to set the boot order. It is safer.

Regards.

---

### Post by raja.genupula on 2011-08-27
[http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html](http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html)

---

### Post by oldfred on 2011-08-27
I do not believe startup manager has yet been updated to work with grub1.99's nested menus. So if you have 11.04 do not use startup manager. Grub customizer is a good solution.

If you really want to do it manually you have to get the grub configure file and grub starts counting at 0, so if it is the 6th line enter 5 on grub_default line.

But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

