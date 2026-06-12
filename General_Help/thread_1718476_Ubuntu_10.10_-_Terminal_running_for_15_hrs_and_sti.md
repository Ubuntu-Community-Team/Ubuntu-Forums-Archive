---
title: "Ubuntu 10.10 - Terminal running for 15 hrs and still going. Please HELP THANKS"
date: 2011-03-31
forum: General Help
---

### Post by kaisar89 on 2011-03-31
Hi, im trying to recover important data from a DVD-+RW discs which have been quick formatted by accident. I have been following some instructions given to me by a user on these forum. I think somethings gone wrong, either incorrect instructions or something wrong with my PC. [COLOR=Red]TERMINAL BEEN RUNNING FOR 15 HOURS AND STILL COUNTING.[/COLOR]

Heres the original thread that the instructions were given to: [http://ubuntuforums.org/showthread.php?t=1715042](http://ubuntuforums.org/showthread.php?t=1715042)

This is the last command i entered and since then the terminal has been running for over 15 hours.

[COLOR=Red]Now, you need to use the dd command to create backup image of the DVD like this:

[/COLOR]   	[COLOR=Red]Code:[/COLOR]
 	[COLOR=Red]sudo dd if=/dev/cdrom of=~/backup.img bs=512 conv=notrunc,noerror[/COLOR] 
Can someone please help me,

---

### Post by r-senior on 2011-03-31
If that dd command was still reading from the disk, I think you'd hear it.

Is there a file called backup.img in your home directory? How big is it?

It's safe to open another terminal window. Right-click in the middle of the one that's open and select "New Window".

Did you unmount the DVD as per step 2?

*Don't enter this command, this is what you should have done as step 2*
```
sudo umount /dev/cdrom
```

If you want to check, look at or post the output of:

```
mount
```

---

### Post by kaisar89 on 2011-03-31
> **r-senior said:**
> If that dd command was still reading from the disk, I think you'd hear it.

Is there a file called backup.img in your home directory? How big is it?

It's safe to open another terminal window. Right-click in the middle of the one that's open and select "New Window".

Did you unmount the DVD as per step 2?

*Don't enter this command, this is what you should have done as step 2*
```
sudo umount /dev/cdrom
```If you want to check, look at or post the output of:

```
mount
```
 
Hi, thanks for the reply. Yes i have a file called backup.img but its 0 bytes and has a padlock on the icon,
I canceled the terminal about 20 min after i posted this thread, it was slowing my computer down.

[COLOR=Red]Is it possible you could tell me which order i have to follow the tutorial?[/COLOR] And how long should it take for 4.7Gb  dvd-rw disc?

Thanks in advance.

---

### Post by kaisar89 on 2011-03-31
bump, please reply.

---

### Post by r-senior on 2011-03-31
Please don't bump a thread after only an hour. People have other commitments.

Anyway, I tried the said command with a DVD:

```
$ time dd if=/dev/sr0 of=~/Desktop/backup.img bs=512 conv=notrunc,noerror
8414552+0 records in
8414552+0 records out
4308250624 bytes (4.3 GB) copied, 565.957 s, 7.6 MB/s

real	9m26.040s
user	0m2.130s
sys	0m57.280s

```

So a matter of minutes if all goes well. 

Not sure why yours is 0 bytes. Obviously the command didn't read anything from the drive. The reason for the padlock is that you ran it as sudo: the file will be owned by root and probably have permissions -rw-r--r--.

To take ownership of it:

```
$ sudo chown kaisar.kaisar ~/backup.img
```

Obviously substitute whatever your username is.

It may be that /dev/cdrom is not linked to the correct device. Unlikely but worth a check. Drop a good CD or DVD in the drive and use the mount command to see what it automounts as (assuming it does automount).

```
$ mount
```

Look for something that looks like whatever you put in the drive and make a note of the device. In my case, a Muddy Waters DVD was pretty obvious:

```
[COLOR="Red"]/dev/sr0[/COLOR] on /media/[COLOR="Red"]MUDDY_WATERS[/COLOR] type udf (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500)
```

Unmount the drive with:

```
$ sudo umount [COLOR="Red"]/dev/sr0[/COLOR]
```

Then try your command again with your broken DVD but substitute what you know to be the correct device. It should sound like a small jet taking off and the noise will continue after the dd command has finished. I had to eject the disk manually.

Processor never got above 6% while this was running by the way.

I can't help you with the rest of the instructions in that post I'm afraid.

EDIT: When you try again, if it doesn't work, post the end of your syslog:

```
tail -100 /var/log/messages > ~/syslog.txt
```

---

### Post by kaisar89 on 2011-03-31
Hi, ive just put pulp fiction dvd into the drive then entered the command[FONT=monospace][COLOR=Red]$ mount[/COLOR] and the response i got was[COLOR=Red] $: command not found[/COLOR]

[COLOR=Black]i tried to play the disc but it would not play, it recognizes that a pulp fiction movies in the drive but does not play.

what i shall i do, is my DVD drive messed up.
[/COLOR][/FONT]

---

### Post by kaisar89 on 2011-03-31
kaisar@kaisar-D2190-A:~$ **[COLOR=Red]mount[/COLOR]**
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kaisar/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kaisar)
/dev/sdg1 on /media/Expansion Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0 on /media/PULPFICTION_DISC1_REG2 type udf (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
kaisar@kaisar-D2190-A:~$ **[COLOR=Red]$ mount[/COLOR]**
$: command not found
kaisar@kaisar-D2190-A:~$

---

### Post by r-senior on 2011-03-31
You don't need to enter the '$'. That's just a shorthand way of saying you should enter it as a terminal prompt. (That's the second time that's confused someone today - must be clearer in future).

Let's rewind. You have a DVD that you can't read from so you've gone into a process of trying to recover the data from it. Now you suspect that your DVD drive is not working.

1. Do you know someone who can try the "broken" DVD disk and confirm it's not readable?

2. Do you have another data disk you could try in the drive to rule out drive errors?

3. Do you have another operating system, e.g. Windows where you can try both the "broken" DVD and a good DVD in the drive? This would rule out Ubuntu configuration/software errors.

---

### Post by kaisar89 on 2011-03-31
> **r-senior said:**
> You don't need to enter the '$'. That's just a shorthand way of saying you should enter it as a terminal prompt. (That's the second time that's confused someone today - must be clearer in future).

Let's rewind. You have a DVD that you can't read from so you've gone into a process of trying to recover the data from it. Now you suspect that your DVD drive is not working.

1. Do you know someone who can try the "broken" DVD disk and confirm it's not readable?

2. Do you have another data disk you could try in the drive to rule out drive errors?

3. Do you have another operating system, e.g. Windows where you can try both the "broken" DVD and a good DVD in the drive? This would rule out Ubuntu configuration/software errors.

Sorry for not being clearer. i [COLOR=Red]quick formatted the DVD[/COLOR] by accident and [COLOR=Red]lost some important holiday pictures which need to be recovered. [/COLOR]

1. the disk is readable but its been quick formatted, so i need the data that was on the disc before recovered, it had my brothers important holiday pics.

2. i have several shop bought dvds which i can try, eg avatar dvd which literally brand new.

3. sorry i have no other operating system, only ubuntu, i think i may have some problems playing dvd movies, as when i tested pulp fiction, the drive recognized the dvd but would not play it, even in vlc player.

---

