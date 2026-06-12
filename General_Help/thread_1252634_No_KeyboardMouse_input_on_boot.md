---
title: "No Keyboard/Mouse input on boot"
date: 2009-08-29
forum: General Help
---

### Post by ajmedfor on 2009-08-29
I recently had a problem with Ubuntu not booting due to DRDY and UNC errors... I ran fsck from the recovery kernel and Ubuntu now boots to the login screen. However, my keyboard and mouse do not respond. I am guessing that the bad sector somehow corrupted the input setup, but do not know how to recover it. I can reinstall, but prefer not to since I am travelling at the moment.

If anyone has suggestions it would be greatly appreciated. Thanks!

---

### Post by deymious on 2009-09-02
Same problem. This gets fixed by power cycling the machine, but without keyboard/mouse and being stranded on the login screen I can't get in to find out what is going on.

I'm booting 2.6.28-15 U9.04 on a new Core 2 Duo P7570 (which Intel amusingly disavows, it seems to be a cousin of the P7550 (2.26GHz) ) with 4GB of RAM on a 800Mhz chipset. It feels like a timing issue to me... like something is starting too fast to get a necessary signal/interrupt.

---

### Post by NoaHall on 2009-09-02
try using "sudo dpkg-reconfigure -phigh xserver-xorg" to rebuild your xorg.conf file.

---

### Post by ajmedfor on 2009-09-14
Sorry for the slow response... I have been traveling for the last few weeks and havent had time to try and fix this.

I tried the sudo dpkg-reconfigure -phigh xserver-org, but to no avail.

I also ran FSCK which detected a good deal of errors. After pushing the yes key a few thousand times it finally finished. I can now run it without getting any errors. I have also tried to run the "fix broken packages" option from the recovery kernel, as well as re-installing the Ubuntu desktop. Still, there is no input from either the keyboard or mouse at the bootup screen.

It seems that something is lost in whatever it is that mounts the hardware when going to init2. I dont know enough to know which packages I should repair to try and fix this?

Simplest solution would probably be to re-install, but I am away from home and dont have an external HDD, so a fix would be great even if it means losing some of the custom settings in Ubuntu.

---

### Post by P4man on 2009-09-14
You could adding acpi=noirq to your kernel. If you're not sure how, look here:
[http://ubuntuforums.org/showpost.php?p=7947460&postcount=24](http://ubuntuforums.org/showpost.php?p=7947460&postcount=24)

---

### Post by ajmedfor on 2009-09-14
thanks for the quick response, but it didn't work. I also tried re-installing all the ACPI modules, but that didn't help either. I don't understand how the keyboard can work at the command line, but the input is lost when I try to boot to the GUI. Can anyone explain?

---

### Post by P4man on 2009-09-14
have you tried making a new user account and logging in with that? That way, at least you could find out if its a system wide issue (probably X) or account specific (something wrongly configured?)

from a terminal try:

```
sudo adduser testuser
sudo passwd testuser
```

---

### Post by ajmedfor on 2009-09-15
I think it is definitely user independent, since I cannot log on at all. The inputs cease to work at the login screen. As soon as the cursor and graphics appear, I cannot do anything. If there is some way to boot under another user which might help, then let me know.

---

