---
title: "How do I use FSCK?"
date: 2009-11-13
forum: General Help
---

### Post by jeb800e on 2009-11-13
How do I use FSCK on an Ubuntu or Ubuntu-based computer? I have been trying to figure it out, and I still have had no luck. 
According to Wikipedia, an example of a text to type into the terminal for FSCK is the following:
"fsck /dev/sdb1"

I tried to do that, but replacing "sdb1" with the name of my hard drive, and I got the following message inside the terminal:

"
jeb@Ubuntu-Linux:~$ fsck /dev/sda
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Permission denied while trying to open /dev/sda
You must have r/w access to the filesystem or be root
jeb@Ubuntu-Linux:~$ 
"

Please help me out here! I am planning on trying FSCK on more than one PC, and I would really appreciate your help! Thanks!

---

### Post by Giblet5 on 2009-11-13
First, read the man page (in related news you have manuals...)

Open a terminal window (or just type it in a recovery console) and enter ```
man fsck
```

When any linux program gives you an error message like the one you saw, it is because your current user account does not have adequate priveleges to run the command as entered.

The default user account has management privileges. To invoke them, precede your command with "sudo".

Since you don't likely know what to do with fsck, I recommend that you always use the -n option so that it won't attempt to fix things, but it will check. Example:

```
sudo fsck -n /dev/sdb1
```

Read that manual all the way through before you try to fix a filesystem. The fsck program is very powerful and incredibly stupid at the same time.

---

### Post by jeb800e on 2009-11-13
I got this error message:

"Cannot write to "sudo fsck -n /dev/sda"  (press RETURN)"

---

### Post by Giblet5 on 2009-11-13
Where did you type that?

That is not an error that you will get from a terminal window OR the recovery mode shell.


Open a terminal window: Click on the Application menu -> Accessories -> Terminal

Click inside the window.

Enter ```
sudo fsck -n /dev/sdb1
```

Hit Enter. You will be asked to enter your password - it won't echo as you do so - enter your user password and hit Enter. The fsck program will run.

---

### Post by jeb800e on 2009-11-14
Oh, I typed that after typing "man fsck"

---

### Post by jeb800e on 2009-11-14
I repleaced "sdb1" with my hard drive's name, "sda"
What do I do now??
"
jeb@Ubuntu-Linux:~$ sudo fsck -n /dev/sda
[sudo] password for jeb: 
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?
jeb@Ubuntu-Linux:~$ 
"

---

### Post by Chronon on 2009-11-14
Don't fsck it while it's mounted.  You can boot a LiveCD and fsck from there, or I think there's also a way to force a check at boot time.

---

### Post by jeb800e on 2009-11-14
Should the livecd be of the same version of Ubuntu, or can it be any version of Linux or Ubuntu. Why can't I use FSCK in my normal mode?

---

### Post by wojox on 2009-11-14
> **jeb800e said:**
> Oh, I typed that after typing "man fsck"

Ahh boy.....

---

### Post by scorp123 on 2009-11-14
You can't fsck a harddrive while it's mounted (= in use; e.g. you booted the PC from the harddrive!)

If you really really want to check your harddrive you'd have to boot from e.g. the Live CD and do it from there.

BUT:

Why do you think you need to fsck your drive?? Your system should auto-detect any corruptions when your computer boots. Manually checking your harddrives usually shouldn't be necessary.

---

### Post by scorp123 on 2009-11-14
> **jeb800e said:**
>  Why can't I use FSCK in my normal mode? That's like repairing a car --opening the hood and everything-- while it's driving 180 km/h down the highway .... NOT a bright idea.

Same with fsck ... you can't have it mess with data blocks and what not while the same are in use. It would end in data loss.

---

### Post by wojox on 2009-11-14
It'll eventually do it's own due to the mount count.

---

### Post by jeb800e on 2009-11-14
> **wojox said:**
> Ahh boy.....
I know! lol
I just realised how ridiculous that was! haha :D

---

### Post by jeb800e on 2009-11-14
Is there a way I can get FSCK to run in recovery mode or somthing?

---

### Post by scorp123 on 2009-11-14
> **jeb800e said:**
> Is there a way I can get FSCK to run in recovery mode or somthing? Why not simply boot the system and let the Ubuntu OS do its magic? If the harddrive needs to be checked it will happen automatically. If the OS determines that such a check is not necessary at this time then why are you insisting on it?

---

### Post by oldos2er on 2009-11-14
> **jeb800e said:**
> Is there a way I can get FSCK to run in recovery mode or somthing?

** sudo touch /forcefsck** should cause fsck to run at next bootup. Not sure if it works in 9.10 or not.

---

### Post by Gnusboy on 2010-01-18
How do I use FSCK?

I just spent the better part of 2 hours looking for the answer to the same question. 

I read the "manual" I searched the forum, I read another "manual", I searched another forum. I searched "documentation" I searched Google and I read and I read and I read.
Confidence is low.

Here's what I have tried so far:

In terminal I entered fsck
the response was: util-linux-ng 2.16
I could not find what that meant - anywhere.

In terminal  under "Emergency Help" I entered fsck -p (automatic repair "no questions" )
The response was: command not found

I then tried e2fsck and got:

[-panyrcdfvtDFV] [-b superblock] [blocksize] ;-I inode _buffer_blocks] [-P process_inode_size] [-some sort of squiggly L l | -L bad_blocks_file] [-C fd] [-j external_journal] [-E extended-options] device

I then tried e3fsck and the response was:
Segmentation fault (core dumped)

I previously had Jaunty 9.04 installed which got screwed up during an attempted install of Mediabuntu. I do not know how or why.

I have burned CDs for both Jaunty and Karmic (2) run the all of the various installs which fail at one point or another and then the system locks.
I used a Live Cd to try the package manager upgrade - no luck. System locked up
I am in the system now with a live CD and can use the terminal the above e2fsck info is where I am at this point.

I am stuck. I don't care if I have to wipe the drive or throw it in the river. If there is a fix through Ubuntu I will try it first. 
I would appreciate it if someone could give an answer that a newbie can understand.

Thank you

P.S. I am not on that machine, which is why I can't post the output.

---

### Post by oldos2er on 2010-01-18
While you're booted from the LiveCD, open Gparted; I think it's in the menus System, Administration. Choose the partition you want to fsck, right-click on it and click 'Check', then 'Apply'. Make sure any partition you fsck is not mounted!

Or, when you're booted from a hard disk partition, run **sudo touch /forcefsck** in a terminal. This will cause fsck to run on next system boot.

---

### Post by CharlesA on 2010-01-18
> **Gnusboy said:**
> 
In terminal I entered fsck
the response was: util-linux-ng 2.16
I could not find what that meant - anywhere.

That's the package that fsck is included in.

If you need to run fsck you need to unmount the device:

sudo umount /mountpoint

then run this:

sudo fsck /dev/sdx -i

I use -i so that it doesn't "auto-repair" if there is any corruption.

---

### Post by lisati on 2010-01-18
> **oldos2er said:**
> ** sudo touch /forcefsck** should cause fsck to run at next bootup. Not sure if it works in 9.10 or not.
Seems to work on 9.04 64-bit server (needed to to damage noticed after overzealous copying of MP3 files and trash subsequently not emptying properly, my old machine currently hosting [website]("http://lisati.myftp.org/status")..... ouch)

edit: seems to have helped, will be "back to normal" in a couple of minutes

---

### Post by bodhi.zazen on 2010-01-19
Boot a live CD 

```
fsck -y /dev/sda1
```

[http://www.kernelhardware.org/how-should-run-fsck-linux-file-system/comment-page-1/](http://www.kernelhardware.org/how-should-run-fsck-linux-file-system/comment-page-1/)

On that link, "single user mode" in Ubuntu is called recovery mode (drop to a root shell).

If you get error messages, see

[http://adminschoice.com/repairing-unix-file-system-fsck](http://adminschoice.com/repairing-unix-file-system-fsck)

but to be honest, if the -y option does not fix the problem, and you are unfamiliar with fsck, you should probably post the error message back here.

---

