---
title: "Need to reconfigure GRUB2"
date: 2010-09-11
forum: General Help
---

### Post by arashiko28 on 2010-09-11
I connected a HDD to my laptop using an external case and installed Ubuntu 10.04, but then now my laptop won't boot without the drive connected, how do I recover my GRUB configuration?

I already tried grub update, and restarted and got an error message, had to connect the HDD again to boot.

Please help!

---

### Post by drs305 on 2010-09-11
Boot to your Ubuntu Desktop (not a LiveCD). If you need the external connected to boot, that's OK. 

You should be able to create the grub files and write to the Ubuntu drive's (**X**) MBR with the following (**X** is the drive letter, normally "a" if you have only one drive):

```
sudo grub-install /dev/sd**X**
```

Do not specify a partition - the command will write the grub files to /boot/grub and write GRUB to the MBR of whatever drive your Ubuntu system is currently running on.


Added:
After you complete the process, if you want to check before you reboot, you can run *meierfra's* [boot info script]("http://bootinfoscript.sourceforge.net"). The top lines should say that Grub 2 is installed on your Ubuntu drive and looks at the Ubuntu partition for the Grub files. If your Ubuntu install is on sda1, it would look like this:
> 
Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.


If things don't turn out as you suspect, post the contents of the RESULTS.txt and we can take a look. Copy them between "code" tags, which you can generate by clicking the # icon in the post's menu.

---

### Post by arashiko28 on 2010-09-11
I'll try it now, I followed the instructions to do it from live CD and got the same error. By the way, all the effort was in vain, now the other computer won't boot at all, but one at the time :?

---

### Post by drs305 on 2010-09-11
> **arashiko28 said:**
> I'll try it now, I followed the instructions to do it from live CD and got the same error. By the way, all the effort was in vain, now the other computer won't boot at all, but one at the time :?

The instructions were for accomplishing the task from a normally running Ubuntu (not a LiveCD). Using a LiveCD requires a different procedure. 

When you get back let us know your computer's status, what environment you want to install from, and we can do the install for that specific situation.

Or if you want to install from the LiveCD, these instructions from the Ubuntu community doc should work:
[Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by arashiko28 on 2010-09-11
Thanks, it actually worked, but due an electricity failure, I was unable to connect as soon as I fixed it.

---

### Post by drs305 on 2010-09-11
> **arashiko28 said:**
> Thanks, it actually worked, but due an electricity failure, I was unable to connect as soon as I fixed it.

I'm glad you fixed it. The longer it took for your response the more concerned I became. :shock:

---

### Post by arashiko28 on 2010-09-11
Well, at least for my laptop it all went well, thanks again!

---

