---
title: "avoid &quot;run fsck Manually&quot;"
date: 2011-02-28
forum: General Help
---

### Post by mpgarcia on 2011-02-28
Hello people!!

I`ve got a proble with fsck in ubuntu, so it will very useful for me if you can help me.
I have ubuntu  which when the pc suddenly shuts down and reboots again, shows an error that makes me check file system manually. It writes:

"UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY 
(i.e. , without -a or -p options) 
fdisk died with exit 4 (...)
* An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted....
*The root filesystem  is currently mounted in read-only mode. 
A maintenance shell will be nor started.
After  performing  system maintenance,  press CONTROL-D to terminate  the maintenance 
shell to restart the system." 

What I need is to avoid users interaction. Do you know if it is possible to start file system check without user´s approval? I mean,  don´t need the user to write fsck and hit control+d.

Thank you very much for your help!!

---

### Post by gradinaruvasile on 2011-02-28
This happens when fsck detects some big issues (it is run automatically BTW). So it is not just "run fsck".
You have to remount read only the root file system, fsck it (sometimes you have to force it with the -f flag) then reboot the system.

---

### Post by Sef on 2011-02-28
> "UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY 

1) Back up your data if you have not already. Your system may not boot into Ubuntu in the future.

2) A problem exists, and it would be best to find the cause, so the correct solution can be applied.

---

### Post by mpgarcia on 2011-02-28
And is there any way to force it to do it automatically?

---

### Post by mcduck on 2011-02-28
> **mpgarcia said:**
> And is there any way to force it to do it automatically?

It *already* tried doing it automatically, decided that the problem is too serious and it can't automatically reliably complete the check, and therefore requested that you'd do it manually.

So no, you can't automate the check after automatic check has already failed. You should instead try to find out what's casing such errors on your disk. Check it's SMART status, for starters. And make sure you have backups of all your important files, the drive doesn't sound very healthy and might be failing...

---

### Post by mpgarcia on 2011-02-28
Does anyone know if it is possible to reboot the pc automatically when this problem ocurred instead of check the file system ?

---

### Post by runeh76 on 2011-02-28
Boot from the Ubuntu LiveCD and then open a terminal and type:
Code:
sudo fsck -pcfv /dev/sda
Where "sda" = the disk in question. 

This command will force automatic bad block checking and it will automatically mark all known bad sectors as bad so that they wont "interfere" in the future. After you boot back into the OS, I would make sure that smartmontools is installed:

Code:
sudo apt-get install smartmontools
You will need to make sure that "SMART' capability is enabled in your BIOS. After you get it installed, then you can run an extended offline test (this will run in the background while the computer is on and you wont even know it is running). To do that:

Code:
sudo smartctl --test=long /dev/sda
And then to see the overall health of the system, you can type:

Code:
sudo smartctl -a /dev/sda
Also, please read the manpages for these programs if you want a more detailed explanation:

Code:
man fsck
man smartmontools

---

### Post by dcstar on 2011-03-01
> **mpgarcia said:**
> 
.........
What I need is to avoid users interaction. Do you know if it is possible to start file system check without user´s approval? I mean,  don´t need the user to write fsck and hit control+d.


fsck may run automatically at startup, but it may not fix anything automatically unless:

```
gksudo gedit /etc/default/rcS
```
Make:
```
FSCKFIX=yes
```
and save the changes.

---

### Post by mpgarcia on 2011-03-01
I just have one little problem. When it gives the error, it mounts the system in read-only mode, so I am not able to modify the file rcS. Anyway, I will do the fsck manually, modify the paramenter [FONT=&quot]FSCKFIX=yes [/FONT]and redo the error to check if it doesn´t appear again. I´ll inform you.

---

