---
title: "Cannot boot into windows anymore. Windows partition became Unknown partition."
date: 2011-09-20
forum: General Help
---

### Post by pawan613 on 2011-09-20
Hi there.
I already have Windows XP(38GB) on my computer and then I installed Ubuntu 11.04.
Initially grub was working fine and was able to boot in both ubuntu and windows.
Then, in ubuntu terminal, I wanted to copy a file named "burg sources" from ubuntu drive to windows xp drive.
So, I executed a command:
cp burg/ sources /dev/sda1

and then it gave some weird output and after that my windows partition has became "Unknown Partition"
Now from grub when I try to boot into Windows XP, a loading cursor keeps on blinking and gets stuck there itself.
Please help me on this, I cant afford to loose any of my data.
I have no idea what went wrong :confused:

---

### Post by Rubi1200 on 2011-09-20
Hi and welcome to the forums :-)

Please post the results of the boot info script so we help you diagnose the problem and hopefully find a solution.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by patryk77 on 2011-09-20
> **pawan613 said:**
> Hi there.
Then, in ubuntu terminal, I wanted to copy a file named "burg sources" from ubuntu drive to windows xp drive.
So, I executed a command:
cp burg/ sources /dev/sda1

Did you run that as root?

You should generally never write to the /dev directory (except for writing garbage/useless output to /dev/null)

You need to first figure out where the file system is mounted (or mount it if it isn't), then copy a file to the mount point, not the device.

For instance, if I run 'df -h' I get:
```
Filesystem            Size  Used Avail Use% Mounted on
*snip*
/dev/sdb1             917G  310G  562G  36% /mnt/1tb

```

Then to copy a file I would use:
cp burg/sources /mnt/1tb/

Writing to (as root) /dev/sda1 is bound to overwrite important sectors on the disk...

---

### Post by AndyCinDallas on 2011-09-20
Boot up from your XP CD and do a [Repair install](http://pcsupport.about.com/od/operatingsystems/ss/instxprepair1.htm) of XP.

Once XP is up and running, you will have to reinstall Grub in order to boot into Linux as well, but that's pretty easy to do from a Ubuntu CD

---

### Post by pawan613 on 2011-09-21
Hello all,
Well I tried with repair process of windows xp, it shows the partition as "Unallocated Space" and I also tried with Bart PE, which showed that drive as "(Unrecognized)".
I had no option and no time to wait for my system to get ready, so I formatted my system.
Well thanks Rubi1200, patryk77 and AndyCinDailas for try.

---

### Post by Jouke74 on 2011-09-21
I can tell you what went wrong: 

cp burg/ sources /dev/sda1

Copies "burg/ sources" (strange directory with space btw) to probably your windows boot record + first other sectors of your /dev/sda1 partition. Depending on the size of the file(s) "sources" (boot record is 512 bytes) one or multiple system files and the partition table have been damaged. That's why it cannot read the file system, technically there is none anymore, because the index of the file system is gone. 

As said: this has to be run as root, so why did you run it as root?

The only way to get your data from windows back is to use a file recovery program. Dot not write anything to this disk anymore, but use testdisk / photorec or another to to recover your data. 

After that you will likely need to reinstall or fix Windows, but I doubt the fixing is going to work.

^Edit: just read you formatted your system... a hard lesson learned.

---

### Post by pawan613 on 2011-09-22
Hey Jouke74
What you telling, it do make sense.
But I'm very new to Terminal, had no idea that I should do it from root.
Yehh, indeed a lesson learned.
Now, keeping one separate partition for experiments. :D
Anyways Thanks!

---

### Post by Jose Catre-Vandis on 2011-09-22
The other thing worth trying is to boot up with a live cd with gparted on it. Run gparted. Review the partitions. Sometimes the windows partition can become "hidden". Uncheck the hidden flag and reboot...

---

