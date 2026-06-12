---
title: "Removed Ubuntu, now have to fix Vista Bootloader through Ubuntu Live..."
date: 2010-04-22
forum: General Help
---

### Post by sab3156 on 2010-04-22
Hey, guys... I got excited while partitioning for installing Ubuntu Server 9.10... I ended up removing Ubuntu Desktop...

Before this, I had one partition for Vista, one for Vista Recovery that came with the comp, and 1 partition for Ubuntu...  After messing around during the install of Ubuntu Server (which I did not even complete... I abandoned it), I get the message:
[INDENT][INDENT]grub loading.  error: file not found

grub rescue> 

[/INDENT][/INDENT]I then booted Ubuntu live.  I see that I have two mountable partitions on my hard drive... 246gb and 20gb (the 20gb I made during the installation procedure of Ubuntu Server that I didn't complete)... So where is the Vista Recovery partition?

What can I do to boot into Vista and simply bring my system back to the way it was pre-Grub (Vista partition + Vista recovery partition)?  I then will partition and install Ubuntu Server.

---

### Post by carl4926 on 2010-04-22
We would need to see 
```
fdisk -l
```

get that by booting a Ub* live cd

You know about this do you:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by sab3156 on 2010-04-22
Thanks for your reply.

Here is my **fdisk -l **:


```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x877d3b07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29904   240200700    7  HPFS/NTFS
/dev/sda2           37205       38913    13720576    7  HPFS/NTFS
/dev/sda3           29905       37204    58637250    5  Extended
/dev/sda5           29905       32336    19535008+  83  Linux
/dev/sda6           36902       37204     2433816   82  Linux swap / Solaris

```Thanks, I do know about the recovery CDs, but I'm wondering what the procedure would be in absence of such discs.  How would I go about removing Grub and go back to the original Vista bootloader?

Also, does my output above indicate that I have not removed Ubuntu Desktop?

---

### Post by klemes on 2010-04-22
No worries ,all of your partitions seem still there including your Vista Recovery partition(it's the second listed in the fdisk output).
Now to get things straight if all you want is your Vista back then the only thing to do is 
use the Vista Recovery CD as clearly pointed out by the former user .
If you plan to reinstall Ubuntu anyway you do not have to take the above step ,you only have to proceed to make a complete Ubuntu installation which will take care the rest,meaning it will install grub with entries for booting Ubuntu as well entries for booting your Vista installation as well as your recovery partition.
And by all means make the installation from Ubuntu LiveCD unless you absolutely need the Server Edition.

---

### Post by sab3156 on 2010-04-22
The Vista recovery disc cannot detect a problem with start-up so it won't even do anything... So I really do now have to fix grub and boot into Vista with that.

So I think I will do a re-install of Ubuntu Desktop and take it from there.

And just out of curiosity, after this, what is the best procedure to go back into the original Vista bootloader settings?

---

### Post by klemes on 2010-04-22
Never mind if it does not detect a problem just go ahead and choose the option to repair booting into Vista.
And by the way that is the ONLY way I know and the simplest one.
There used to be a package ms-sys in the Ubuntu and Debian repos used to restore the Windows boot record but it was withdrawn from 8.04 and onwards due to copyright reasons,so you are stuck with the Recovery CD I am afraid.

---

### Post by john newbuntu on 2010-04-22
Follow the vista part from this guide:
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

type bootrec.exe /fixmbr

---

### Post by klemes on 2010-04-22
> **john newbuntu said:**
> Follow the vista part from this guide:
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

type bootrec.exe /fixmbr

Yes but this solution implies having a Vista CD available,which sab ,as most owners of preinstalled Vista systems ,apparently hasn't one.
And the recovery CD is not exactly bootleg it is derived from the original Vista CD and it's purpose is exactly to overcome the fact that most owners of preinstalled Vista(especially laptops) don't get a full Vista installation CD except only a recovery section in their HDD and in a few cases a Recovery CD iin most cases used only to reinstall the system, with the repair function of the original Vista CD being unavailable to them.Hope I have explained this right this time.

---

### Post by sab3156 on 2010-04-22
Excellent.

Everything is fine now after re-install of Ubuntu.  I do have a Vista Recovery CD, but I guess what I really wanted to do in the beginning was know how to delete Grub and go back to the Vista bootloader manually without a recovery process.

Thanks for your help.  :popcorn:

---

### Post by john newbuntu on 2010-04-22
@klemes: Isn't that where neosmart comes to help?

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by carl4926 on 2010-04-22
Good to know you managed it.
Just never panic in these situations. You seemed to do well.:)

---

