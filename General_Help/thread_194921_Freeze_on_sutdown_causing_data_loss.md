---
title: "Freeze on sutdown causing data loss"
date: 2006-06-12
forum: General Help
---

### Post by dbd on 2006-06-12
Hi,
I have a very annoying problem with Dapper (Kubuntu), every now and then when I attempt to shut down from KDE KDE appears to shutdown without problems, but then the screen goes black and the computer freezes without getting any further towards shutting down. This means I am forced to press the reset button, and when I reboot I have to use fsck, which comes up with many errors (which I say yes to fixing). 

Then when I get back to KDE many of my settings have gone, I always lose the basic KDE stuff (taskbar layout, desktop, style...) and also seem to lose a random mix of other stuff such as Kmail accounts, Amarok settings, Kopete settings, Kaddress book and sometimes my KDE Wallet gets corrupted.

This problem happened consistently with the Dapper beta (which I had upgraded to from Breezy), so I did a complete reinstall for the Dapper RC. And now the problem only happens every now and then. With the Dapper beta I found a workaround to avoid the problem - not shutting down when logged in, but instead using Ctrl+Alt+Backspace and then shutting down from kdm. But thats not really the way I want to be shutting down.

Please, please, PLEASE help! I had thread for the Dapper beta which wasn't replied to, and I've asked in IRC and recieved no help at all, and I've searched the forums for similar problems, and found nothing. So ANY ideas at all about how to fix the problem would be MUCH appreciated. Even just a tip where to ask (other than these forums and the #kubuntu IRC room) for help if no one on these forums can help would be useful. It's getting hard to recommend Ubuntu with such an annoying problem. And I have no idea what to do.

Thanks

---

### Post by blackjack6.21.91 on 2006-06-12
Look at the errors you recieve.  Do they say anything that might be of help?  No?  File a bug.

When you lose settings, I'll bet it's because of how the errors are fixed.  I doubt you would ever lose data on a manual shut down.  If it gets annoying, maybe start doing that.

Also, be sure your getting updates.  They fix ALOT.

fish and chips,
blackjack

---

### Post by dbd on 2006-06-12
I hadn't actually thought of looking much at the errors fsck was finding. I'll try having a look next time and googling them to see if I can make any sense from them.

My system is perfectly up to date, so thats not the problem. 

What sort of stuff should I include if I file a bug. Its not related to any particular program, and I have no way to consistently reproduce it even on my machine. So I doubt that just describing what I described above will help fix it. So is there anywhere (other than when running fsck) that I should look?

thanks :)

---

### Post by dbd on 2006-06-16
Ok, its happened again (took a while this time), luckily I don't seem to have lost too much this time. 
It happened after an update with adept, so that may be what caused the error. (It would explain why it almost always happened with the beta, because there were updates everyday) So I'm gonna see if the theory that it is caused by that proves true, then I can get a bug report out of it :D

Anyway, here is what happened (I decided to try and keep track of it this time), so if this makes any sense to anyone, let me know :)
It froze on shutdown after KDE had gone, as described above
Then it started booting, then started again at some point (not sure when, but when checking filesystems I think)
It rebooted
then said: /home not cleanly unmounted
multiply-claimed blocks in inode ....[inode info]
(it had 15 of these messages)
There are 15 nodes containedd multiply claimed blocks

Files /home/mezz/.kde/share/apps/kmail/mail/trash.index.ids (inde ...[inode info] has 1 multiply claimed block(s) shared with files .... (kmailrc file)

Unexpected inconsistency; Run fsck manually

[I run fsck]

/dev/hdb5 [one of my fat32 partitions] is mounted 
WARNING running e2fsck on a mounted filesystem may cause SEVERE filesystem damage do you want to continue. y/n   [no]
check aborted

difference between bootsector and its backup
[this error has never happened before, it may be because the kernel updated so the bootsector change too??? anyway, I chose 3 - no action] [this error came up another 2 times in a row, and I eneterd 3 for those two too]

clone multiply claimed blocks? [y]
[this error repeated loads of times for many different files, I said yes each time]

unattached inode
connect to lost+found? [y]
[I got a few of this error]

indoe 16200 ref count is 2 should be 1. Fix? [y]
[I also got a few of this error]

PAss 5 Checking group summary information
block bitmap differences [LOADS of numbers and stuff here, around 8 lines of them]
fix? [y]
[I got another one of these errors, but the second time there were far less numbers and stuff, I said yes both times]

Free blocks count wrong for group #0 fix? [y]
[I also got a few of this error]

***FILESYSTEM WAS MODIFIED*** (13.0% non-contiguous)
I press Ctrl+D
it coninues to boot ok (does not reboot) and then I log in and settings and stuff are gone again

Any info on what is going on would be greatly appreciated. And I'll see if it is an adept releated error.

Thanks

---

### Post by Gomek on 2006-08-12
Same exact thing happens to me.  Happens even when I haven't done an Adept upgrade, too, so I don't think it's that.  It's really, really annoying.  For some reason the files that love to corrupt themselves on my system are all of my Firefox settings and bookmarks.

What's the best way to run an fsck?  Any tips here?

Where would be the best place to look for error output from the freeze on shutdown?  Where would I find fsck or XFS recovery logs?

I never get the fsck options on startup, though.  I am using XFS, and all it does is run some type of automatic recovery.

---

### Post by Gomek on 2006-08-14
bump?

---

### Post by absurdist on 2006-08-15
Try upgrading your graphics card driver, or switching to proprietary driver.

If you're using intel graphics, with i810 driver, then this bug report might help:

[https://launchpad.net/bugs/34697](https://launchpad.net/bugs/34697)

Otherwise, what is your setup?  What computer or motherboard etc... 32 or 64 bit? What graphics card?

---

### Post by Gomek on 2006-08-20
I am using the fglrx driver currently with an ATI Radeon 9800 Pro.  I have an AMD64 processor and am using the k7 kernel.  I'm using an AOpen AK86-L mobo.

This is extremely annoying...

---

### Post by absurdist on 2006-08-20
In kubuntu you could try uncommenting the line (delete the #):

# TerminateServer=true

in /usr/share/config/kdm/kdmrc

Also, make sure you have the most up-to-date drivers from ATI:

[https://support.ati.com/ics/support/KBAnswer.asp?questionID=3380](https://support.ati.com/ics/support/KBAnswer.asp?questionID=3380)
How-to:  [http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)

And, check this bug report:

[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/30447](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/30447)

---

### Post by Gomek on 2006-08-21
[QUOTE=absurdist]In kubuntu you could try uncommenting the line (delete the #):

# TerminateServer=true

in /usr/share/config/kdm/kdmrc[/QUOTE]

Thanks for the helpful reply.  The file you fave me didn't exist, so a quick [COLOR="DarkSlateBlue"]sudo find / -name 'kdmrc'[/COLOR] pointed me towards [COLOR="DarkSlateBlue"]/etc/kde3/kdm/kdmrc[/COLOR].  I assume that's the equivalent.

Now, there isn't any [COLOR="DarkSlateBlue"]TerminateServer[/COLOR] option commented in this file.  After doing a little research, I figure I should simply add it to the [COLOR="DarkSlateBlue"][X-:*-Core][/COLOR] section?

I will try to see if enabling this will fix the problem before I use the drivers from their website.  Straying from the Debian packages has meant nothing but trouble for me in the past.

---

### Post by NiksaVel on 2006-08-24
hey guys... I'm having a very similar problem...  every now and then when I go to shut down my kubuntu i just get a blank screen and it hangs there so I have to keep the power button pressed to manually kill it.

Any solutions here?


I am using a laptop computer with ati graphics and fglrx, it's a fresh install.
I used to work with ubuntu gnome and it worked with NO PROBLEMS for about a month, then I decided to give kubuntu a try...


cya

---

### Post by Gomek on 2006-08-25
Yeah.  Try this:

Open [COLOR="DarkSlateBlue"]/etc/kde3/kdm/kdmrc[/COLOR] with administrative privileges.

Under the [COLOR="DarkSlateBlue"][X-:*-Core][/COLOR] section, add this line:
```
TerminateServer=true
```

This seems to work for me.

---

### Post by NiksaVel on 2006-08-25
seems to work on the first run... will report back if it doesnt

---

