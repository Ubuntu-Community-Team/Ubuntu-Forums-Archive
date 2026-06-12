---
title: "How to uninstall ubuntu 10.10???"
date: 2010-11-11
forum: General Help
---

### Post by samrat94 on 2010-11-11
How do I uninstall Ubuntu 10.10 using the 10.04 live cd?? I have Ubuntu installed at sda4. 

Also, I plan to install 10.04(instead of 10.10 because 10.10 ran a bit jerky). Do you recommend that I do a wubi install or from the live cd??

---

### Post by dcstar on 2010-11-11
> **samrat94 said:**
> How do I uninstall Ubuntu 10.10 using the 10.04 live cd?? I have Ubuntu installed at sda4. 


Just install 10.04 on the same partition and select the option to format it.

---

### Post by BoBeau on 2010-11-26
I am having problems with this.  I never saw an option to format it.  I tried to install 10.04 in the same partition as 10.10.  Now I have two boot options, and both of them are 10.10.

BTW... I am a newbie and speak little computer language.  English?  Fluent! Computer jargon?  Beginner.

Thanks for the help!

---

### Post by ivarn on 2010-11-26
Do you dual boot or is ubuntu the only os you have on your pc?
If your not dual booting, run the option where it  says "this will delete ubuntu 10.10".

---

### Post by WorMzy on 2010-11-26
> **BoBeau said:**
> I am having problems with this.  I never saw an option to format it.

You should get to a screen like this one during the installer (if you choose to set up partitions manually):
[[IMG]http://img413.imageshack.us/img413/6999/ubuntuinstallpartitioni.th.jpg[/IMG]](http://img413.imageshack.us/i/ubuntuinstallpartitioni.jpg/)

Double-clicking a partition here will give you a window asking you what to use the partition as (e.g. /, /home/, /boot/, etc), what filesystem you want to use (e.g. ext2, ext3, ext4, reiserfs, etc), and whether you want to format it. You may also be able to check the checkbox which appears in the table (in the image), I can't remember.

If you didn't format it when you installed, chances are the old kernel was left behind, and that's what the second entry in grub is. You might want to reinstall Ubuntu, formatting the partition this time, just in case the remnants of the old install cause problems (or take up too much space).

---

