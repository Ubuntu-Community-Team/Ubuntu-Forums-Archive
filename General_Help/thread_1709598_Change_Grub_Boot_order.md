---
title: "Change Grub Boot order"
date: 2011-03-18
forum: General Help
---

### Post by MRRangel on 2011-03-18
Hello,

Absolute beginner here.  I am trying to change the default gnu grub boot order to first go to windows 7.  I entered gksudo gedit /boot/grub/menu.lst and it opened up the file but the file was blank.  It didn't show me the 5 or 6 possible choices.  What should I do?  Thanks

---

### Post by drs305 on 2011-03-18
You are probably using Grub2, which uses different configuration files.

I'd recommend Grub Customizer if you like GUI. If you prefer manually editing files, go to the "Tasks" link. The "Basics" link will probably tell you more than you want to know about Grub 2.

All are linked in my signature line.

---

### Post by MRRangel on 2011-03-18
I don't think I prefer to do it manually, it was just the first response when I googled it.  Thanks for the links.  I'll take a look.

---

### Post by highspider on 2011-03-18
sudo gedit /boot/grub/grub.cfg

GRUB_DEFAULT=0
or
default=0

EDIT THIS TO NUMBER WHICH WINDOWS IS

like if windows is the fourth option in the boot menu edit this to

GRUB_DEFAULT=3
or
default=3

Read these

[http://ubuntuforums.org/showthread.php?t=1306670](http://ubuntuforums.org/showthread.php?t=1306670)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by akakingess on 2011-03-18
I found Startup Manager to work fine for me, and it did the trick and I am using Grub2...just a suggestion, it's also a GUI interface which you might be more comfortable with.

---

### Post by garvinrick4 on 2011-03-18
```
grep menuentry /boot/grub/grub.cfg
```Will show you your menu entry list in grub2 so as to pick right Number for GRUB_DEFAULT

---

### Post by stinkeye on 2011-03-18
> **garvinrick4 said:**
> ```
grep menuentry /boot/grub/grub.cfg
```Will show you your menu entry list in grub2 so as to pick right Number for GRUB_DEFAULT
I came across this command the other day which nicely lists and numbers your grub menu entrys.
```
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
``` 
```
glen@MavMusic:~$ grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
     0	Ubuntu, with Linux 2.6.35-27-generic
     1	Ubuntu, with Linux 2.6.35-27-generic (recovery mode)
     2	Ubuntu, with Linux 2.6.35-25-generic
     3	Ubuntu, with Linux 2.6.35-25-generic (recovery mode)
     4	Ubuntu, with Linux 2.6.35-24-generic
     5	Ubuntu, with Linux 2.6.35-24-generic (recovery mode)
     6	Windows NT/2000/XP (loader) (on /dev/sda1)
     7	LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (on /dev/sdb1)
     8	LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (recovery mode) (on /dev/sdb1)
```

[COLOR="Red"]**@ MRRangel**[/COLOR]
Run the above command to get the number for your windows entry.

Then use ```
gksudo gedit /etc/default/grub
```
to change the boot order.


Change the line 
```
GRUB_DEFAULT=[COLOR="Magenta"]0[/COLOR]
```
to correspond to the number for your windows entry.
Save and close and then run
```
sudo update-grub
```

---

### Post by MRRangel on 2011-03-18
High Spider & all, the udo gedit /boot/grub/grub.cfg entry and change did the trick.  Thanks all for your input.

---

### Post by drs305 on 2011-03-18
> **MRRangel said:**
> High Spider & all, the udo gedit /boot/grub/grub.cfg entry and change did the trick.  Thanks all for your input.

That method will work but you should know it will not survive any update of Grub2. It will be overwritten the next time there is a kernel or grub update. 

The more permanent method is to change the setting in /etc/default/grub or use one of the GUI apps mentioned, which will make the change in the appropriate file.

---

