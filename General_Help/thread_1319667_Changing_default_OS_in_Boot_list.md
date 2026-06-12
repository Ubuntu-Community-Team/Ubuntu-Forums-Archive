---
title: "Changing default OS in Boot list"
date: 2009-11-08
forum: General Help
---

### Post by chirag64 on 2009-11-08
Hello, I recently downloaded and started using Ubuntu 9.10 (which is great, btw). I've installed it on a multi-boot system which also includes my Windows XP alongside.

What I wish to do is change my default OS to XP in the boot list, so that I don't need to select it everytime the pc boots, and also, I want to change the time (10-second time) that is allowed to select which OS to boot from.

Is this possible to do from Windows, because I'm still not very comfortable to do so in Ubuntu.

And if I've to do it in ubuntu, please guide me step by step because I'm a complete newbie to Ubuntu.

---

### Post by Minsky on 2009-11-08
I don't know if its possible to do it from within windows, but this is the Ubuntu way. The GRUB menu entries are stored in **/boot/grub/grub.cfg** but you must not edit this file. Instead, you need to edit **/etc/default/grub** which is one of the configuration files used to update GRUB. Look in **grub.cfg** to determine the position of XP within the GRUB menu list, the menu entries will be in a block beginning with the header **### BEGIN /etc/grub.d/10_linux ###** and each menu entry is preceded with the keyword **menuentry**. Menu entries start at position 0, so if XP is 4th in the list its menu entry position will be classed as 3.

First of all back up the **grub.cfg** and **grub** files by opening a terminal window and typing

```
sudo cp /boot/grub/grub.cfg /boot/grub/grub.cfg.bkp
sudo cp /etc/default/grub /etc/default/grub.bkp
```

With the backups done you can then edit the configuration files, so in the terminal window, type

```
sudo gedit /etc/default/grub
```

Towards the top of the file you'll find an entry **GRUB_DEFAULT=0**. Change the value to whatever the position of XP is within the menu list (remember that menu entries start at position 0).

A few lines further down you''ll also find the entry **GRUB_TIMEOUT=10**. This is the delay countdown and you can change this value to your preference (alter it to -1 if you do not want the countdown). Save the file after you have completed the alterations and back in the terminal window type in

```
sudo update-grub
```

This will update the **grub.cfg** file and your changes will come into effect when you reboot.

---

### Post by Minsky on 2009-11-10
Just found this excellent How To by drs305 on how to configure GRUB2. Lots of information here [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by chirag64 on 2009-11-11
Thnx a lot. Tried all the terminal commands you gave and it worked great :D

---

### Post by B.Hat on 2009-11-24
I figure I'll dig up this thread rather than start a new one that is so similar.

The solution posted here worked fine for me, having my 6th option (Windows XP) boot as default for most of my family to use, **UNTIL** the kernel got updated, at  which point the computer began booting to "memory test" by default, making it all-but inaccessible to the simple users in my family.

Is there a way to specify the default OS that will be OS specific, and not entry number specific?

If not, is there a way to have Ubuntu delete the old kernel version upon update so it is also removed from GRUB 2? (Yeah, I know this option isn't very safe, but it is unacceptable to have GRUB switch the default OS every time the kernel is updated.)

---

### Post by blur xc on 2009-11-24
I changed my boot order, IIRC, by simply changing their order in the menu.lst file.  A little copy/paste action in gedit...

BM

---

### Post by Don1500 on 2009-11-24
Blur,
Are you using Grub2, with Ubuntu 9.10? (Bet your not)

Others, (IIRC since I'm at work on a windows machine) BUT... System=>Administration=>Start-up Manager=> Pick the one you want to start first. It's there, just like in 9.04 and earlier, and it works.

---

### Post by blur xc on 2009-11-24
> **Don1500 said:**
> Blur,
Are you using Grub2, with Ubuntu 9.10? (Bet your not)


yup- my bad, missed that part, I'm hanging out on 9.04 for now.

BM

---

### Post by blur xc on 2010-01-05
I finally got around to doing a few Karmic installs and I now understand...  

My question is, how do you re-order the selections in the boot menu?  Right now, there are two ubuntus on top, a recovery mode, memtest, and way down at the bottom there are the two windows optons- xp (or vista, depending on the computer), and then the windows restore option.  

At the very least, I'd like to two main boot options Ubuntu and Winows, to be #1 and #2 on the list.  the rest beyond that.  What would be nice, is if you could hide the rest of the options (maybe have some key to expand the list and show hidden options).  If hiding is impossible, a space to separate the normal boot os's from the other ones would be nice.  I've got kids, from 5 to 9 yrs old, and I don't need them booting into recovery mode, or worse, windows restore mode, by accident.

Thanks,
BM

---

### Post by drs305 on 2010-01-05
> **blur xc said:**
> 
My question is, how do you re-order the selections in the boot menu?  Right now, there are two ubuntus on top, a recovery mode, memtest, and way down at the bottom there are the two windows optons- xp (or vista, depending on the computer), and then the windows restore option.  

At the very least, I'd like to two main boot options Ubuntu and Winows, to be #1 and #2 on the list.  the rest beyond that.  What would be nice, is if you could hide the rest of the options (maybe have some key to expand the list and show hidden options).  If hiding is impossible, a space to separate the normal boot os's from the other ones would be nice.  I've got kids, from 5 to 9 yrs old, and I don't need them booting into recovery mode, or worse, windows restore mode, by accident.
Thanks,
BM

There are various ways. You can really get into the nuts & bolts of the Grub 2 scripts and hack away. I wrote a guide on G2 tweaks that give some examples of how to do this. These include renaming the titles, hiding certain entries, etc. Caution - geek alert.
[Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602")

You can hide the Recovery Mode options from within /etc/default/grub by removing the # symbol:    "GRUB_DISABLE_LINUX_RECOVERY="true"

A lot easier would be to make a custom menu or edit /etc/grub.d/40_custom. You can copy any of the entries in /boot/grub/grub.cfg, paste them into the 40_custom file (leave the top three lines). At that point, you can reorder them, change the titles, etc.

If you want these entries at the top of your menu, name the file 06_custom (and make it executable).

Run "sudo update-grub" to incorporate these entries into your grub menu.

The advantage is that you can easily edit the file contents. The disadvantage (and advantage) is that the contents will NOT change, even if new kernels are installed or parititions change.

If you don't want to include duplicate entries which would appear from 10_linux, 30_os-prober, etc, make them unexecutable. If you do this however, you would lose updated entries when "sudo update-grub" is run in the future.

**Added: ** You mention your kids and entries you don't want them to be able to boot. I've also written a guide on password protection:
[Grub 2 Password Protection]("http://ubuntuforums.org/showthread.php?t=1369019") and the Title Tweaks mentioned earlier has ways to hide the Windows Recovery menu option (PW would be easier).

---

### Post by blur xc on 2010-01-05
> **drs305 said:**
> There are various ways. You can really get into the nuts & bolts of the Grub 2 scripts and hack away. I wrote a guide on G2 tweaks that give some examples of how to do this. These include renaming the titles, hiding certain entries, etc. Caution - geek alert.
[Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602")

You can hide the Recovery Mode options from within /etc/default/grub by removing the # symbol:    "GRUB_DISABLE_LINUX_RECOVERY="true"

A lot easier would be to make a custom menu or edit /etc/grub.d/40_custom. You can copy any of the entries in /boot/grub/grub.cfg, paste them into the 40_custom file (leave the top three lines). At that point, you can reorder them, change the titles, etc.

If you want these entries at the top of your menu, name the file 06_custom (and make it executable).

Run "sudo update-grub" to incorporate these entries into your grub menu.

The advantage is that you can easily edit the file contents. The disadvantage (and advantage) is that the contents will NOT change, even if new kernels are installed or parititions change.

If you don't want to include duplicate entries which would appear from 10_linux, 30_os-prober, etc, make them unexecutable. If you do this however, you would lose updated entries when "sudo update-grub" is run in the future.

**Added: ** You mention your kids and entries you don't want them to be able to boot. I've also written a guide on password protection:
[Grub 2 Password Protection]("http://ubuntuforums.org/showthread.php?t=1369019") and the Title Tweaks mentioned earlier has ways to hide the Windows Recovery menu option (PW would be easier).

Thanks- that's a lot of geek info to digest.  I'll study it and see what I can do (and hope to not break anything)...

BM

---

### Post by drs305 on 2010-01-05
> **blur xc said:**
> Thanks- that's a lot of geek info to digest.  I'll study it and see what I can do (and hope to not break anything)...

BM

I know. But it's one of the great things about Linux. You aren't confined to one way of doing things.

If it's intimidating, you can't break anything by creating a custom 06_custom or 40_custom file and leaving everything else the way it is. Well, if it breaks it wouldn't be from anything in the custom file anyway. ;-)

---

