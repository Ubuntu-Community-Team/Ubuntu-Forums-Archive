---
title: "Multiple Ubuntu Entries in Grub"
date: 2011-03-23
forum: General Help
---

### Post by FinalShot on 2011-03-23
Over time Grub just has more and more Ubuntu entries, currently at 5 ( including start in recovery mode ).

Is it safe to just remove them from /boot/grub/grub.cfg? Or is there a better way ( I've ran sudo update-grub ), and how can I stop it from happening again.

---

### Post by sj1410 on 2011-03-23
when you upgrade you kernel, it actually installs a new kernel and the old one is still there. to remove the old kernels you can do a 


```

sudo apt-get autoremove

```

---

### Post by darolu on 2011-03-23
Do not modify /boot/grub/grub.cfg, grub 2 works a bit different.

First to delete extra entries, you'll need to remove those old kernels; the safest way to do this is with Synaptic so go to System - Administration - Synaptic; it will ask for your password, enter it. Then on the search box type: **linux-image-2.6** look for the installed ones and righ click them and mark the ones you don't use to be uninstalled, to check what kernel you are using open a terminal and type "uname -r" and hit enter, it will print the kernel version you are currently using, this is the one you want to leave intact; it is also advice to leave an old one (that you are sure it works), this is up to you.

Doing this should remove most entries; if you don't want/use the memtest and recovery options, you need to do two more things, for the memtest options open a terminal and go to /etc/grub.d/ and remove execution permissions to the **20_memtest86+** file:

```

youruser@yourcomputer:~$ cd /etc/grub.d/

youruser@yourcomputer:/etc/grub.d$ ls
00_header        10_linux      **20_memtest86+**  40_custom  README
05_debian_theme  20_linux_xen  30_os-prober   41_custom

youruser@yourcomputer:/etc/grub.d$ **sudo chmod a-x 20_memtest86+**

youruser@yourcomputer:/etc/grub.d$ ls -l
total 52
-rwxr-xr-x 1 root root 6831 2010-10-06 07:23 00_header
-rwxr-xr-x 1 root root 1516 2010-10-20 03:49 05_debian_theme
-rwxr-xr-x 1 root root 4757 2010-10-06 07:23 10_linux
-rwxr-xr-x 1 root root 5028 2010-10-06 07:23 20_linux_xen
**-rw-r--r-- 1 root root 1588 2010-09-24 12:14 20_memtest86+**
-rwxr-xr-x 1 root root 6933 2010-10-06 07:23 30_os-prober
-rwxr-xr-x 1 root root  214 2010-10-06 07:23 40_custom
-rwxr-xr-x 1 root root   95 2010-10-06 07:23 41_custom
-rw-r--r-- 1 root root  483 2010-10-06 07:23 README

```

And to remove the recovery entries, you need to edit the /etc/default/grub file:

```
youruser@yourcomputer:~$ gksu gedit /etc/default/grub
```

Look for the **#GRUB_DISABLE_LINUX_RECOVERY="true"** line and uncomment it by removing the #:

```
# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_LINUX_RECOVERY="true"
```

Save the file and close gedit. And now the final step, go back to your terminal and run:

```
youruser@yourcomputer:~$ sudo update-grub2
```

And that's it, you should have a clean Grub now.

P.S.
> **sj1410 said:**
> when you upgrade you kernel, it actually installs a new kernel and the old one is still there. to remove the old kernels you can do a 


```

sudo apt-get autoremove

```
That won't remove old kernels.

---

### Post by satish_j on 2011-03-23
You can also remove the old kernels from synaptic manager.
i.e if you have 2.6.28-28,2.6.28-29,2.6.28-30,
then you can remove all occurances 2.6.28-28 from synaptic,reboot and you will be shown the last 2 kernels at boot.
Overtime,if you think the latest kernel(2.6.28-30) is working fine,then you can also remove 2.6.28-29..
I always keep 2 kernels on my system.
It is usually considered safe to keep one extra kernel,usually the one that precedes the latest kernel,so as to tackle any kernel related issues.

---

### Post by satish_j on 2011-03-23
> **darolu said:**
> 
P.S.

That won't remove old kernels.

That's correct..autoremove basically removes the dependencies packages that are not required on system.

---

### Post by FinalShot on 2011-03-23
Thank darolu, worked perfectly. But I didn't want to remove Memtest ;)

---

### Post by darolu on 2011-03-23
> **FinalShot said:**
> Thank darolu, worked perfectly. But I didn't want to remove Memtest ;)

I'm glad it worked, if you want to save some space from your HD you can also remove the **linuxe-headers-2.6*** packages using synaptic, again, don't remove the kernel headers you use.

---

### Post by domu on 2011-03-23
I'm glad you got it sorted. I wrote a script which does it automatically - see '**remove-kernel**' under My Programs at [**http://www.timedicer.co.uk/**]("http://www.timedicer.co.uk/")

It allows you to view what kernels you have and then to delete  ones you don't need, it knows not to delete the kernel currently in use, it updates grub2, it deletes old headers. It leaves the memory testing entry and recovery mode entry in grub (why remove them?)

I use it a few days after each kernel update to clear out the old one.

---

### Post by darolu on 2011-03-24
> **domu said:**
> I'm glad you got it sorted. I wrote a script which does it automatically - see '**remove-kernel**' under My Programs at [**http://www.timedicer.co.uk/**]("http://www.timedicer.co.uk/")

It allows you to view what kernels you have and then to delete  ones you don't need, it knows not to delete the kernel currently in use, it updates grub2, it deletes old headers. It leaves the memory testing entry and **recovery mode** entry in grub (**why remove them?**)

I use it a few days after each kernel update to clear out the old one.

If you are a security "freak" (paranoid) like some of us are, doing this may be desirable as you log in as root when you choose this option, no questions (nor passwords) asked. Memtest options are useful and there is no particular reason to remove them other than "I don't use them... ever", "I like my grub super-clean" and of course (my favourite) "just because I can" :p

It's great you took the time to make that script, I'll definitely check it out :D

---

