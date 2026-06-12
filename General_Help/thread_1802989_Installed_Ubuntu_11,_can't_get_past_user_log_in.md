---
title: "Installed Ubuntu 11, can't get past user log in"
date: 2011-07-12
forum: General Help
---

### Post by byob_soad2 on 2011-07-12
I'm completely new to any OS other than Windows, so I have almost literally no idea what I'm doing. Please treat me like the idiot I am when it comes to this :P

After choosing Ubuntu over Windows XP, I get an error:
> There is a problem with the configuration server.
(/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)

I click close and get the sign in prompt. I click my user name and put in my password. I hit enter and I get another message:
> Install problem!
The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator. That goes away, and then the first error comes up again. Then, I'm sent back to the sign in screen.

---

### Post by byob_soad2 on 2011-07-12
I've tried Google to see what I could do, but nothing worked. A lot of things I found seemed to be individual, too; there were different situations and none were like mine.

---

### Post by wildmanne39 on 2011-07-12
Hi, you can give this a try.
Reinstalling from recovery, boot to recovery, choose root prompt with network then run this command. 
```
apt-get update && apt-get install ubuntu-desktop && apt-get upgrade && reboot

```
Here is a link to boot into recovery just in case you do not know how to do it.
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by byob_soad2 on 2011-07-12
> **wildmanne39 said:**
> Hi, you can give this a try.
Reinstalling from recovery, boot to recovery, choose root prompt with network then run this command. 
```
apt-get update && apt-get install ubuntu-desktop && apt-get upgrade && reboot

```Here is a link to boot into recovery just in case you do not know how to do it.
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
Tried it, but no luck.
I did, however, notice this at the end:

Errors were encountered while processing: /var/cache/apt,archives/libreoffice-core_1%3a3.3.2-1ubuntu (the picture I took cut off any more if it exists)
E: sub-process /usr/bin/dpkg returned an error code (1)

I know Libre Office is a program that comes with Ubuntu, but I don't know if the second error line is related to that one or not

---

### Post by wildmanne39 on 2011-07-12
Hi, I am not sure where to go from here there are a lot of things we could try but I do not think they will work in this case. One thought get back into recovery and select upgrade or fix broken packages.

---

### Post by byob_soad2 on 2011-07-12
> **wildmanne39 said:**
> Hi, I am not sure where to go from here there are a lot of things we could try but I do not think they will work in this case. One thought get back into recovery and select upgrade or fix broken packages.
Still nothing :(

---

### Post by wildmanne39 on 2011-07-12
Hi, when you enter the boot screen do you have the option to login to safe mode?

---

### Post by byob_soad2 on 2011-07-12
> **wildmanne39 said:**
> Hi, when you enter the boot screen do you have the option to login to safe mode?
No. GRUB has Ubuntu, Ubuntu Recovery Mode, 2 different memory tests, Windows XP, and Windows NT/2000/Me (or something like that, which I'm guessing is from the old hard drive I took from another computer). Maybe safe mode is found somewhere else?

---

### Post by wildmanne39 on 2011-07-13
> **byob_soad2 said:**
> No. GRUB has Ubuntu, Ubuntu Recovery Mode, 2 different memory tests, Windows XP, and Windows NT/2000/Me (or something like that, which I'm guessing is from the old hard drive I took from another computer). Maybe safe mode is found somewhere else?Hi, ok boot recovery root with network and try
```
apt-get install gdm
```if you get a permission error put sudo in front of it but you shound not get that error.

---

### Post by byob_soad2 on 2011-07-13
> **wildmanne39 said:**
> Hi, ok boot recovery root with network and try
```
apt-get install gdm
```if you get a permission error put sudo in front of it but you shound not get that error.
I tried it once, and I got an error about LibreOffice. I looked at the recovery mode options and did the one to try to free up space. After that, I tried again, and it went through, but I'm still getting those errors.


By the way, thanks for all this time and effort :)

---

### Post by wildmanne39 on 2011-07-13
> **byob_soad2 said:**
> I tried it once, and I got an error about LibreOffice. I looked at the recovery mode options and did the one to try to free up space. After that, I tried again, and it went through, but I'm still getting those errors.


By the way, thanks for all this time and effort :)
Hi, your welcome I am going to sleep on this tonight, in the mean time maybe someone else will have a suggestion.

---

### Post by byob_soad2 on 2011-07-13
No one else? :(

I wish this was something I could just mess around with and hope, but I don't know any of the commands or anything.

---

### Post by wildmanne39 on 2011-07-13
> **byob_soad2 said:**
> No one else? :(

I wish this was something I could just mess around with and hope, but I don't know any of the commands or anything.Hi, I asked a friend to take a look at your problem he has a lot of experience with fixing issues, I do not know if he is online but he is most of the time.

---

### Post by wildmanne39 on 2011-07-13
Hi, give this a try.
```
sudo apt-get install --reinstall gdm

```

---

### Post by mali2297 on 2011-07-13
Perhaps you could try this command (in recovery mode):
```

chmod 1777 /tmp

```
From this thread:[http://ubuntuforums.org/showthread.php?t=1061084](http://ubuntuforums.org/showthread.php?t=1061084).

Also, while in recovery mode, check the disk space usage with the command
```

df

```
Anything close to 100% use?

---

### Post by wildmanne39 on 2011-07-13
Hi, here are two bug reports on this problem.
[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/577545](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/577545)
[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215)

---

### Post by byob_soad2 on 2011-07-13
> **mali2297 said:**
> Perhaps you could try this command (in recovery mode):
```

chmod 1777 /tmp

```From this thread:[http://ubuntuforums.org/showthread.php?t=1061084](http://ubuntuforums.org/showthread.php?t=1061084).

Also, while in recovery mode, check the disk space usage with the command
```

df

```Anything close to 100% use?
/dev/sdb5 says 100% use, but there are 4 other things, 2 at 1% and 2 at 0%

I will look at those bug reports now and see if they help

---

### Post by byob_soad2 on 2011-07-14
Nothing worked :(

---

### Post by mali2297 on 2011-07-14
> **byob_soad2 said:**
> /dev/sdb5 says 100% use, but there are 4 other things, 2 at 1% and 2 at 0%

I will look at those bug reports now and see if they help

Do you know what /dev/sdb5 is used for? In the output of df, what does it say in the column 'Mounted on'?

Perhaps you need to repartition the hard drive to give more space to Ubuntu.

---

### Post by byob_soad2 on 2011-07-14
> **mali2297 said:**
> Do you know what /dev/sdb5 is used for? In the output of df, what does it say in the column 'Mounted on'?

Perhaps you need to repartition the hard drive to give more space to Ubuntu.
all it says is
/

I have no idea what it's for, or even what it is. And how would I repartition it?

---

### Post by wildmanne39 on 2011-07-14
Hi, that is most likely the problem that is your root partition. Here is a link on resizing partitions.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by byob_soad2 on 2011-07-14
[s]Sorry for not replying, I've been busy with school work.

I'm running Ubuntu right now, via the CD's Try feature. I went into GParted and found that Windows and Ubuntu are on different hard drives, with Ubuntu being on one that is only about 20 GB (from an OLD computer), and I cannot resize it any larger than 5.14 GB. Could I get more space for that by moving the files from it to my main hard drive for now? Or, is there a way to move the partition?

EDIT: Here's what's on the small hard drive[/s]


EDIT AGAIN: I ran the install again and it works :D
The only thing is that I now have 4 Ubuntu-related things to choose from in GRUB. It's not a huge deal, I don't think, but it's there :/

Anyway, thanks again for the help and patience :)

---

