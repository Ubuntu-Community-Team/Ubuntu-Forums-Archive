---
title: "Lost the Will to Live - GRUB2"
date: 2009-12-14
forum: General Help
---

### Post by Quarkrad on 2009-12-14
I have sda1 ubuntu 9.10 and sda2 winxp.  Just reinstalled ubuntu to sda1.  Now PC boots without grub - when I first installed it picked up winxp on sda2.  So installed grub2 on 9.10 and when I type update-grub2  I can see grub.cfg going through picking up things, but no winxp.  When I reboot still no grub - straight through to Ubuntu.  I know know know grub2 is better than grub1 but if one is a newbie to ubuntu (only had it since 8.10) and it is 20.41 and close to bed time it is very trying when trying to work out what to do.  The countless pages on how to get my winxp partition showing on grub2 and it loading with the choice of boot is driving me mad.  It is all too complex.   If ubuntu was not so good I would junk this whole Grub business and go back to windows.  Win OS is c*$)p but at least getting multiple things to boot was nothing as complex as GRUB2.  Is this really for the 'great unwashed'?  HELP

---

### Post by drs305 on 2009-12-14
Sorry you are having problems with Grub 2. To display the menu, you can hold down the SHIFT key during the early boot stage to display the menu. 

Normally even when G2 doesn't pick up Windows during the initial install it *does* see it when "sudo update-grub" is run after the installation.

If you can't get G2 to find your XP install, you could make an entry in the /etc/grub.d/40_custom file. A typical Windows entry would look something like this:
> 
menuentry &#8220;Windows XP on sda1"  {
set root=(hd0,1)
chainloader +1
}


---

### Post by estyles on 2009-12-14
It's unlikely that it's "booting without grub."  Most likely your timeout is set to 0.  I know how to fix that in regular grub, but not so sure in grub2.  Take a look in the config file for timeout, and/or search on the forums for that.

---

### Post by Quarkrad on 2009-12-14
Thanks - I think I may have found my problem but do not know what to do.  When I fire up gparted it shows a yellow triangle against sda2 - my NTFS boot partition.  The information shows it as not mounted.  I have a number of NTFS partitions - one (sda2) has winxp on it - the other are jut for storage.  I installed NTFS Configuration Tool when I installed 9.10 to ease the NTFS partitions mounting but it looks like sda2 has gone missing.  somehow I need to make sda2 visible.

---

### Post by estyles on 2009-12-15
It's normal for your windows partition to not be mounted when you are running in Linux.  You can mount it, but I'm not sure that will help.

Have you figured out how to get your grub timeout fixed?

Check your grub.cfg file.  There should be a section like: ```
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
```

That's what mine says, and the timeout defaults to 10.

Also check in the file and see if it has Windows as a "menuentry".

I have a feeling there's a graphical tool for modifying your grub config, but I don't know what it is...  If you give some info about what your grub.cfg file says, that may help fix the problem.

---

