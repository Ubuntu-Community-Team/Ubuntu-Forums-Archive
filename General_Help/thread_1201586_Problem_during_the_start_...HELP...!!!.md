---
title: "Problem during the start ...HELP...!!!"
date: 2009-07-01
forum: General Help
---

### Post by Alexandros_ on 2009-07-01
While i was restart my pc...appeared a message..."checking disk"...It stop at 68% and appeared a black screen that say...


[B]Error reading block 76223608 (Attempt to read block from filesystem resulted in short read) 
while reading indirect blocks of inode 19054630.

/dev/sdb1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
     (i.e., without -a or -p options)
fsck died with exit status 4
                                                                                                                    [ [COLOR=#ff0000]fail[/COLOR] ]
*An automic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
*The root filesystem is currently mounted in read only mode.
A maintenance shell will now be started.
After performing system maintenance press CONTROL-D
to terminate the maintenance shell and restart the system.
bash: no job control in this shell
root@...-desktop:~#[/B]

---

### Post by x22 on 2009-07-01
how about doing what the message says, i.e.

"fsck /dev/sdb1"

then wait for further instructions.  Then <ctrl><D>.

---

### Post by Alexandros_ on 2009-07-01
OK...I solved the problem...

Run live cd --> Terminal --> "fsck /dev/sdb1" 

It works X22...thanks...:p

Thanks "Mr Teo"...:p

---

### Post by greenewbie on 2009-07-06
I have EXACTLY the same problem as Alexandros, except my problem arises on [COLOR=DarkGreen]/dev/sda1[/COLOR]. and I use Ubuntu 8.10 

To date I haven't been able to resolve the problem, either by writing [COLOR=Red]fsck/dev/sda1 [/COLOR]after [COLOR=Red]root@john-desktop [/COLOR](at the bottom of the black page after all the references to the manual fsck) or by starting up Terminal using a Live CD (which by the way is working perfectly, including internet access etc).  In both cases I get "no such file or directory" etc.
On the assumption that starting up a Live CD is the best way forward, can I resolve the problem via the Terminal as a "Live session user" (ie without reinstalling Ubuntu on my hard drive)?  If so, would I perhaps change name from the default "[COLOR=Red]ubuntu@ubuntu[/COLOR]" appearing on the Terminal screen to [COLOR=Red]john@john-desktop[/COLOR] (by altering the "Set Title" in the menu)?
If I reinstalled Ubuntu 8.04 on my hard drive, would I lose all my files, documents, Thunderbird emails etc?  Please note that I currently have **Ubuntu 8.10** installed on my hard drive but I only have a Live CD for **8.04** (Gutsy Gibbon LTS).......does this make any difference to the problem?

Although I've used Ubuntu for some time, I know NOTHING about technical stuff.  So I would be very grateful for answers that a NON-technical guy can understand!!
Thanks in advance.
John

---

### Post by michy99 on 2009-07-06
In your post it looks like you entered ```
fsck/dev/sda1
```but it should be ```
fsck /dev/sda1
```(Note the space) But maybe that was a typo.

If you use a Live CD, your username will be ubuntu and your machine will be named ubuntu, so ubuntu@ubuntu is as it should be. You do not need to change it.

---

### Post by greenewbie on 2009-07-06
Thanks very much for your help, Michy99 .  I didn't spot the gap needed between fsck and /dev.  The problem now is that in my Terminal (with the heading ubuntu@ubuntu), after entering [COLOR=#ff0000]fsck /dev/sda1[/COLOR], I get -  
 [COLOR=#008000]" fsck 1.40.8 (13-Mar-2008) [/COLOR] 
 [COLOR=#008000]e2fsck 1.40.8 (13-Mar-2008) [/COLOR] 
 [COLOR=#008000]fsck.ext2: Permission denied while trying to open /dev/sda1 [/COLOR] 
 [COLOR=#008000]You must have r/w access to the filesystem or be root "[/COLOR]
 

 I'm the only person who uses my computer, so I AM the administrator etc, apparently not able to hack my way into my own computer.........!

At the top of the Terminal it says 
[COLOR=#008000]"To run a command as administrator (user "root"), use "sudo <command>". [/COLOR] 
 [COLOR=#008000]See "man sudo_root" for details."[/COLOR]  I had a go but with my clueless know-how, I drew a blank on that one.
 

 I also tried entering fsck /dev/sda1 on the black page when the Ubuntu load up gets stuck (in my case at 59% due to **"unclean shutdown, checking drives"** ), the automatic fsck fails etc (as reported above).  This time the command WAS recognised but I just got a load of error messages.
 

 Does anybody have any recommendations please?  EG Is it better to plod on via the Terminal using my Live CD or NOT use the CD, let Ubuntu fail to load up and try entering different commands that way?
 

 By the way if anybody suggests the "black screen method" (I'm afraid my Ubuntu vocab is rather limited!), how can you copy all the stuff the computer churns out on it (like Alexandros did above), so that I can show you all the error messages it sends?
 

 Thanks in advance.

---

### Post by t0p on 2009-07-06
> **greenewbie said:**
> The problem now is that in my Terminal (with the heading ubuntu@ubuntu), after entering [COLOR=#ff0000]fsck /dev/sda1[/COLOR], I get -  
 [COLOR=#008000]" fsck 1.40.8 (13-Mar-2008) [/COLOR] 
 [COLOR=#008000]e2fsck 1.40.8 (13-Mar-2008) [/COLOR] 
 [COLOR=#008000]fsck.ext2: Permission denied while trying to open /dev/sda1 [/COLOR] 
 [COLOR=#008000]You must have r/w access to the filesystem or be root "[/COLOR]
 

 I'm the only person who uses my computer, so I AM the administrator etc, apparently not able to hack my way into my own computer.........!

At the top of the Terminal it says 
[COLOR=#008000]"To run a command as administrator (user "root"), use "sudo <command>". [/COLOR] 
 [COLOR=#008000]See "man sudo_root" for details."[/COLOR]  I had a go but with my clueless know-how, I drew a blank on that one.
 

Okay, I can see 2 possible reasons for the problem when trying commands from the Live CD:

1. It says you need r/w access to the file system.  Have you mounted the file system?  When you run from live CD, the file system (ie the hard disk) is by default unmounted.  You can mount it by using the gui file manager to navigate to /media.  There you'll see a file system called something like "60 GB volume" (depends on the size of the hard disk of course) or maybe just "disk".  Right-click on it and select to mount it.  Then try your commands again.

2.  Perhaps you haven't used **sudo** properly.  You need to enter the command prefixed with "sudo".  Like this:

```
sudo fsck /dev/sda1
```

You'll be prompted for your password.  Type it in - you won't see what you're typing but that is normal - and press Enter.  The command should work then.

---

### Post by greenewbie on 2009-09-15
Thanks very much "t0p" for giving me the key to solving the problem! 

I didn't know that the command had to be prefixed by "sudo", as you told me below:

2.  Perhaps you haven't used **sudo** properly.  You need to enter the command prefixed with "sudo".  Like this:

 	Code:
 	sudo fsck /dev/sda1 
I worked my way through it all and was delighted to get my hard disk up and running!
Thanks to "Michy99" too :KS

---

