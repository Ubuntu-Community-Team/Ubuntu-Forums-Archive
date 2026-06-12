---
title: "Is my hard drive bust"
date: 2011-06-06
forum: General Help
---

### Post by ianc1 on 2011-06-06
I recently wiped Windows for a Linux only machine and noted that my boot times were slower than they were on the dual boot machine.  Today I decided to look at /var/log/boot.log and the first few lines are as follows:
```
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/sda5: clean, 165284/915712 files, 943501/3662080 blocks
/dev/sda1: clean, 229/427680 files, 18961/854492 blocks
init: ureadahead-other main process (860) terminated with status 4
/dev/sda7: clean, 1097/18169856 files, 1287119/72648960 blocks
init: ureadahead-other main process (865) terminated with status 4
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
```I assume these exit status comments are not normal.  For info I'm running 11.04 and sda1 is /boot sda5 is / and sda7 /home.

Do I have anything to worry about?

Thanks

---

### Post by matt_symes on 2011-06-06
Hi
[FONT=monospace]
[/FONT]> init: ureadahead-other main process (860) terminated with status 4That is normal and is not an issue according to the developer of ureadhead.

> 
ureadahead exits with status 4!
 This isn&#8217;t actually a bug
 Status 4 (usually ureadahead-other exits with this) means that you  had a mountpoint in your fstab that didn&#8217;t have any files on it needed  during boot. Probably that drive with all those MP3s and movie files on  it.
 It still reads everything needed during boot, the status is just there for me to debug other issues.
 The real bug here is that Upstart spams the console with that  message,even though the ureadahead-other.conf file has &#8220;normal exit 4&#8243;  in it!
from here (it was originally posted on these forums by the developer but i cant find the post)

[http://ubuntuguide.net/howto-fix-ureadahead-problem-after-upgrading-to-ubuntu-10-04](http://ubuntuguide.net/howto-fix-ureadahead-problem-after-upgrading-to-ubuntu-10-04)

You can get rid of the status 4 message if you want to.

Kind regards

---

### Post by crispy_420 on 2011-06-07
Did you maybe delete your swap space? Just throwing that out there.

---

### Post by ianc1 on 2011-06-07
Thanks all, and thanks for the links - very informative, although I am still confused.

My machine is definitely slower by ca 10 s to boot than maybe 2 weeks ago.  I have not removed SWAP its still there as /dev/sda6 but appears to not be showing in the boot log.

What puzzles me about exit code 4 of ureadhead is the quote "Status 4 (usually ureadahead-other exits with this) means that you had a mountpoint in your fstab that didn’t have any files on it needed during boot".  I would have thought that both the boot and root partitions (/dev/sda1 and /dev/sda5 in my case) were needed during boot.

Is it possible that fsck is the cause of the slower booting as I understand this to be a check of the file system?

Thanks again.

---

### Post by matt_symes on 2011-06-08
> **ianc1 said:**
> Thanks all, and thanks for the links - very informative, although I am still confused.

No problem. I think it was posted early 2010 IIRC.

> 
My machine is definitely slower by ca 10 s to boot than maybe 2 weeks ago.  I have not removed SWAP its still there as /dev/sda6 but appears to not be showing in the boot log.Open a terminal and type

```
swapon -s
```This will tell you about your swap.

> 
What puzzles me about exit code 4 of ureadhead is the quote "Status 4 (usually ureadahead-other exits with this) means that you had a mountpoint in your fstab that didn&#8217;t have any files on it needed during boot".  I would have thought that both the boot and root partitions (/dev/sda1 and /dev/sda5 in my case) were needed during boot.As far as iu understand it, the root / partition is the main one profiled by ureadahead.  This is your sda5 partition where you get status 0 from ureadahead. sda1 and sda7 will also checked but they will return status 4 as they are not the root parition.

> 
Is it possible that fsck is the cause of the slower booting as I understand this to be a check of the file system?
Thanks again.It is possible but it would have to perform an fsck check on every boot to be continually that slow. We can check this. Open a terminal and type

```
cat /etc/fstab
```Post the results back here. If that shows nothng you can look at tune2fs.

```
sudo dumpe2fs /dev/sda5 | grep -Ei "check interval|mount count"
```Enter your password. It will not be echoed to the screen.
Post that back as well.

Ureadahead my also be profiling on every boot and that would be slow but, like fsck, it should not be happening on every boot. It should only happen on chages to the directory /etc/init* or a couple of other situations.

Kind regards

---

### Post by ianc1 on 2011-06-08
Thanks again Matt.

The outputs of these tests are as follows:

swapon -s :```
Filename                Type        Size    Used    Priority
/dev/sda6                               partition    3905532    0    -1
```I guess this confirms my swap partition is still there and in  use, although none used at present.

cat /etc/sftab (I assumed this to be fstab as I have no ftab file?) :```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=df8cbaf2-e780-4d28-bfb3-248949539b50 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=161b6bd6-c88b-4cf0-9260-fbf80ee7fc12 /boot           ext2    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=21ed1f6a-d0d1-42d3-af93-3296d20daf32 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=3172df6a-e0bd-4fde-b9d0-4eccd5f28006 none            swap    sw              0       0
# Mounting /dev/shm as read only
tmpfs     /dev/shm     tmpfs     defaults,ro     0     0

```sudo dumpe2fs /dev/sda5 | grep -Ei "check interval|mount count" :```
dumpe2fs 1.41.14 (22-Dec-2010)
Mount count:              7
Maximum mount count:      21
Check interval:           15552000 (6 months)
```If you're wondering why dev/sda5 shows only 7 mounts its due to the fact I reinstalled the other day under the false assumption the machine was slower to boot as I had messed up the installation / configuration files somehow.

You're correct about ureadahead not profiling on every boot as there is no mention in my /var/log/boot.log file at present but fsck is still there 3 times.```
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/sda5: clean, 164612/915712 files, 940093/3661824 blocks
/dev/sda1: clean, 229/427680 files, 18959/854272 blocks
/dev/sda7: clean, 994/18169856 files, 1286691/72649216 blocks
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting AppArmor profiles                                                  [ OK ]
 * Stopping System V initialisation compatibility                              [ OK ]
 * Starting System V runlevel compatibility                                    [ OK ]
 * Stopping automatic crash report generation                                  [fail]
 * Starting CPU interrupts balancing daemon                                    [ OK ]
 * Starting deferred execution scheduler                                       [ OK ]
 * Starting regular background program processing daemon                       [ OK ]
 * Starting ACPI daemon                                                        [ OK ]
 * Starting anac(h)ronistic cron                                               [ OK ]
 * Starting save kernel messages                                               [ OK ]
```To give you an idea of boot times my 2.5 year old machine boots in ca 40-45 seconds to the login prompt (it takes 15 seconds to get past the bios screen) and then another 5-8 seconds after entering the password.

Thanks again for all your help, much appreciated.

---

### Post by matt_symes on 2011-06-08
Hi

There is no problem with swap :D

ureadahead also looks good.

fstab looks good.

fsck has not run after three reboots but once on three different partitions.
[FONT=monospace]
[/FONT]> fsck from util-linux-ng 2.17.2 
fsck from util-linux-ng 2.17.2 
fsck from util-linux-ng 2.17.2 
/dev/sda5: clean, 164612/915712 files, 940093/3661824 blocks 
/dev/sda1: clean, 229/427680 files, 18959/854272 blocks 
/dev/sda7: clean, 994/18169856 files, 1286691/72649216 blocksThere is no problem there. dumpe2fs looks good.

Try running a bootchart and posting that back.

Kind regards

---

### Post by ianc1 on 2011-06-08
[LEFT]So fsck should run for each partition on boot?

I attach the bootchart.  Wow what a complex graph, I have no idea where to start with this.  If this makes sense to you I envy you.  I can tell from the top plot that there is ca 10 s where pretty much nothing goes on.  I'm fairly sure it didn't take that long for me to enter my password, but I could be mistaken.

Thanks yet again.
[/LEFT]

---

### Post by matt_symes on 2011-06-08
Hi

> **ianc1 said:**
> [LEFT]So fsck should run for each partition on boot?
[/LEFT]

[LEFT] fsck will run on every partition that you have set it to run on in /etc/fstab if it's due to run.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Read the above link and have a look at options 5 and 6 in fstab.

> 
I attach the bootchart.  Wow what a complex graph, I have no idea where to start with this.  If this makes sense to you I envy you.  I can tell from the top plot that there is ca 10 s where pretty much nothing goes on.  I'm fairly sure it didn't take that long for me to enter my password, but I could be mistaken.

Thanks yet again.
[/LEFT]
It's getting late here. I will look tomorrow.

Bump this thread.

Kind regards

---

