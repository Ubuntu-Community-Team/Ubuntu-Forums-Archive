---
title: "What replaced &quot;grub&quot;?  Need to edit startup menu"
date: 2011-04-24
forum: General Help
---

### Post by JohnFDay on 2011-04-24
I run multiple systems on my computer...Ubuntu 9.10,  Ubuntu 10.04 and Windows 7.

It seems that every time there's an upgrade to either Ubuntu system, my startup menu list gets longer.

I remember being able to edit the "grub," but it's gone now.

Is there a way to edit this startup list, and delete older versions, instead of it getting longer and longer?

Thanks in advance.

---

### Post by WorMzy on 2011-04-24
grub was replaced with grub 2. [You have to edit configuration files now]("https://help.ubuntu.com/community/Grub2"), then run update grub. If you'd rather not bother with that rubbish, you can just [reinstall grub legacy]("http://www.terabyteunlimited.com/kb/article.php?id=232").

---

### Post by hal8000 on 2011-04-24
Its been gone for some time, luckily drs305 has wrote a great howto:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

As an alternative to grub2 you may want to look up burg, which gives you graphical entries for your linux installs, screenshot on RHS at themes:


[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by coffeecat on 2011-04-24
You are accumulating a load of old kernels, each of which will have two entries (normal and recovery) in the grub menu. 

In Lucid/10.04, for example your latest kernel will be version 2.6.32-30 which you will want to keep. But you may still have version 2.6.32-24 which you can uninstall. Open Synaptic and search for "2.6.32-24". You'll find three or four packages corresponding to that version. Mark them all for complete removal. Repeat for any other kernel versions you do not want, but it is a good idea to retain the version immediately preceding the current one. Do this for each of your Ubuntu installations and the grub menu *should* be updated automatically. If it isn't, in the installation of Ubuntu that has the controlling grub menu, open a terminal and run:

```
sudo update-grub
```> **JohnFDay said:**
> I remember being able to edit the "grub," but it's gone now.

No, you still have grub, otherwise you wouldn't be able to boot anything. I think you mean that in the days of legacy grub you had a file called /boot/grub/menu.lst which you could edit directly. Since Ubuntu 9.10, grub2 has been installed and things are a little more complicated now. See:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

That being said, simply editing a grub menu to remove unwanted kernel entries is not a good idea because you are left with all the unused kernel files which take up a lot of room. Uninstalling unwanted kernels is the way to do it.

---

### Post by JohnFDay on 2011-04-24
To all....I got into the synaptic area and uninstalled all but the actual versions I'm running, but when I rebooted, the list still showed all the versions.  I then installed the GRUB2 and ran it.

When I rebooted again, all the OLD, UNWANTED versions were no longer being shown.  That is exactly what I wanted.

THANKS TO EVERYONE WHO REPLIED!

John Day

---

