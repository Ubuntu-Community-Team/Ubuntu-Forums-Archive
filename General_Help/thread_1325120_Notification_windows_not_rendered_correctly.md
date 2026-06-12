---
title: "Notification windows not rendered correctly"
date: 2009-11-13
forum: General Help
---

### Post by zainka on 2009-11-13
.. Well, I am not sure if the word render should be used, but I got a problem when uppgrading to version 9.10 of xubuntu, from v9.04. 

All notifications windows only show a grey screen with some colored lines in it. I Did not have any such problems when running 9.04.

First i thought that this had to do withe me experimenting to find the windowmanager that suited me best. So on the same machine I had ubuntu gnome, xfce (as in xubuntu) and kde, aswell as a couple of others. I had also tweaked the systems settings a bit. However, the problem, arised only when uppgrading to 9.10. I thought I had messed my system up so I deside to reinstall everything completely. I.e. a clean installation of Xubuntu 9.10.

The same problems was still there.

Any idea why this is so? I have included a couple of screen shots. The first showing notification when network is detected, the second showing a notification given when installing eagle from cadsoft.de.

Are Xubuntu missing som libs? Atleast network notifications should be visible...


Thanks in advance
Breg
Vidar

---

### Post by zainka on 2009-11-13
Okay, so I was able to solve it after a while, well, only partial. It seems like the notification daemon has failed somehow during installation, if installed at all (bug? or machineware incompatibility?? After all I had the same problem when installing from scratch as when installing as an upgrade). However I did this to atleast make the pop up notifications work, but installation notifications does still mess up:

> sudo apt-get install xfce4-notifyd

After an reboot I was able to see notifications correctly.

One also now have an new option under xfce settings for notification tweaks

BUT! IT IS NOT SOLVED YET, 
Anyone have any ideas how to make rest of the daemons work?


have a :popcorn:

---

### Post by crjim on 2009-11-16
thank you [zainka]("http://swiss.ubuntuforums.org/member.php?u=68341")... had the same problem with the pop up notifications and the xfce install did the trick... also had same problem with menu items on open office but switched my theme in appearances to human from the custom theme i had been using and that cleared it up... 

thanks again... jim

---

### Post by zainka on 2009-11-17
Hi

Glad I could help. 

However I do no longer beleive this is caused by something that has gone wrong during installation. This is a bug in new 9.10 version. I will fill out a bug report when I understand more and reffere to this thread and also update this thread with refference to the bug report filled for your refference.

However, CRJIM, are you able to open and see the contents of the system monitor menue? In terminal run command **gnome-system-monitor** This may also have its output destroyed


EDIT:
Hi again. I found that someone has filled an bug report already for this issue but it has not been assigned to anyone yet. However you can follow the bug status here [https://bugs.launchpad.net/ubuntu/+bug/474134]("https://bugs.launchpad.net/ubuntu/+bug/474134").

If you have ADDITIONAL information pleas log in and fill in. You could also log in (should be able to use same password and user as in the forums I think(!)). Then you will have an option almost at top to click on a link named "Yes, This affects me too" or something.

WE ARE NOT ALONE 


Breg
Vidar

---

### Post by zainka on 2009-11-18
Okay, Now I am confused. I  Thought that I could not live with this problem for long and therefor desided to install :

> sudo apt-get install ubuntu-desktop

Thus having gnome suport. 

However, Even Gnome have this problem with unreadable notifications. If I dont make this working soon then I will have revert to version 9.04 Jaunty again, as Karmic does not seem to make the job done.


-----
I also tried to figure out how to remove the XUBUNTU tag in title since it no longer is related to XUBUNTU only (or is there other diferences among XUBUNTU 9.10 and UBUNTU 9.10 other than the window managers? Anything that may mess up my notification windows`???)


Thanks in advance for any reply

---

### Post by P4man on 2009-11-18
it looks like a problem with transparency and therefore related to your videocard/driver. Might help if you told us which one you have

---

### Post by zainka on 2009-11-18
Hmm, yes maybe. 

My HW is an Compaq Evo n800c for which use <snip> ATI Mobility Radeon 7500, 64-bit video graphics with 32- or 64-MB VRAM for increased color depth and graphics performance.

Mor info on my HW can be found here:
[http://h18000.www1.hp.com/products/quickspecs/11344_na/11344_na.HTML]("http://h18000.www1.hp.com/products/quickspecs/11344_na/11344_na.HTML")

I will try the following as soon I get hands on my laptop again (its at work and I am at home) : [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

EDIT
Hi, a small edit here. I seem to have the correct driver installed so prob. must be something else. 

```
$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]

```



Thanks in advance
Breg
Vidar

---

### Post by zainka on 2009-11-18
Sigh

After spent evening work trying to solve this s.... I will by the end of tomorrow revert to 9.04 since this is atleast working perfectly. No hard feelings but there is limits of how long one should try to have these things working. 

I really cant understand what the difference between 9.04 and 9.10 should have this impact but still , as it is now, it is useless to me.

I understand it have to do something with HW incompatibility since there is wery few of us having this problem. 

Let me finalize this post with the words flying out of my speakers right now, served by Pink floyd, 

Jaunty, how I wish you where here!

:popcorn: (again)

Godnight

---

### Post by dakaujunk on 2009-11-18
Thanks zainka. I too have this mysterious issue on Xubuntu 9.10 running on a thinkpad t42 with ATI Radeon Mobility 7500. Added a comment to the bug report. 

I dont want to go back to 9.04. Seems some are able to fix this by adding a xorg.conf from older versions (8.10). I will post if i find any fixes to this.

---

### Post by zainka on 2009-11-19
Great! I have also another thread in xfce forum up and running now, though we should try to keep al information iside this thread.

However, you may follow this second thread here.: [http://forum.xfce.org/index.php?topic=5277.0](http://forum.xfce.org/index.php?topic=5277.0)


For the audience, i will repeat what has been written in Xfce forum (more or less...):

There was a question if diferent themes may appear diferent. I have tried several themes and combination with diferent styles. 

As crjim mentioned he had to switch to human theme, but that did not make any diference to my problm.

I also wanted to check for clues in available logs, as in /var/log/ , buty as I do not know what to look for that is rather pointless activity. I did do a search though and found that in kern.log I had several listing of : ```

nnn kernel: [105538.792809] [drm:radeon_cp_reset] *ERROR radeon_cp_reset called without lock held, held -214783648 owner ef9a7600 ef9a7cc0
nnn kernel: [105538.792809] [drm:radeon_cp_start] *ERROR radeon_cp_start called without lock held, held -214783648 owner ef9a7600 ef9a7cc0
nnn kernel: [105538.792809] [drm:radeon_cp_idle] *ERROR radeon_cp_idle called without lock held, held -214783648 owner ef9a7600 ef9a7cc0
```

I do not know if it has anything to do with this problem indicating that the driver is not working properly or not.

---

### Post by P4man on 2009-11-19
File a bug report. Sounds like its a regression from this bug:
[http://bugs.freedesktop.org/show_bug.cgi?id=7128](http://bugs.freedesktop.org/show_bug.cgi?id=7128)

---

### Post by zainka on 2009-11-19
There is already a bug filled and  you may find a link earlier in this thread.

EDIT:
Thought I should provide this output. 

I get the following terminal output when installing eagle.
> nnn@nnn:~$ sudo ./Downloads/eagle-lin-5.6.0.run 
[sudo] password for nnn: 
X Error: BadMatch (invalid parameter attributes) 8
  Extension:    149 (RENDER)
  Minor opcode: 4 (RenderCreatePicture)
  Resource id:  0x26


After this output the installation window opens up, unreadable.


EDIT AGAIN:

Above error message is related to this thread aswell [http://ubuntuforums.org/showthread.php?t=1148340](http://ubuntuforums.org/showthread.php?t=1148340)
and launchpad [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898)

---

### Post by zainka on 2009-11-19
There is another thread discussing the problem and which even may have a solution:


[http://ubuntuforums.org/showthread.php?p=8330252#post8330252](http://ubuntuforums.org/showthread.php?p=8330252#post8330252)

EDIT:
By information given in thread above I was finaly able to solve my problem, I still do not understand why 9.10 should be so picky and mess everything up and my big fear is that at next upgrade New problems will arise. Guess I will wait longer before jumping onto an upgrade like this then.

This is was helped me out. I had to create the xorg.conf file since it did not exist from before. In this I added :
```
# To avoid unreadable windows.
Section "Device"
	Identifier	"Radeon7500"
	Driver	"ati"
	BusID	"PCI:1:0:0"
	Option	"RenderAccel" "false"
EndSection
```

Note that these where the setting working for me. However, what I do not like is that the renedering accelerator now has been turned of and things may get slower. So this is considered a workaround and not a fix in my opinion. Apperantly the xorg driver does not support radeon 7500 well enough. Maybe in the future

---

