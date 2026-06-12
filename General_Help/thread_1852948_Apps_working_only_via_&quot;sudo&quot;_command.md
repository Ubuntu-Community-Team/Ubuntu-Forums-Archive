---
title: "Apps working only via &quot;sudo&quot; command"
date: 2011-10-01
forum: General Help
---

### Post by majortom67 on 2011-10-01
Hi to everybody. I'm an Apple Macbook Proi user but I'm going to post my question here as the problem seems non related to the platform. here it is: there is no way anymore to launch and work with applications in 'normal' mode. I have to enter Terminal and digiti "sudo 'applications's name'. In standard mode anything can happen: from preventing the app to start to getting any type of strange error thatlook that 1 or more folders do not have the correct percmissions. In Mac OS X I wuold run the 'Repair Permission' feature in Disk Utility but what caI do here in (K)Ubuntu?
TIA for any help
Simon

---

### Post by sanderd17 on 2011-10-01
can you give us the output of the following commands?

```

kate
$PATH #including the $ sign
ls -l /usr/bin/kate

```

---

### Post by WorMzy on 2011-10-01
You should never use "sudo" for graphical applications, only use it for CLI apps.

Instead, use gksu, gksudo, or kdesudo. If you don't have any of these (I don't know what Kubuntu comes with - I would guess kdesudo), then use sudo -i, and *then* run the application. All of these ensure that the correct env variables are set for the root user, which prevents the permissions problem you're experiencing now.

To fix it, run the following:

```
sudo chown -R $USER:$USER $HOME
```

You may get an error about a .gvfs folder, but that can be ignored.

---

### Post by majortom67 on 2011-10-01
Thanks.
"Kate" command make Kate app run.

"$PATH" in the same window: nothing.

"$PATH" in new window:
simon@Kubuntu-MBPro:~$ $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: File o directory non esistente
simon@Kubuntu-MBPro:~$

"ls -l /usr/bin/kate" (new window):
simon@Kubuntu-MBPro:~$ ls -l /usr/bin/kate
-rwxr-xr-x 1 root root 5492 2011-09-15 23:56 /usr/bin/kate

By the way... I'm user 1000.
simon@Kubuntu-MBPro:~$ 

Thanks again.
Simon

---

### Post by majortom67 on 2011-10-01
Thanks very much. I believe this come from the fact that I'm unable to access to partitions I have personally created the using "sudo dolphin" instead of just running Dolphin.
Thanks again
PS: installed gksu since long time.

---

### Post by sanderd17 on 2011-10-01
> **majortom67 said:**
> Thanks.
"Kate" command make Kate app run.

then run dolphin, or any app that gives you an error. I thought all apps gave you errors, so I just picked kate
> 

"$PATH" in the same window: nothing.

"$PATH" in new window:
simon@Kubuntu-MBPro:~$ $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: File o directory non esistente
simon@Kubuntu-MBPro:~$

the path seems ok to me
> 

"ls -l /usr/bin/kate" (new window):
simon@Kubuntu-MBPro:~$ ls -l /usr/bin/kate
-rwxr-xr-x 1 root root 5492 2011-09-15 23:56 /usr/bin/kate


If kate works, this is normal. Try again with a program that gives an error.

---

### Post by WorMzy on 2011-10-01
You can create partitions in Dolphin? Or do you mean folders?

Any folders you make using Dolphin as the root user will be owned by root:root with the permissions "755" (drwxr-xr-x), so you should be able to access them, but you won't be able to create files inside them without being the root user. This is normal.

You can change the ownership of these directories and their contents to *your* user, but you should never do this for "system" directories. (e.g. /bin, /sbin, /usr, /lib, /etc, /var, /boot, etc), as doing so can cause your system to stop working. So be careful about what you change the ownership of.

---

### Post by majortom67 on 2011-10-01
Thank you everybody.
Sanderd17: I can't replicate the problem as I run WormZy's command.

Yes I did a root command but I can't remember what for. Maybe because I alway have problems writing to partitions I personally created regardless the app used to.

Simon

---

### Post by WorMzy on 2011-10-01
Well, NTFS and FAT (Windows) partitions don't support UNIX file permissions, so you will have problems with permissions if you mount these partitions as root using the mount command. If you use udisks, though, you should be fine.

Linux partitions (e.g. ext4, xfs, jfs) which *do* support UNIX file permissions will be owned by root by default. You can change this by mounting the partitions, then running the chown command on their mount point. Again, be careful with this. If the other partition holds another operating system's files, changing their ownership may cause the operating system in question to stop working.

I don't know what filesystem Apple uses on their macs, but since OSX rips off UNIX, I'd expect the filesystem to support UNIX file permissions. If they use a closed-source propriety filesystem, you may have a similar problem to that of Windows (NTFS/FAT) partitions.

---

