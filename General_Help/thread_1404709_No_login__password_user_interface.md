---
title: "No login / password user interface"
date: 2010-02-11
forum: General Help
---

### Post by greenewbie on 2010-02-11
My desktop won't come up automatically now on a hard disk of mine (see below for the Ubuntu version history). It does boot up with “Grub” etc; then the Ubuntu load up bar thing with the timer spinning around [I hope you can understand this technical language!] goes through ok but then instead of getting the user interface with the little boxes to enter my login and password, the whole screen is in black (as if it's in Terminal mode). This black screen then asks me for my login and password: when I entered them, it said:

[COLOR=DarkGreen]“Starting up......loading, please wait
19 + 0 records in
19 + 0 records out
kinit:** [COLOR=Black][followed by a load of technical stuff and a series of numbers][/COLOR]**
kinit: trying to resume from /dev/disk/ by-uuid/9b **[COLOR=Black][then a whole series of numbers][/COLOR]**
kinit: no resume image, doing normal boot.....
[/COLOR]
[COLOR=DarkGreen]Ubuntu 9.04 john-desktop tty1
john-desktop login: **[COLOR=Black][I entered it][/COLOR]**
Password: **[COLOR=Black][I entered it][/COLOR]**[/COLOR]

On one occasion only (among the dozens that I tried), I then got this ominous sounding message: [COLOR=DarkGreen]“There is 1 zombie process”.[/COLOR] [COLOR=Red]Is this something to worry about?![/COLOR]
It then gives details of my last log in (& some general info about Canonical etc).
It then finishes with [SIZE=3][COLOR=DarkGreen]john@john-desktop:~ $ “[/COLOR][/SIZE]

I've done my best to find answers to this problem but to no avail yet. The nearest I've found to date is as reported in the thread below (It's not possible to post to this now):

[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=347778[/COLOR]

I then tried as [COLOR=Blue]r4ik[/COLOR] suggested in the above thread:

[COLOR=Red]Log in with you're username and password and do a “sudo apt-get install gdm ubuntu-desktop”[/COLOR]

My screen then said:
[COLOR=DarkGreen]“Reading package lists.....done
Building dependency tree
Reading state information....done
gdm is already the newest version
ubuntu-desktop is already the newest version.
The following packages were automatically installed and are no longer required:
python-pexpect dar libdar64-4 pmount.
Use “apt-get autoremove” to remove them.”
[/COLOR]
I tried to see if my desktop would load ok, without doing the last instruction. It didn't, so I repeated the operation above and carried out the last instruction but it still didn't work. The desktop still didn't load and the last thing on the black screen was once again [SIZE=3][COLOR=DarkGreen]john@john-desktop:~ $[/COLOR][/SIZE]

I´d also like to mention that this problem suddenly developed one day several months ago when my hard disk had Ubuntu [COLOR=Red]8.10 Intrepid [/COLOR]installed on it. I decided to take it out of my normal computer and try it in my old computer (as I had been using this hard disk on it before without any problem); for some reason, it booted ALL THE WAY to my desktop, no problem. I then successfully upgraded it to Ubuntu [COLOR=Red]9.04 Jaunty [/COLOR](in the hope that this would solve the problem). The result was that: 
- on my old machine it would boot all the way to the desktop but then kick me out back to the login page, whenever I used the scroll bar!
- on my new machine, I haven't managed to get to the login/password interface even after dozens of attempts. I've tried a multitude of different options using my installation CDs for both 8.10 and 9.04 (trying the various Recovery Mode options etc).  

Yesterday I tried a fresh installation this time with Ubuntu [COLOR=Red]9.10 Karmic [/COLOR](this time using a CD-R, as opposed to the CD-RW, as I read that CD-Rs are more reliable). I could successfully use desktop applications with the trial option (indicating that there's nothing wrong with my machine; indeed I'm using Karmic on this machine as I write using a really ancient hard disk). But whenever I tried to install, it wouldn't go past the [COLOR=DarkGreen]“Prepare Partitions”[/COLOR] step: absolutely nothing would appear in the Partitions table; all options at the bottom of the screen [COLOR=DarkGreen](“New Partition Table”[/COLOR] etc) were greyed out and on clicking “forward”, this message would appear:

[SIZE=3][COLOR=DarkGreen]“No root file system is defined. Please correct this from the partitioning menu”.[/COLOR][/SIZE]

The reason why I would really like to get this hard disk up and running is that there are some files on it I would like to recover!  But if it's enormously difficult for a BEGINNER then I'd prefer to just completely wipe it and start again, if that is considerably easier (so at least I'd have this hard disk back).

Can anybody help please? :confused: 
Thanks in advance

---

### Post by spiderbatdad on 2010-02-11
>  john@john-desktop:~ $
 At this prompt try entering: ```
startx
```

---

### Post by greenewbie on 2010-02-12
Thanks Spiderbatdad

At the prompt [SIZE=3][COLOR=DarkGreen]john@john-desktop:~ $ “

[COLOR=Black][SIZE=2]I tried your suggestion:
[/SIZE][/COLOR][/COLOR][/SIZE]     Code:
     startx 
[SIZE=3][COLOR=DarkGreen][COLOR=Black][SIZE=2]I literally just typed[COLOR=DarkGreen] [COLOR=Red]startx [/COLOR][/COLOR]immediately after this prompt; also [COLOR=Red]sudo startx[/COLOR] (nothing ventured, nothing gained I thought!). Neither worked. I got a screenful of technical stuff finishing with these lines:

[COLOR=DarkGreen]Closing log giving up
xinit: no such file or directory (errno 2): unable to connect to X server
xinit: no such process (errno 3): server error
[/COLOR][/SIZE][/COLOR][/COLOR][/SIZE][SIZE=2][COLOR=DarkGreen]john@john-desktop:~ $ “[/COLOR][/SIZE]

[COLOR=Black]BTW I don't know what this server stuff is about, as I don't have one (no doubt it would be way beyond my know how anyway). Another comment: I'm the only person who has ever used my computer[/COLOR] and hard disks, so I'm hoping this means I'm the "root user"!

Any other ideas please? :confused:

PS Could the problem be a virus? I don't actually have a virus checker on either of my Ubuntu disks. I haven't heard much about viruses with Ubuntu but I'll look it up in the forums

---

