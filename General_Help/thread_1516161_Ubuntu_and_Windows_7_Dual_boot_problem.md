---
title: "Ubuntu and Windows 7 Dual boot problem"
date: 2010-06-23
forum: General Help
---

### Post by lukster91 on 2010-06-23
Hey all,

My Acer Aspire 5920 is dual booted with Windows 7 and Ubuntu 10.04 64-bit. 

A while ago Windows 7 just stopped booting after the boot selection options. I'd select Windows 7, and there would be a "_" in the top left hand corner, and it would just remain there. 
After a while if I hit any keys it would just bleep. 

Windows 7 is intact, I can access the files through Ubuntu etc - the problem is between selecting Windows 7 and then that connecting to load Windows 7 (At least I'm quite sure it is). Short of reinstalling Windows 7 (which as I am sure you all know is a painful process of redirecting calls, and people telling you for 5 minutes that formatting will delete your files.), I'm not sure what to do. I've tried reinstalling Ubuntu in the hope that would reinstall the Operating System selection process. No such luck.

Any ideas?

Thanks.

---

### Post by vel. on 2010-06-23
Have you tried to reinstall GRUB ?
I'm guessing since it doesn't load windows 7 from the partition its possibly that some grub setting might have been deleted [possibly the one loading windows from the HDD partition] ? 
Another option would be to check your Master Boot Record.
anyway good luck :)

---

### Post by lukster91 on 2010-06-23
How do I reinstall the grub?

And what's this master boot record? 

Thanks :)

---

### Post by vel. on 2010-06-23
> **lukster91 said:**
> How do I reinstall the grub?

And what's this master boot record? 

Thanks :)

to reinstall grub try:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
and MBR info:
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by lukster91 on 2010-06-23
Couldn't I just update the grub?

---

### Post by Praveen30 on 2010-06-23
> **lukster91 said:**
> Hey all,

My Acer Aspire 5920 is dual booted with Windows 7 and Ubuntu 10.04 64-bit. 

A while ago Windows 7 just stopped booting after the boot selection options. I'd select Windows 7, and there would be a "_" in the top left hand corner, and it would just remain there. 
After a while if I hit any keys it would just bleep. 

Windows 7 is intact, I can access the files through Ubuntu etc - the problem is between selecting Windows 7 and then that connecting to load Windows 7 (At least I'm quite sure it is). Short of reinstalling Windows 7 (which as I am sure you all know is a painful process of redirecting calls, and people telling you for 5 minutes that formatting will delete your files.), I'm not sure what to do. I've tried reinstalling Ubuntu in the hope that would reinstall the Operating System selection process. No such luck.

Any ideas?

Thanks.

GRUB is the first software which loads when you start the computer.Grub is responsible for  showing that black screen from where you choose which kernel you have to install,at the top, version of the grub is given.there are different situation where you have to reinstall the grub,i also faced one of the situation which i have written in myblog(link is below).for reinstallation of grub you can watch this---

[http://http://www.youtube.com/watch?v=WtBBl6HvdpM]("http://http://www.youtube.com/watch?v=WtBBl6HvdpM")

---

### Post by yetiman64 on 2010-06-23
Hi lukster91,
Firstly the first link in post #4 is from 2006 and is for grub legacy. Lucid uses grub2 so don't use those instructions.

For a better view of your situation click on link #1 in my sig and follow the guide for the boot_info_script, and post back here in code tags.

---

### Post by oldfred on 2010-06-23
It may be more a windows issue than a grub issue.

Sometime this works, if windows is ok:
sudo update-grub

If not to see your entire boot configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by bodycoach2 on 2010-06-23
Had the same problem on another Acer laptop. Reinstalling Windows or Ubuntu resulted in the same blinking "_". I opened the case, took out the memory and hard drive, put them back and and made sure everything was 'seated' well. Computer booted up fine.

Seems to be a problem with other Acer laptops too. Do a search on your model, and see if others are experiencing the same problem, but with Windows7 only installed.

---

