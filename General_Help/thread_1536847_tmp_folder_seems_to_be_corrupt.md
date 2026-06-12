---
title: "tmp folder seems to be corrupt"
date: 2010-07-22
forum: General Help
---

### Post by alanmoreira on 2010-07-22
I have a machine running Windows Vista and Ubuntu 10.4.

I mostly use linux. But recently the linux start suddenly booting for no apparent reason.

Some have suggested that my tmp folder might be corrupt since I had to hard boot the computer a couple of times. 

If I ls -l my tmp folder that what I get:

total 3740
-rw------- 1 alan alan 1517243 2010-07-22 16:17 FlashmxX6Vm
-rw------- 1 alan alan 2233985 2010-07-22 16:13 Flashs7a9Gg
drwxr-xr-x 2 alan alan    4096 2010-07-22 16:44 hsperfdata_alan
drwx------ 2 alan alan    4096 2010-07-22 16:42 kde-alan
drwx------ 2 alan alan    4096 2010-07-22 16:18 keyring-tphguN
drwx------ 2 alan alan    4096 2010-07-22 16:42 ksocket-alan
drwx------ 4 alan alan    4096 2010-07-22 15:37 lyx_tmpdir.MT2017
drwx------ 3 alan alan    4096 2010-07-22 16:44 lyx_tmpdir.MT5514
drwx------ 2 alan alan    4096 2010-07-22 16:46 orbit-alan
drwx------ 2 gdm  gdm     4096 2010-07-22 16:18 orbit-gdm
drwx------ 2 root root    4096 2010-07-22 16:17 orbit-root
drwx------ 2 alan alan    4096 2010-07-22 16:00 plugtmp
drwx------ 2 alan alan    4096 2010-07-22 16:23 plugtmp-1
drwx------ 2 alan alan    4096 2010-07-22 16:18 pulse-Br7c6D0F9Zds
drwx------ 2 gdm  gdm     4096 2010-07-22 16:18 pulse-PKdhtXMmr18n
drwx------ 2 alan alan    4096 2010-07-22 16:18 seahorse-imBcSD
drwx------ 2 alan alan    4096 2010-07-22 16:18 virtual-alan.mIAOE2
drwx------ 2 alan alan    4096 2010-07-21 20:14 virtual-alan.NqX1sG


Seems that the Flash application is completely taking over it. What makes sense since the CPU starts running full capacity after a couple of hours running Pandora.

Is there any problem with my tmp folder? Is it possible that this is connected with the sudden reboots?

What can I do to fix it?

Thank you very much

---

### Post by dcstar on 2010-07-23
> **alanmoreira said:**
> I have a machine running Windows Vista and Ubuntu 10.4.

I mostly use linux. But recently the linux start suddenly booting for no apparent reason.
.........
Is there any problem with my tmp folder? Is it possible that this is connected with the sudden reboots?

What can I do to fix it?

Thank you very much
The /tmp folder it totally regenerated at every reboot, there is nothing to fix.

If your PC reboots after a time then look for things like bad memory or overheating.

---

### Post by alanmoreira on 2010-07-24
David:

thanks for your answer. But for some reason,the tmp regeneration doesn't seem to be happening in my case.

These Flash folders are huge even if I just restarted the computer.

I read in some thread that if you hard re-boot you can get a screwed up tmp folder.

I know that I re-boot quite a bit because once a week my notebook does not come back form the stand by mode...so the hard re boot is the only option..

So can you tell from looking at my tmp ls-l if it does look corrupt?

Thanks a lot

Alan

---

### Post by alanmoreira on 2010-07-27
David:

For example, looking at this ls-l report

total 120
drwxr-xr-x   2 root root  4096 2010-05-25 12:38 bin
drwxr-xr-x   3 root root  4096 2010-07-27 08:14 boot
lrwxrwxrwx   1 root root    11 2009-10-24 13:46 cdrom -> media/cdrom
drwxr-xr-x  18 root root  4060 2010-07-27 08:15 dev
drwxr-xr-x 160 root root 12288 2010-07-27 09:37 etc
drwxr-xr-x   3 root root  4096 2009-10-24 13:54 home
lrwxrwxrwx   1 root root    33 2010-07-27 08:14 initrd.img -> boot/initrd.img-2.6.32-24-generic
lrwxrwxrwx   1 root root    33 2010-07-01 08:22 initrd.img.old -> boot/initrd.img-2.6.32-23-generic
drwxr-xr-x  16 root root 16384 2010-07-16 08:02 lib
drwxr-xr-x   7 root root 16384 2010-07-21 07:52 lib32
lrwxrwxrwx   1 root root     4 2009-10-24 13:46 lib64 -> /lib
drwx------   2 root root 16384 2009-10-24 13:45 lost+found
drwxr-xr-x   6 root root  4096 2010-07-27 08:32 media
drwxr-xr-x   2 root root  4096 2009-04-13 04:33 mnt
drwxr-xr-x   3 root root  4096 2010-04-26 21:28 opt
dr-xr-xr-x 173 root root     0 2010-07-27 03:15 proc
drwx------  19 root root  4096 2010-06-08 08:32 root
drwxr-xr-x   2 root root  4096 2010-07-23 08:49 sbin
drwxr-xr-x   2 root root  4096 2009-03-06 11:16 selinux
drwxr-xr-x   2 root root  4096 2009-04-20 08:59 srv
drwxr-xr-x  13 root root     0 2010-07-27 03:15 sys
[COLOR=Red]drwxrwxrwt  20 root root 12288 2010-07-27 10:04 tmp[/COLOR]
drwxr-xr-x  11 root root  4096 2009-11-05 18:42 usr
drwxr-xr-x  16 root root  4096 2010-05-25 10:19 var
lrwxrwxrwx   1 root root    30 2010-07-27 08:14 vmlinuz -> boot/vmlinuz-2.6.32-24-generic
lrwxrwxrwx   1 root root    30 2010-07-01 08:22 vmlinuz.old -> boot/vmlinuz-2.6.32-23-generic


We can see that the tmp folder is huge, and I just restarted my computer! No applications running yet.


Thank you very much

Alan

---

### Post by WorMzy on 2010-07-27
What makes you think that it's huge from that? That number (12288 ) is the inode value. Run
```
du /tmp
``` to find out how much disk space (approximately) is being used.

---

### Post by alanmoreira on 2010-07-27
Thanks.

Thank is what I got:

du: cannot read directory `/tmp/pulse-PKdhtXMmr18n': Permission denied
4    /tmp/pulse-PKdhtXMmr18n
4    /tmp/keyring-ubgsRL
4    /tmp/.exchange-alan
4    /tmp/.ICE-unix
du: cannot read directory `/tmp/.esd-105': Permission denied
4    /tmp/.esd-105
8    /tmp/orbit-alan
4    /tmp/.esd-1000
4    /tmp/seahorse-0RFLHG
4    /tmp/aptdaemon-36mq0p
4    /tmp/plugtmp
68    /tmp/hsperfdata_alan
4    /tmp/virtual-alan.fk16DY
4    /tmp/kde-alan
4    /tmp/.X11-unix
8    /tmp/pulse-n1Crus6gxhEs
du: cannot read directory `/tmp/orbit-gdm': Permission denied
4    /tmp/orbit-gdm
4    /tmp/lyx_tmpdir.MT2146/lyx_tmpbuf2
4    /tmp/lyx_tmpdir.MT2146/lyx_tmpbuf0
4    /tmp/lyx_tmpdir.MT2146/lyx_tmpbuf1
16    /tmp/lyx_tmpdir.MT2146
4    /tmp/ksocket-alan
292    /tmp


Alan

---

### Post by Deiz on 2010-07-27
That's tiny, typical of a fresh boot. You might also try du -sh (summarizes, and prints human-readable output) in future.

That's barely a quarter megabyte. To contrast, after a month of uptime and numerous large builds in /tmp, mine is bordering on 2 GB. You have nothing to worry about.

---

### Post by alanmoreira on 2010-07-27
Thanks man:

So I need to look for problems elsewhere.

My computer became extremely unstable  a few weeks back. It reboots without any warning and really fast.

I don't know why , so I was exploring this option.

But thanks a lot, at least now I know that I tmp folder is not my problem

Best

Alan

---

