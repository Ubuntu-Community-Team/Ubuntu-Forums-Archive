---
title: "Grub loading, vista partition death"
date: 2009-12-31
forum: General Help
---

### Post by Tarkan640 on 2009-12-31
I had my desktop partitioned with ubuntu and vista. I probably made a mistake by doing this, but in the vista os, I deleted the ubuntu partition and along with some other partition that was part of ubuntu I beleive, and extended my Windows vista partition to fill it up, and there is also a Recovery partition that is part of windows that I haven't messed with, but now hard disk has just windows and the recovery taking up all space, and when I start my computer it still tries to load GRUB...!  except grub isn't there and says Error 22 and just stops. Before any of this, it would open an option menu for me to choose which os to run, now when i start my computer it stays at the grub loading... error 22. 
I have lots and lots of information on my vista partition, anyone know what I should do?

(I was trying to get my comp back to just vista)

---

### Post by Leppie on 2009-12-31
download a boot image like [Ultimate Boot CD]("http://www.ultimatebootcd.com/index.html"), or Hiren's Boot CD, etc., and restore the master boot record.

---

### Post by BigCityCat on 2009-12-31
Yeh when you do that your supposed to use the free program easybcd to re write the mbr (master boot record) before you log out of windows.

I'm guessing but you should try and download a copy of partition magic. Then use it to shrink your partition again. After that it's easier for the laymen to then install ubuntu again on the largest continuous space. Then it should reinstall grub. You can remove it again and resize your hard disk with windows again but this time use easybcd to re write the mbr. Easybcd is real easy. Just point in click. Takes like 2 seconds.

---

### Post by BigCityCat on 2009-12-31
> **Leppie said:**
> download a boot image like [Ultimate Boot CD]("http://www.ultimatebootcd.com/index.html"), or Hiren's Boot CD, etc., and restore the master boot record.

or you can do this. lol

didn't know that.

---

### Post by oldfred on 2009-12-31
Supposedly windows changed the MBR from XP and before, to Vista and Win7 with minor differences.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista Recovery Disc - Repairs boot only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently)

---

### Post by Tarkan640 on 2009-12-31
Well, here's the deal. I downloaded both UBCD and vista recovery. The ubcd asked for things I had no clue. I managed to find a restore for the master boot record, but then it was asking things like, restore type, file or sector. I didn't know at all, i clicked sector, and then it asked sector number (1-10) so thats when i decided to stop because I really did not know. The file option asked for a filename. That cd seemed like it would work I just dont know enough to use it, maybe you guys could tell me what to do with that. As for the vista recovery, I clicked startup repair "Automatically fix problems that are preventing Windows from starting" because it seemed to be the right one, it doesn't work, says that I need to remove newly added hardware and restart, (I haven't had any new hardware for a while) and I restarted, gave the same error. the other options on the Vista recovery are system restore ("to an earlier point in time") and complete pc restore ("from a backup") which I thought neither would fix the problem. What do you guys think I should do now?

(thanks for the help so far)

---

### Post by Leppie on 2009-12-31
if you still have an ubuntu livecd, boot with it.
install ms-sys:
```
$sudo apt-get install ms-sys
```
restore the mbr:
```
$sudo ms-sys -m /dev/sda
```

---

### Post by drs305 on 2009-12-31
If you are running an Ubuntu LiveCD, you can dowload *lilo*, and use it to restore the Windows MBR.

```

sudo apt-get install lilo # Don't worry about the generated messages
lilo -M /dev/sd[COLOR="Red"]X[/COLOR] mbr  # sd[COLOR="Red"]a[/COLOR], sd[COLOR="Red"]b[/COLOR], etc

```

---

### Post by Tarkan640 on 2009-12-31
it says it couldn't find package ms-sys

---

### Post by Leppie on 2009-12-31
> **Tarkan640 said:**
> it says it couldn't find package ms-sys

hmm... looks like they removed it... try the lilo option.

---

### Post by drs305 on 2009-12-31
Yes, *ms-sys* was replaced. Now it's *mbr*, but meierfra says *lilo* is more consistent, and I don't doubt him.

---

### Post by Tarkan640 on 2009-12-31
um, this probably does not help, but the comp that has this problem does not have wired internet, it has wireless internet. So with the ubuntu livecd, there is not internet. Last time I used ubuntu it took about a week to set up wireless internet on there and I dont' have a cable to connect it directly. IF these commands don't require internet, they are still giving me errors. The lilo thing says "failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/lilo/lolo_22.8-7ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/lilo/lolo_22.8-7ubuntu1_i386.deb) Could not resolve 'archive.ubuntu.com'"

---

### Post by oldfred on 2009-12-31
Another choice that I had saved:

You will need to boot with your Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it didn't do any good for me. Then I selected the command prompt (console) and typed in the following commands: 
BootRec.exe /fixmbr 
BootRec.exe /FixBoot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

---

### Post by Tarkan640 on 2009-12-31
> **oldfred said:**
> Then I selected the command prompt (console) and typed in the following commands: 
BootRec.exe /fixmbr 
BootRec.exe /FixBoot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

and this worked?

---

### Post by Tarkan640 on 2009-12-31
Thank you thank you everyone for all the help! Oldfred, your commands worked on my computer, and now it starts up with windows just fine. Thank you very much, and everyone else too. 

:) Don't worry, I still use Ubuntu, just not on that comp

---

