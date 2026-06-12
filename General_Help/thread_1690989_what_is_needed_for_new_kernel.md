---
title: "what is needed for new kernel?"
date: 2011-02-19
forum: General Help
---

### Post by garyed on 2011-02-19
I'm trying to find out what files are needed to boot into another kernel.
I know there's vmlinuz* & initrd* but what else is need?
Is is possible to just copy some files to a partition with an already running Ubuntu version, set up grub & boot a different kernel?
I've seen some documentation on building a new kernel but I was wondering since I already have a good running kernel on a different hard drive if I could just move it & test it on another drive without having to build it.

---

### Post by tredegar on 2011-02-19
Take a look in **/boot**
Looks like 6 files are needed
You might also want the relevant kernel headers from **/usr/src**

---

### Post by garyed on 2011-02-19
> **tredegar said:**
> Take a look in **/boot**
Looks like 6 files are needed
You might also want the relevant kernel headers from **/usr/src**

I tried adding all those files too but it still didn't work.
I just get a black screen with no errors after selecting it in grub.
When I didn't have the partition set right in grub I got an error about not finding the kernel. After fixing that I just get a black screen.

---

### Post by tredegar on 2011-02-19
From your first post:> since I already have a good running kernel on a different hard drive if I could just move it & test it on another drive
A different *drive* or a different *PC* or a different *version of linux?*

> I tried adding all those files too but it still didn't work.
You will notice that the files in **/boot** all have a kernel version number as part of their name. These all need to match up. Each version needs the full 6 files as a bare minimum.

Please try not to be economical with the information you provide

I have not had any trouble installing and booting some custom-built kernels I have needed for new sony hardware (not this PC though).

Perhaps post the output of **ls /boot**, and we can take a look. 

My  **/boot** dir looks like this:```
tred@vaio2:~$ ls /boot
abi-2.6.32-21-generic     config-2.6.32-26-generic      memtest86+.bin                vmcoreinfo-2.6.32-25-generic
abi-2.6.32-22-generic     config-2.6.32-27-generic      System.map-2.6.32-21-generic  vmcoreinfo-2.6.32-26-generic
abi-2.6.32-23-generic     config-2.6.32-28-generic      System.map-2.6.32-22-generic  vmcoreinfo-2.6.32-27-generic
abi-2.6.32-24-generic     grub                          System.map-2.6.32-23-generic  vmcoreinfo-2.6.32-28-generic
abi-2.6.32-25-generic     initrd.img-2.6.32-21-generic  System.map-2.6.32-24-generic  vmlinuz-2.6.32-21-generic
abi-2.6.32-26-generic     initrd.img-2.6.32-22-generic  System.map-2.6.32-25-generic  vmlinuz-2.6.32-22-generic
abi-2.6.32-27-generic     initrd.img-2.6.32-23-generic  System.map-2.6.32-26-generic  vmlinuz-2.6.32-23-generic
abi-2.6.32-28-generic     initrd.img-2.6.32-24-generic  System.map-2.6.32-27-generic  vmlinuz-2.6.32-24-generic
config-2.6.32-21-generic  initrd.img-2.6.32-25-generic  System.map-2.6.32-28-generic  vmlinuz-2.6.32-25-generic
config-2.6.32-22-generic  initrd.img-2.6.32-26-generic  vmcoreinfo-2.6.32-21-generic  vmlinuz-2.6.32-26-generic
config-2.6.32-23-generic  initrd.img-2.6.32-27-generic  vmcoreinfo-2.6.32-22-generic  vmlinuz-2.6.32-27-generic
config-2.6.32-24-generic  initrd.img-2.6.32-28-generic  vmcoreinfo-2.6.32-23-generic  vmlinuz-2.6.32-28-generic
config-2.6.32-25-generic  lost+found                    vmcoreinfo-2.6.32-24-generic
tred@vaio2:~$ 

```

It would be helpful if you told us which kernel boots, and which does not.

---

### Post by garyed on 2011-02-19
> **tredegar said:**
> From your first post:
A different *drive* or a different *PC* or a different *version of linux?*



A different drive on the same PC. 
I have 4 HD's on one PC.
1 - IDE - Windows NTFS  all one partition
2 - SATA  Windows Fat32 all one partition (data only)
3 - IDE   Ubuntu-Gusty , Ubuntu Studio Lucid 
4 - SATA  Ubuntu Lucid , Puppy Sudio
I've got 5 booting OS's all working fine except for Ubuntu Studio Lucid.
That partition actually works O.K. but I get an error at boot up: see thread

[http://ubuntuforums.org/showthread.php?t=1687313](http://ubuntuforums.org/showthread.php?t=1687313)

After booting it works fine too.
So my plan was to try a kernel that I know boots without any issues & see what it does on my problem booting partition (Ubuntu Studio Lucid).

Here is the /boot directory from Ubuntu Studio Lucid partition:
```

me@ustudio:~$ ls -l /boot
total 44304
-rw-r--r-- 1 root root  640617 2011-02-19 09:55 abi-2.6.32-21-generic
-rw-r--r-- 1 root root  635427 2010-04-16 08:34 abi-2.6.32-21-preempt
-rw-r--r-- 1 root root  646642 2011-01-10 19:57 abi-2.6.32-28-preempt
-rw-r--r-- 1 root root  115847 2011-02-19 09:55 config-2.6.32-21-generic
-rw-r--r-- 1 root root  110424 2010-04-16 08:34 config-2.6.32-21-preempt
-rw-r--r-- 1 root root  110649 2011-01-10 19:57 config-2.6.32-28-preempt
drwxr-xr-x 3 root root    4096 2011-02-19 13:58 grub
-rw-r--r-- 1 root root 7954692 2011-02-19 09:55 initrd.img-2.6.32-21-generic
-rw-r--r-- 1 root root 8333093 2011-01-04 18:03 initrd.img-2.6.32-21-preempt
-rw-r--r-- 1 root root 8346744 2011-02-02 22:45 initrd.img-2.6.32-28-preempt
-rw-r--r-- 1 root root  160280 2010-03-23 05:40 memtest86+.bin
-rw-r--r-- 1 root root 1687378 2011-02-19 09:55 System.map-2.6.32-21-generic
-rw-r--r-- 1 root root 2168040 2010-04-16 08:34 System.map-2.6.32-21-preempt
-rw-r--r-- 1 root root 2172457 2011-01-10 19:57 System.map-2.6.32-28-preempt
-rw-r--r-- 1 root root    1196 2011-02-19 09:55 vmcoreinfo-2.6.32-21-generic
-rw-r--r-- 1 root root    1336 2010-04-16 08:37 vmcoreinfo-2.6.32-21-preempt
-rw-r--r-- 1 root root    1336 2011-01-10 19:59 vmcoreinfo-2.6.32-28-preempt
-rw-r--r-- 1 root root 4029792 2011-02-19 09:55 vmlinuz-2.6.32-21-generic
-rw-r--r-- 1 root root 4093760 2010-04-16 08:34 vmlinuz-2.6.32-21-preempt
-rw-r--r-- 1 root root 4109056 2011-01-10 19:57 vmlinuz-2.6.32-28-preempt
me@ustudio:~$ 

```

The *-generic is the kernel I'm trying to import.
The *-preempt ones work.

---

### Post by tredegar on 2011-02-20
Perhaps you should open /boot/grub/grub.cfg and take a close look at the menuentry grub has made for the kernel you cannot boot. Maybe grub has made some mistake.

---

### Post by garyed on 2011-02-20
> **tredegar said:**
> Perhaps you should open /boot/grub/grub.cfg and take a close look at the menuentry grub has made for the kernel you cannot boot. Maybe grub has made some mistake.


Everything looks right in grub.cfg as far as I can tell.
I don't use the os_prober. I use a custom menu for all my entries but I've checked & can't find anything wrong there.

After looking at the size of the kernel download site its more than 60mb so there must be a lot more files involved than we think.

---

### Post by CHRSB on 2011-02-20
[FONT=Arial]> **garyed said:**
> I'm trying to find out what files are needed to boot into another kernel.
I know there's vmlinuz* & initrd* but what else is need?
Is is possible to just copy some files to a partition with an already running Ubuntu version, set up grub & boot a different kernel?
I've seen some documentation on building a new kernel but I was wondering since I already have a good running kernel on a different hard drive if I could just move it & test it on another drive without having to build it.

More information would help (kernel version? same of different hardware? Both Ubuntu?), but I am afraid just coping the kernel and files will not work.

It would be quicker to build a new kernel than to figure it out in my opinion.
[/FONT]

---

