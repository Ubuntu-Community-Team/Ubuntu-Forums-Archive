---
title: "formatting entire hard disk"
date: 2010-11-26
forum: General Help
---

### Post by steveredshaw on 2010-11-26
;)

I am definitely non-techy, non-geeky, a GUI guy really, but learning steadily - I have been using Linux for a while now, have just moved on to Ubuntu and find it really great to use - I now feel confident enough to have just Ubuntu Linux on my Sony Vaio laptop (at the moment I have dual boot with Windows XP)

however there are just  a few Windows programs that I need to use that will not run under Wine

so I would value comments/advice on my 'grand plan'

1) re-format the Windows partition so that Ubuntu can use the entire hard disk (I don't know the best way to acheive this - is it to reinstall Ubuntu using all available disk space? or is it better to just format over the Windows partition and treat it as a second hard disk?)

2) install VirtualBox and use a version of Windows as a guest OS so I can use those Windows programs when I need to -  I understand this is easier than having to reboot the computer to get access to Windows

thanks for the help...

---

### Post by aeronutt on 2010-11-26
That's what I do, and am very happy with it. There are some limitations in virtualbox. You'll need the 'non-free' version to get to a USB port. But the non-free version has other options that make it much more user friendly IMO. (get the non-free version from virtualbox.org.) And, I'm not sure you can write CD's/DVD's from virtualbox, but someone else might know better. I think I read that somewhere in the VB gui just a few days ago.

---

### Post by deserthowler on 2010-11-26
> **steveredshaw said:**
> ;)

1) re-format the Windows partition so that Ubuntu can use the entire hard disk (I don't know the best way to acheive this - is it to reinstall Ubuntu using all available disk space? or is it better to just format over the Windows partition and treat it as a second hard disk?)

That worked for me when I did it.  I use the extra drive as a backup for data if I decide to reinstall Ubuntu or install a different OS.  It was also nice when I bricked my Ubuntu install and needed to salvage my files with a live CD.

> **steveredshaw said:**
> ;)
2) install VirtualBox and use a version of Windows as a guest OS so I can use those Windows programs when I need to -  I understand this is easier than having to reboot the computer to get access to Windows

thanks for the help...

For me that was the best way to run Windows until I got free of it completely.

Earl

---

### Post by steveredshaw on 2010-11-28
Everything is going to plan, VirtualBox up and running, also installed GParted

just need to check before I reformat!

windows partition that I no longer need is on dev/sda1, Ubuntu is on dev/sda2

sda1 is marked as the boot disk

I intend to format sda1 as ext4 - as sda2 is

after I do this, will Ubuntu start up automatically when I turn my laptop on?

also when the 2 partitions are formatted the same (ext4) will I be able to change the sizes, ie make the Ubuntu (sda2) partition larger and reduce the other (sda1) so it can remain as a data backup area?

thanks for the advice...

---

