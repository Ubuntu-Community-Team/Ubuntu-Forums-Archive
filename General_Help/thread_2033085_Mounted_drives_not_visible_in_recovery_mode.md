---
title: "Mounted drives not visible in recovery mode"
date: 2012-07-25
forum: General Help
---

### Post by nurbles on 2012-07-25
I booted into 12.04's recovery mode yesterday to look for some lost disk space that might have been the files that were in the /home folder tree before I moved it to a separate drive. I (incorrectly) did not expect /home to be mounted and when I used the 'mount', 'cat /etc/mtab' and 'df -h' commands to get a few different ways of seeing what was mounted, they showed that only / (/dev/sda1) was mounted, as I expected.

Unfortunately, /home (/dev/sdb1) actually *WAS* mounted, but none of the three commands listed above included it in their list. Yet when I ran 'mount -t ext4 /dev/sdb1 /mnt/b' and then ran 'mount' the new drive/mount point WAS listed. If I created a new file in /home, it was immediately visible in /mnt/b as well. This can only mean that /dev/sdb1 was actually mounted on /home as well as /mnt/b even though none of mount, mtab and df showed anything mounted on /home.

This is on a live mail server, but if necessary I can boot into recovery mode again and duplicate the problem, which I would consider to be rather critical. The system tools that report mounted drives should never fail to report something that is actually mounted!

FWIW, this machine got to 12.04 by upgrading 11.04 => 11.10 => 12.04 and AFTER upgrading to 12.04, I added two additional hard drives (sdb1 and sdc1) to be mounted as /home and /home/vmail, then moved the files to them, added them to fstab and they've worked fine ever since.  Except they didn't show as mounted in recovery mode even though they were.

---

### Post by Paddy Landau on 2012-07-25
I have tried to replicate this without success. I wonder if there was something, perhaps an error you didn't spot, to do with the system's read-only status? If I enter [FONT=Lucida Console]mount[/FONT] without making the system read-write, I get the list of mounted partitions, but I also get this error at the end:
```
mount: warning: /etc/mtab is not writeable (e.g. read-only file-system).
       It's possible that information reported by mount(8) is not
       up to date. For actual information about system mount points
       check the /proc/mounts file.
```Indeed, if I then mount [FONT=Lucida Console]/home[/FONT] on a pre-created [FONT=Lucida Console]/mnt/b[/FONT] (it has to have been created beforehand because the system is read-only), [FONT=Lucida Console]mount[/FONT] fails to list the newly-mounted partition.

As I cannot replicate the problem, please do try to replicate it yourself. If you do manage, please take careful note of the steps you took so that we can duplicate your error.

By the way: You don't need [FONT=Lucida Console]-t[/FONT] [FONT=Lucida Console]ext4[/FONT] on your mount command, because it figures it out by itself. You can also use [FONT=Lucida Console]/run[/FONT], which is read-write, because it is loaded in memory. Example:
```
mkdir /run/b
mount /dev/sdb1 /run/b
```

---

### Post by nurbles on 2012-07-25
I think you've figured it out, except for a couple things you didn't know.  My sequence was:

[LIST=1]
[*]Boot into Recovery Mode
[*]Look in /media/usb0 (which is physically disconnected) to see if there were files that did not belong
[*]Attempt to remove the files and discover / is mounted RO
[*]Remount / as RW
[*]Remove the files from /media/usb0
[*]Check to see if there are files that don't belong in /home (since I believe /home is *NOT* mounted)
[*]When home folders are discovered, use 'df' and 'mount' to see if the system says /home is mounted.  It does not (and no warnings are produced)
[*]Mount /dev/sdb1 (which contains /home) at /mnt/b to double check
[*]mkdir /home-old and move the first directory from /home to /home-old
[*]Look in /mnt/b and discover that the first directory is unexpectedly GONE!
[*]Put the directory back where it belongs
[*]Report a bug because the system fails to report drives that are not only mounted, but mounted as RW
[/LIST]
Since I didn't run mount before step #4, I never saw a warning about /etc/fstab not being writable and, apparently, once /etc/fstab WAS writable, mount "forgot" that it had ever mounted drives that were not listed there.

Tomorrow morning (a very slow time for our mail server) I'm going to boot into recovery mode to see if /proc/mounts and/or /proc/partitions shows that things ARE mounted.  If (as I suspect) they do, I think we should suggest to the mount maintainers that it always verify fstab with something else and report discrepencies.  Otherwise this situation seems possible in any time /etc/fstab is RO and addition mounts are executed during boot (especially since with / mounted RO, there was no boot log of dmesg or kernel log to check for possible error messages (I even looked for them when I experienced the "hidden" mounts.

---

### Post by Paddy Landau on 2012-07-25
> **nurbles said:**
> I think you've figured it out, except for a couple things you didn't know...
In steps 4 and 8, please let us have the exact command that you entered.

> **nurbles said:**
> ... I'm going to boot into recovery mode to see if /proc/mounts and/or /proc/partitions shows that things ARE mounted.
Let us know what happens.

I shall load this into a virtual machine, with two disks, to try to duplicate what you had. Please let us know specifically what version of Ubuntu you have: I know it's 12.04, but is it Ubuntu Server or Desktop, and is it fully updated? If it does not contain anything confidential, would you also provide your [FONT=Lucida Console]/etc/fstab[/FONT].

---

### Post by nurbles on 2012-07-26
#4 command:  mount / -o remount,rw

#8 command:  mount /dev/sdb1 /mnt/b

FWIW, I watched the messages displayed during the boot sequence and as far as I could tell, it showed /dev/sda1 (or '/' to me) mounted RO, then a screenful or two later it showed /dev/sdb1 and /dev/sdc1 (/home and /home/vmail, respectively) also mounted as RO and there were no mount warnings or errors displayed.

Once booted into recovery mode, I looked and /proc/mounts and it did, indeed, have the correct listing of mounted drives, while /etc/mtab (as expected) did not.  After entering #4 above, there was little change to either file, except RO changed to RW for the root mount entry. My /etc/fstab is below (and all the comments that say 'was' are still 'is' -- I just copied the comment made for / by the installer when I added my other two drives.)

```
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=5a38a6d5-625a-4ef9-bd83-d615b99848e7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=70f47249-9c60-4845-999a-aedb32b5bc23 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /home was initially on /dev/sdb1
UUID=ac60cbf3-5b67-4dcf-a117-8889d0666109 /home           ext4    errors=remount-ro 0       0
# /home/vpopmail was initially on /dev/sdc1
UUID=62b89d89-5397-4b5a-b94f-7e478cefac88 /home/vmail     ext4    errors=remount-ro 0       0
```If there is any additional information I can provide, or things I can check, please let me know and I'll do my best to comply.

---

### Post by Paddy Landau on 2012-07-26
Thanks for the answers. To clarify:

[LIST=1]
[*]Your current [FONT=Lucida Console]/home[/FONT] is [FONT=Lucida Console]/dev/sdb1[/FONT], but your original [FONT=Lucida Console]/home[/FONT] was [FONT=Lucida Console]/dev/sda1[/FONT] in still-existing folder [FONT=Lucida Console]/home[/FONT], is that right?
[*]You use Ubuntu Desktop and not Ubuntu Server?
[/LIST]
Furthermore, in a normal boot (not Recovery Mode), you can verify that what you *think* is mounted is indeed what is mounted. Enter the following command:
```
sudo blkid
```Then:

[LIST]
[*]Check that none of the UUID's listed is a duplicate of another (it  should not be, but it might have happened if, for example, you cloned a  partition).
[*]Match the partition + UUID's shown with those in [FONT=Lucida Console]/etc/fstab[/FONT] to ensure that your [FONT=Lucida Console]/[/FONT], [FONT=Lucida Console]/home[/FONT], [FONT=Lucida Console]/vpopmail[/FONT] and swap really are on the partitions you think they are. (In other words, you are double-checking point 1 above.)
[/LIST]
It may help to post the results of [FONT=Lucida Console]sudo[/FONT] [FONT=Lucida Console]blkid[/FONT] here.

I know this may seem like overkill, but we should eliminate the simple before looking at other possibilities.

I will try later today to duplicate your situation in a virtual machine.

---

### Post by nurbles on 2012-07-26
Sorry, I forgot to answer the system type... I'm fairly certain I installed Ubuntu Server 11.04 (it was about nine months ago) and upgraded to 11.10, then to 12.04.  When I log in I see this:

Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-27-generic-pae i686)

Also, if it helps, cat /etc/issue gives:

Ubuntu 12.04 LTS \n \l

and cat /proc/version offers:

Linux version 3.2.0-27-generic-pae (buildd@akateko) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #43-Ubuntu SMP Fri Jul 6 15:06:05 UTC 2012

As for the partitions and mount points:  when I originally installed (and upgraded twice), I only had /dev/sda1 which contained /, /home and /home/vmail (among others).  About a month ago, two additional drives were donated and I chose to use one for the user's ftp areas (/home, aka /dev/sdb1) and the other for all of the mail folders (/home/vmail, aka /dev/sdc1).  There may also be a USB drive (/dev/sdd1) mounted for backups, but that's done manually as needed.

I did the 'sudo blkid' and the output looks good to me, every UUID is unique and they match those shown by 'ls -l /dev/disk/by-uuid' (as expected.)  I used blkid to *get* the UUID values that I put in /etc/fstab for the two new drives, so I sure hope they are correct! ;-)   FWIW, here's the blkid output:
```
/dev/sda1: UUID="5a38a6d5-625a-4ef9-bd83-d615b99848e7" TYPE="ext4"
/dev/sda5: UUID="70f47249-9c60-4845-999a-aedb32b5bc23" TYPE="swap"
/dev/sdb1: LABEL="/home" UUID="ac60cbf3-5b67-4dcf-a117-8889d0666109" TYPE="ext4"
/dev/sdc1: LABEL="/home/vmail" UUID="62b89d89-5397-4b5a-b94f-7e478cefac88" TYPE="ext4"
/dev/sdd1: LABEL="/mnt/backup2" UUID="c5909455-fffb-4843-a1ce-8875b0661370" TYPE="ext4"
```By the way, thanks for taking so much time to look into this.  I'm certain we resolved *my* problem, but I'm happy to continue trying to help if you think there is another resolvable issue here (like the /etc/mtab vs /proc/mounts debate, which apparently has been around a long time:  [http://www.xss.co.at/sysinfo/mounts.html](http://www.xss.co.at/sysinfo/mounts.html))

---

### Post by Paddy Landau on 2012-07-26
Thanks for all the information. It looks as though everything is in order.

I have never used Ubuntu Server, so this will be a nice learning curve for me as I attempt to duplicate your set-up!

I am about to download the 11.04 ISO, and I shall let you know when I have run my test &#8212; which may be only tomorrow.

There are a couple of things that I see are different.

[LIST=1]
[*]You have 32-bit, whereas I use 64-bit. However, I shall use 32-bit in my test.
[*]My installations are always fresh, whereas you have upgraded from 11.04 to 11.10 to 12.04. I shall attempt to do the same as you in my test.
[/LIST]

---

### Post by Paddy Landau on 2012-07-26
I've run the test as follows. However, apart from the misreporting of [FONT=Lucida Console]mount[/FONT], everything worked correctly for me.

[LIST]
[*]Installed 11.04 server 32-bit with one disk ([FONT=Lucida Console]/dev/sda[/FONT]). [FONT=Lucida Console]/dev/sda1[/FONT] has root (including [FONT=Lucida Console]/home[/FONT] and [FONT=Lucida Console]/home/vpopmail[/FONT]). [FONT=Lucida Console]/dev/sda5[/FONT] has swap.
[*]Updated and added test files.
[*]Upgraded to 11.10 and updated.
[*]Upgraded to 12.04 and updated.
[*]Added disks [FONT=Lucida Console]/dev/sdb[/FONT] and [FONT=Lucida Console]/dev/sdc[/FONT]. Formatted. Copied files across as required.
[*]Modified [FONT=Lucida Console]/etc/fstab[/FONT] to use the new disks (to duplicate your situation).
[*]Rebooted to ensure it worked. Deleted files, amended files, added new files.
[*]Booted from a Live CD to ensure that everything looks as it should.
[/LIST]

So far, so good.

I booted into Recovery Mode. I had the same experience as you:

[LIST]
[*][FONT=Lucida Console]/proc/mounts[/FONT] is correct: only [FONT=Lucida Console]/dev/sda1[/FONT] mounted, read-only.
[*][FONT=Lucida Console]mount[/FONT] shows [FONT=Lucida Console]/dev/sdb1[/FONT] and [FONT=Lucida Console]/dev/sdc1[/FONT] mounted as they are supposed to be (but in fact are not). I guess this is because of the known bug that [FONT=Lucida Console]mount[/FONT] is incorrect when the system is read-only.
[*][FONT=Lucida Console]/home[/FONT] is what you would expect at this point: the old [FONT=Lucida Console]/home[/FONT] on [FONT=Lucida Console]/dev/sda1[/FONT], not the new one on [FONT=Lucida Console]/dev/sdb1[/FONT].
[/LIST]
```
mount --options=rw,remount /
```
[LIST]
[*]At this point, everything is as I expect. [FONT=Lucida Console]mount[/FONT] still incorrectly claims that [FONT=Lucida Console]/dev/sdb1[/FONT] is mounted on [FONT=Lucida Console]/home[/FONT], while [FONT=Lucida Console]/proc/mounts[/FONT] is correct.
[/LIST]
```
mount /dev/sdb1 /mnt/b
```Again, I think the same experience as you, if I correctly understood.

[LIST]
[*][FONT=Lucida Console]/proc/mounts[/FONT] shows what we'd expect: [FONT=Lucida Console]/dev/sdb1[/FONT] mounted on [FONT=Lucida Console]/mnt/b[/FONT].
[*][FONT=Lucida Console]mount[/FONT] shows [FONT=Lucida Console]/dev/sdb1[/FONT] mounted *twice*: once on [FONT=Lucida Console]/home[/FONT] and once on [FONT=Lucida Console]/mnt/b[/FONT].
[*]At least everything is mounted correctly: [FONT=Lucida Console]/home[/FONT] is still the old [FONT=Lucida Console]/home[/FONT], and [FONT=Lucida Console]/mnt/b[/FONT] is the new [FONT=Lucida Console]/home[/FONT].
[/LIST]
Create [FONT=Lucida Console]/home-old[/FONT] and move a file from [FONT=Lucida Console]/home[/FONT] (the old [FONT=Lucida Console]/home[/FONT], that is) to [FONT=Lucida Console]/home-old[/FONT].

[LIST]
[*]At this point, everything is correct.
[/LIST]
So, as I said, everything worked correctly for me.

I surmise that you are doing something of which we are unaware that has an "interesting" side-effect.

Go back into Recovery Mode, mount as read-write, and check that [FONT=Lucida Console]/home[/FONT] is the old one. Mount [FONT=Lucida Console]/dev/sdb1[/FONT] on [FONT=Lucida Console]/mnt/b[/FONT]. Again, check that [FONT=Lucida Console]/home[/FONT] is the old one, and that [FONT=Lucida Console]/mnt/b[/FONT] is the new one. If anything is wrong, report back.

**By the way:**

I would recommend that instead of trying to move files and folders from the old [FONT=Lucida Console]/home[/FONT] to a holding area, simply rename the old [FONT=Lucida Console]/home[/FONT] to [FONT=Lucida Console]/home-old[/FONT]. Then you can reboot into normal mode and mess around as you need!

---

### Post by nurbles on 2012-07-26
Your test sequence sounds like what I remember doing.  When I moved /home to the new drive, I first renamed it (I was in single user mode that time, so it worked), created a new (empty) /home to use as a mount point and copied the files to the new drive.  Then I mounted the new drive at /home and I was happy.

I had exactly the OPPOSITE experience with mount in recovery mode.  Remember, I remounted / as RW *before *I checked anything (just in case that was relevant).  When I first ran mount it showed that sdb1 and sdc1 were **NOT** mounted even though they actually **WERE **mounted.

Your suggestion to rename /home as /home-old reminded me that I attempted to do that and it was that command's *failure *that started me looking into what was mounted and what was not.  The rename (mv) command failed and told me that /home was still in use.

I really think that you helped me understand what I saw when you first pointed out that with / (and therefore /etc/mtab) being read-only, mount could not record what it mounted and therefore could not correctly report later.  That PRECISELY describes what I experienced.  If there is anything to fix, it would be any or all of these:

[LIST]
[*]If "recovery mode" is going to mount the root read-only, then it should NOT mount additional drives, especially not for read-write!
[*]mount's problem with a read-only /etc/mtab is apparently well known and yet still not fixed.
[*]any other tools that rely on /etc/mtab will have similar bugs (for example, 'df') when attempting to list or operate on mounted drives.
[/LIST]
Personally, I'll stick to single user mode instead of recovery mode because single user is designed to mount / read-only, NOT mount other partitions and NOT run more than the absolute minimum to provide a starting point for system recovery.  To me, THAT is what a recovery mode *should be*.

Thanks for all of your help, you have gone surprisingly far beyond the call!  You have my sincere thanks and admiration for your effort.

---

### Post by Paddy Landau on 2012-07-27
Thanks for the reply and the clarifications.

This thread started, of course, from [the original reported bug]("https://bugs.launchpad.net/ubuntu/+bug/996454"), which seems to be getting a low priority.

I think we have enough information now to post a comment there stating that the problems stretch beyond a mere inconvenience.

I am unable to duplicate your bizarre problem, but as  you can reliably duplicate it, clearly something is there.

** EDIT:** I am about to post a comment on the bug. You may want to add to it.

**EDIT:** If you boot into Recovery Mode and immediately enter the following two commands, do you still get errors?
```
mount --options remount,rw /
mount --all
```

---

### Post by nurbles on 2012-07-27
> **Paddy Landau said:**
> I am unable to duplicate your bizarre problem, but as  you can reliably duplicate it, clearly something is there.

After what you've helped me learn, I don't believe that I saw an error.  Rather, because the additional drives were mounted while **/etc/mtab** was read-only, they were not reported by **mount** or **df**, both of which produce their lists of mounted drives by reading **/etc/mtab**.  So what I experienced seems to be the expected behavior -- whether or not that is *correct* behavior I'll leave to others.

I believe that anyone, with any distro, could duplicate what I've seen by booting into single user mode (where only the root partition is mounted and it is read only), then mounting their remaining drives read-write and using **mount **or **df **to check for what drives were mounted.  Since **/etc/mtab** should be read-only, the drives mounted (manually) read-write should not be listed, or at least should not appear in **/etc/mtab**.

The fact that my additional drives were mounted during the recovery mode boot (or root sign-in) sequence in **read-write** mode is probably an issue with recovery mode, but then, the fact that recovery mode boots anything that requires **/home** to exist (and/or to be mounted) seems like a mistake to me, since I may need to recover the very thing that is referencing **/home** and it may be difficult to *stop *once it is already running.  But recovery mode itself is not what I was asking about, so again, I'll leave that for others.

> **Paddy Landau said:**
> **EDIT:** If you boot into Recovery Mode and immediately enter the following two commands, do you still get errors?
```
mount --options remount,rw /
mount --all
```

After those commands, the drives appear to be mounted "normally" (i.e. they look like they do after a normal boot) and everything works as expected.

Thanks again for your assistance in helping me learn what I needed to understand what I saw!

---

### Post by Paddy Landau on 2012-07-27
> **nurbles said:**
> ... the fact that recovery mode boots anything that requires **/home** to exist (and/or to be mounted) seems like a mistake to me...
No. Booting is supposed to act upon [FONT=Lucida Console]/etc/fstab[/FONT]. It does not require [FONT=Lucida Console]/home[/FONT] to exist. It simply was unable to do so because the root system was read-only (surely such information should be stored in RAM?).

It is simple to undo such mounting: just enter the appropriate [FONT=Lucida Console]umount[/FONT] command. The only partition that you cannot dismount is root itself.

---

### Post by nurbles on 2012-07-27
I seems like we're talking about different things, or our opinions of how **recovery mode** is intended to be used...

To me, **recovery mode** should provide the most basic, simple environment possible so that I can make changes to as many of the things that would normally be running as possible.  That would include **NOT** mounting any drives beyond the absolute minimum needed by a *root *log in in case normally mounted drives needed to be maintained/adjusted in some way.  By not mounting any drives (except the one containing **/root**) a **recovery mode** would ensure that nothing was using those drives that may have them locked or may fail in an unexpected and potentially catastrophic way if the drive is unmounted.

So, in my context, everything I saw should have been expected -- except for the fact that **/home** and **/home/vmail** had been automatically mounted as read-write.  That said, I must admit that, since I do not have a list of exactly every command I entered, I cannot say for certain that I am not responsible for the mounted drives. (But I am equally sure that I did not *intend *to mount them, if I, in fact, did so.)

And as for storing the mount information in RAM, I believe that is what one sees by issuing a **cat /proc/mounts** command.  Since **/proc** is a virtual filesystem that generally results in a system or driver subroutine being called to print information to stdout, I think that **/proc/mounts** is indeed a list of what the operating system thinks is mounted.  That is why I believe (as do others) that tools like **mount** should compare **/etc/mtab** with **/proc/mounts** and report discrepancies or do away with **/etc/mtab** altogether, since it *will *be wrong any time something is mounted (or unmounted) when **/etc/mtab** is read-only, but **/proc/mounts**, being virtual, cannot be read-only so it will be correct.

---

### Post by Paddy Landau on 2012-07-28
You raise some excellent points.

I understand what you say about Recovery Mode: it should be read-only and mount nothing else. However, Ubuntu is supposed to be targeted at the "average user", so I wonder if it would be better to offer a choice at the Recovery Mode menu: "Basic" mode, which would be as you describe, and "full" mode, which would be read-write with [FONT=Lucida Console]/etc/fstab[/FONT] taken into account. The latter would be for the typical newbie requests ("I have forgotten my password" and so forth).

Regarding [FONT=Lucida Console]/etc/mtab[/FONT], yes, you are absolutely right. This is a bug and needs to be fixed; but Canonical cannot do that without the rest of the Linux community. I suspect that the solution is probably as simple as moving it into RAM, but as I am not a developer, I could well be wrong.

---

