---
title: "Mount of root file system failed"
date: 2009-12-17
forum: General Help
---

### Post by caddict on 2009-12-17
ok i've screwed something up
the thing is i didn't really DO anything
i was intending tp create a new partition in some free space...i started the process but didn't hit 'create'
i was trying to get brasero/k3b/gnomebaker to write to cdrom, but again i'm not aware of doing anything bad...

i tried to add new software sources but got a message something like "cannot execute...as root". thinking maybe i had somehow become root, i rebooted. now i get the dreaded msg

Mount of root filesystem failed...

with my minimal knowledge and following threads here, i have checked fstab and run e2fsck. look ok to me but it would be great if someone could have a look and give me some ideas of where to go from here. i tried various options with the fstab entries with no success. and multiple reboots

screen shots attached

---

### Post by caddict on 2009-12-17
i notice that when the maintenance shell starts, i am logged in as root. is this ok? and, if i cd to home and ls, there is nothing...

---

### Post by philinux on 2009-12-17
Let it boot to the shell and use this.

```
fsck -y /dev/sdb1
```

---

### Post by caddict on 2009-12-17
thanks phil, the output is

/dev/sdb1: clean, 298394/550528 files, 1756315/2196880 blocks

---

### Post by caddict on 2009-12-18
anymore ideas, anyone...

---

### Post by caddict on 2009-12-23
still stuck with this problem

booting into recovery mode gives this msg:
```
mountall: mount /dev/pts [422] terminated with status 32
mountall: Filesystem could not be mounted: /dev/pts [   21.725662] devpts: called with bogus options
mount: wrong fs type, bad option, bad superblock....
```
does this give any clue to the problem?

also, if i boot with the live cd, how would i navigate to my original filesystem from the terminal?

---

### Post by Arand on 2009-12-23
Add -f to the command to force the check, like so:```
fsck -fy /dev/sdb1
```
- Arand

---

### Post by caddict on 2009-12-23
thanks arand

the check seems to be ok. it did 5 passes with no errors. the output is 
```
/dev/sdb1: 298394/550528 files (3.4% non-contiguous), 1756315/2196880 blocks
```

---

### Post by Arand on 2009-12-23
This is something I've not seen/used myself, and I have no idea whether or not it might be relevant, but looking at ```
fsck --help
```there are the " -b " and " -c " flags..
{alternative superblock & check badblocks (might have to use -f with them as well)}
..which might be worth a shot, if nothing else.
- Arand

---

### Post by caddict on 2009-12-23
fsck -c did do something..."updating bad block inode" and "fs was modified, reboot linux"

rebooting into recovery mode again gave a different messsage:

```
mountall: mount /dev/pts [422] terminated with status 32
mountall: Filesystem could not be mounted: /dev/pts [   21.725662] devpts: called with bogus options
mount: wrong fs type, bad option, bad superblock....

...Adding 2931852k swap on /dev/sdb4. Priority -1 extents 1 across 2931852
```

same msg again on reboot, but at least some change.

---

### Post by Arand on 2009-12-23
You might want to try running these same fsck commands from a livecd as well (use the terminal, with " sudo " prepended)

Onwards though.. I really do not know
(I have no idea what, apart from filesystem mess-ups, might cause something like this, and I do not know of anything else than these fsck commands that could correct filesystem mess-ups)
There seems to be someone having had the same issue at [http://ubuntuforums.org/showthread.php?t=1328385](http://ubuntuforums.org/showthread.php?t=1328385) however there were no confirmed solutions there, only additional suggestions.

For your other questions:

Yes the recovery mode is supposed to be root {hence you can recover even if you forgot your password (and yes, if anyone has physical access to your computer, most security measures [except bios pwd/encryption] are in fact moot)}

If you boot on the liveCD you should in your places menu have a "##.# GB Media" (You will have 2 of these, one for root " / " filesystem and one for " /home ") which if you click should be mounted and browsable in the file manager automatically.

However, if the root filesystem is indeed kaputt (as your error might imply) it might be trickier, although, most of your personal data would normally be contained on /home and hopefully you'll be able to browse that one.

- Arand

---

### Post by caddict on 2009-12-24
the fs is readable and all looks good from the live cd

but this is more interesting. i decided to try booting with different kernels. 2.6.27.14 almost did it, but 2.6.28.15 actually booted the system perfectly...with one problem, and this may be the real issue here; in fact this was the first strange behaviour that i noticed before the boot failure problem.

if i try to perfom any tasks from gnome requiring root privileges, after entering my password, i get "failed to run ... as user root...sudo does not allow you to run this program"

if i try using sudo commands from terminal, i get " steve is not in the sudoers file ..."

of course i can't imagine how this came about, or how it prevents me from booting with some kernels. i don't think it is possible to add my user to the sudoers list unless i boot into recovery mode as root. 

what would be the best approach here?

btw merry christmas to everyone who celebrates it ...

---

### Post by JKyleOKC on 2009-12-24
> **caddict said:**
> if i try using sudo commands from terminal, i get " steve is not in the sudoers file ..."

of course i can't imagine how this came about, or how it prevents me from booting with some kernels. i don't think it is possible to add my user to the sudoers list unless i boot into recovery mode as root. 

what would be the best approach here?
Boot into recovery mode as root (which gives you all necessary permissions so be very cautious), and make sure that you are a member of the "admin" group in addition to any others. That should put you in the sudoers list with no need to edit the sudoers file itself. Then re-boot to see if you're okay again.

---

### Post by caddict on 2009-12-24
thanks for that

in recovery mode the admin group did not exist in /etc/group. (assuming that's the right place). so i added a line

```
admin:x:steve:
```

but not successful.

another thing, at boot in recovery mode there are a list of warnings: 

udevd[2315]: specified group 'blah' unknown

where blah = dialout, plugdev, disk, fuse, tty, kmem, video, floppy, cdrom, tape and others

does this give any clues? could it be that the boot process is reading the wrong group file??

---

### Post by caddict on 2009-12-24
actually now i see that the line in the group file should probably read 
```
admin:x:##:steve:
```
where ## is some number...

---

### Post by caddict on 2009-12-24
looking more closely at a group file posted at

[http://psychocats.net/ubuntu/sudo]("http://psychocats.net/ubuntu/sudo")

i can see that a lot of entries seem to be missing from my group file...

i might try copying and editing the one from above link

can the group file become corrupted?

---

### Post by caddict on 2009-12-24
ok we're back in business, booting perfectly into 2.6.31-17 as if nothing ever happened. i added the following lines to /etc/group:

```
admin:x:106:steve
adm:x:4:steve
sudo:x:27
```

maybe only the first one was required (the first time i added ```
admin:x:steve:
``` which was wrong)

it is possible that i inadvertently deleted the admin group at some earlier time.

thanks arand and jkyle :)

---

### Post by Dutch Treat on 2009-12-30
> **caddict said:**
> ok we're back in business

Hi - I am having the same exact problem.

Only: I am a beginner in Linux / Ubuntu.

I have a Ubuntu 9.04 CD ('Desktop Edition' = LiveCD?) 

My system has upgraded to Ubuntu 9.10 and was running smoothly untill yesterday. 

Could you summarize what steps I exactly need to take? 


Thanks in advcance for any help !

---

### Post by Arand on 2009-12-31
So.. to edit the file in question you will have to use the terminal (Applications>Acessories>Terminal).
First you might want to do:```
sudo cp /etc/group /etc/group_backup
```which will create a backup file should the original accidentaly end up in a mess.

Then to edit the original use:```
gksudo gedit /etc/group
```This will open the file in question with root privilieges for editing.
Then check to see if the lines caddict mentioned are present there, and if necessary add those lines where appropriate.

Should you need to restore from the backup just do:```
sudo cp /etc/group_backup /etc/group
```

---

### Post by Dutch Treat on 2009-12-31
> **Arand said:**
> 
Then check to see if the lines caddict mentioned are present there, and if necessary add those lines where appropriate.


That is 

= = = 
Code:

admin:x:106:steve
adm:x:4:steve
sudo:x:27

and 

admin:x:steve:
= = = 

Thanks - will do ! 


BTW: what does stand 'steve' for? (should I replace it with something of my own?)

---

### Post by Dutch Treat on 2009-12-31
I added all - except for sudo:27, which was there - but it will not boot on.

After booting I have a 'dark' screen - has been like that since the beginning - so I can't really see what's happening / what the status is.

Any further suggestions? 


(and: a Happy New Year!)

---

### Post by caddict on 2009-12-31
instead of "steve" you should write you normal username.

do you see the grub screen where you can choose the kernel boot options?

if you do, after that do you get any messages?

also, make sure you entered the code exactly. the important line is
```
admin:x:106:your-username
```
this will add you to the admin group
and make sure there is no other group in that file with the number 106

---

### Post by Dutch Treat on 2010-01-01
Made the changes like you said. But no booting into Ubuntu.

The GRUB message I see is when the system is booting from LiveCD is: " GRUB loading stage1.5 " and " Press 'ESC' to enter the menu " 

After that thew screen goes dark - and after sometime the disk stops reading data.

---

### Post by caddict on 2010-01-02
are you booting from the live cd?

you need to somehow generate some error messages to get some clues.

can you boot into recovery mode?

---

### Post by HiImTye on 2010-01-02
sounds like they changed from ext2/3 to ext4 for their main drive post-install if it boots fine using a previous kernel (and the output of something you posted lists 'extents')

this is a big PITA as it will work perfectly until you upgrade your kernel and then it will fail unless you boot off that old kernel fixing it is alot of work and rather it's easier to just install ubuntu over using ext4

---

### Post by Dutch Treat on 2010-01-15
> **caddict said:**
> are you booting from the live cd?

you need to somehow generate some error messages to get some clues.

can you boot into recovery mode?


I let the system rest for some weeks because I could not get it to startup again.

Yes, I did try tot boot up in recovery, but from the HDD.


I will try and boot - in recovery - from LiveCD now. 

I'll post the results later today.

---

### Post by ashrocks on 2010-11-11
Hi ,

I have the same problem. i am trying to fix from a week.

My error message says.

"Gave up waiting for root device. Common Problems
-Boot ards (cat /proc/cmdline)
  -Check rootdelay- (did the system wait long enough?)
  -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/cciss/c0d0p1 does not exist. Dropping to a shell !

BusyBox v1.1.3 (Debian 1:1.1.3-4) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)_       "

This is the exact same message i got when i tried to reboot. After a little research i found out that the root file system failed to mount. There is no way i can execute any simple commands through initramfs built in shell as it returns: command not found.

I even cannot do a fsck : command not found error.

If anyone can help how can fix this bug, i will be very grateful.

FYI, i can get into the harddisk and see all the contents and parititions when i use a rescue shell from a rescue disk of the debian. But i cannot clone or copy files. It returns error. I don't want to lose any information so i'm not installing it afresh without a backup.

Any inputs will be highly appreicated. 

Thank you for your time

Ash

---

### Post by Dutch Treat on 2010-11-11
> **ashrocks said:**
> Any inputs will be highly appreicated. 

Thank you for your time

Ash


Same for me - I still am waiting for a solution ...


(had to go back to Windows Vista on another eco-system ;-)

---

