---
title: "remove ubuntu from dual boot"
date: 2011-05-04
forum: General Help
---

### Post by Mindless Z on 2011-05-04
I'm dual-booting vista and Ubuntu on a Dell studio XPS 16.  I cant upgrade ubuntu and i've run into several errors lately, so i'd like to remove ubuntu all together and start from scratch with 11.04.

I assume formatting the partition would be a terrible idea, so my question is how would i go about properly removing ubuntu and then clearing the partition for reinstallation?  All of this without affecting vista preferably.

thanks in advance,
~Mindless

---

### Post by SavageWolf on 2011-05-04
Is your hard disk fairly large-ish? If so, you should probably install it as a "tri-boot" then, once everything is working, remove the old Ubuntu's partition and run update-grub.

---

### Post by Mindless Z on 2011-05-04
Thanks for the suggestion, i'll try it as soon as i get 11.04 on a disk!

---

### Post by wilee-nilee on 2011-05-04
> **Mindless Z said:**
> Thanks for the suggestion, i'll try it as soon as i get 11.04 on a disk!

If you would like specific information give us a screen shot of the gparted partitioner in Ubuntu you may need to install it.

If you have a real dual boot and not a wubi install, and the grub menu is what you see to choose Vista or Ubuntu when powering on, if you just remove the Ubuntu, you will need to reinstall the vista bootloader to the mbr.

To be honest here with the wording so far and the very vague response so far not really confirming your set up I'm a bit concerned your on the correct track.

---

### Post by WorMzy on 2011-05-04
Two things you need to bare in mind

1) Deleting your existing Ubuntu partition will leave your computer without a bootable OS (more or less). The reason for this is that grub (the bootloader that lets you boot either Ubuntu or Windows) stores most of it's information on the Ubuntu partition. So by removing Ubuntu, you'll leave yourself with a grub rescue prompt, since it can't find any of it's files.

2) Ubuntu can easilly be installed *over* Ubuntu. You can simply mark the existing Ubuntu partition for use as /, and then check the "format" checkbox to make the installer reformat the partition, deleting the old files.

These things being the case, I recommend that you either go with the tri-boot suggestion made by SavageWolf, OR, backup all your important files (from /home and /var/www if you host a website), then install the new version over the old.


If you want to remove Ubuntu and just have Windows, you'll need to reinstall the Windows bootloader. You'll need a Windows installation/recovery disk for this.

---

### Post by Mindless Z on 2011-05-04
Ok so apparently my ubuntu partition is farther gone than i thought.  I tried to boot into ubuntu and it wont let me. i get to a black screen where i can see my cursor but nothing else.

> Ubuntu can easilly be installed over Ubuntu. You can simply mark the existing Ubuntu partition for use as /, and then check the "format" checkbox to make the installer reformat the partition, deleting the old files.


so if i take an 11.04 live cd and install ubuntu over my current partition (with format checked) it should work with minimal issues?


btw to answer a previous question i have a proper dual boot, not wubi

---

### Post by WorMzy on 2011-05-05
Yes. Just make sure that you choose to manually partition your disk when asked how you want to install. Don't let the installer install side-by-side or use the whole disk.

Once the install is completed, you may need to run
```
sudo update-grub
```
in order to be able to boot into Windows again.

---

### Post by Mindless Z on 2011-05-05
The liveCd gave me the option to replace my current copy of ubuntu.  I chose that and it appears to have worked perfectly.  thanks for the help

~Mindless

---

