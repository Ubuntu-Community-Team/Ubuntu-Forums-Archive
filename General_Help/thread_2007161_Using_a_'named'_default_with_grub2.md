---
title: "Using a 'named' default with grub2"
date: 2012-06-20
forum: General Help
---

### Post by brianmc on 2012-06-20
I've been trying to sort out a laptop for work such that, by default, GRUB2 will boot into Windows 7.

As you probably know, kernel upgrades (and removal thereof) can change the number of entries in the grub menu, with "Windows 7 (loader)" always being the last one.

Per the manual, I'm trying to use the GRUB_DEFAULT=<whatever>  option to always select this.

I've tried:
GRUB_DEFAULT="Windows 7 (loader)"
GRUB_DEFAULT="Windows 7"
GRUB_DEFAULT='Windows 7 (loader)' and
GRUB_DEFAULT='Windows 7'

Yes, I'm always running 'sudo update-grub2' after editing /etc/default/grub

Has anyone else managed to get a named windows entry to be the default boot? If so, how?

---

### Post by YannBuntu on 2012-06-20
I think you need to use the entire string which is in the grub.cfg, for example:
```
Windows 7 (loader) (on /dev/sda2)
```

---

### Post by NotSoRandomUsername on 2012-06-20
You need to edit /boot/grub and Move the windows entry to the top. You can define the timeout in there too. open gedit as root otherwise you wont be able to edit it.

---

### Post by brianmc on 2012-06-20
> **NotSoRandomUsername said:**
> You need to edit /boot/grub and Move the windows entry to the top. You can define the timeout in there too. open gedit as root otherwise you wont be able to edit it.

That's plain wrong.

As soon as a new kernel version is installed /boot/grub would be regenerated. You're not supposed to edit that file, and the documentation clearly states so.

I'll try using the full string with device later on.

---

### Post by Cavsfan on 2012-06-20
You could look at the how to in my signature. It sets the default and you never have to mess with it when 
a new kernel gets loaded. I tri-boot Windows 7, Lucid Lynx 10.04 and Precise 12.04.

There is a picture of my current grub2 screen on one of the last posts in the thread.

However, I'll find that command for you.

---

### Post by Cavsfan on 2012-06-20
I could not find it. All I could find was setting it to a number with the starting menu entry being 0.
There is a way I believe but, I like my way better. Even when a new kernel gets installed the default doesn't change.
It is a bit tedious but, it is fairly straight forward. you just edit the 40_custom file and then save it as 06_custom and make it executable.
That way it will be at the top and when you are comfortable with it you can make the rest of the menu entries unexecutable so they do not show.
Just remember to enter **sudo update-grub** every time you make a change to any of of the grub files mentioned.

---

### Post by NotSoRandomUsername on 2012-06-20
Cavsfans solution sure sounds better lol. Just trying to help out. Obvisously I did not succeed.

---

### Post by philinux on 2012-06-20
This [http://askubuntu.com/questions/82928/how-to-make-windows-boot-first](http://askubuntu.com/questions/82928/how-to-make-windows-boot-first)

Or what i did was use easybcd. This would require restoring the windows bootloader.

---

### Post by drs305 on 2012-06-20
> **YannBuntu said:**
> I think you need to use the entire string which is in the grub.cfg, for example:
```
Windows 7 (loader) (on /dev/sda2)
```

What YannBuntu said. Use everything between the quotation marks.

---

### Post by oldfred on 2012-06-20
I find it easier to just copy the entry from what os-prober found and is in grub.cfg.

find your windows entry in this and copy to grub default like this Vista entry:
gedit /boot/grub/grub.cfg
and copy into grub_default  here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new :
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

I think I learned this from drs3052's threads :)

The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

