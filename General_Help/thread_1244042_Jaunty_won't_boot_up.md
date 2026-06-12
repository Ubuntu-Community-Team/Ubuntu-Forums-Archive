---
title: "Jaunty won't boot up"
date: 2009-08-19
forum: General Help
---

### Post by AMV_Ph34r on 2009-08-19
I just now started up my desktop computer, which has Jaunty installed on it. It started out fine, showing the Grub loading screen, followed by the bootloader. I selected kernel 2.6.28-15-generic to boot, and got the usual "Boot from (hd0,0) ext3 blah blah" message, and then the Ubuntu splash screen loaderbar. For some reason, it was off centered. After a couple seconds, the screen went blank, and a cursor started flashing in the top-left corner of the screen. About half a minute later, I get "* Reading files needed to boot...", then the boot diagnostic screen that shows up when the splash fails, and then... nothing. The computer sits there, cursor flashing, and doesn't boot. The only change to the computer I made from Startup-Manager recently was changing the boot splash back to the default Ubuntu splash (I was previously using a custom one). Now I can't get it to boot at all. I tried recovery mode, but ended up in a similar situation. It begins to boot, and then stops. How can I get it to boot again without reformatting the hard drive or deleting any of my files?

---

### Post by Strongman332 on 2009-08-19
use the boot in safe graphics mode option

---

### Post by AMV_Ph34r on 2009-08-19
How would I do that? Is it a kernel I boot from? The only boot options I see are kernels 2.6.28-(11-15)-generic, and the respective recovery modes, as well as memtest86+.

---

### Post by AMV_Ph34r on 2009-08-19
I should probably also mention that the last thing it says right before it freezes up is:
"* Starting system message bus dbus                                                                [OK]"
I'm not sure what it's trying to do after it starts dbus, but whatever that is, that's where the problem is. But I'm not sure how to fix it.

---

### Post by MaxIBoy on 2009-08-19
Okay, boot off the nearest convenient liveCD or liveUSB. Pull up a terminal. Change to the root directory of the installation in question. Then change to the "/etc/" directory of the broken installation. Then post the output of these commands:
```
ls ./rcS.d
ls ./rc2.d
```



Just so you know, these files are all symbolic links (AKA symlinks, they're almost like "shortcuts") to the "init scripts" in the /etc/init.d directory. Each init-script contains all the tools needed to start, reload, or stop a given daemon (a daemon is a background process which idles until it is needed; for example, one of the daemons sits around doing nothing until you want to print something.) Which symlinks happen to be in rcS.d and rc2.d tell the system which daemons belong in runlevels S and 2, respectively, and in what order to start them. All systems boot up starting in runlevel S, before moving onto a different runlevel. In Debian systems, runlevel 1 is recovery mode, runlevel 2 is the normal default mode. The symlinks in a runlevel directory are named in such a way as to encode the order they should be run. If the name of the symlink starts in K, the process will be killed (if it is already running) when entering that runlevel. If the name starts in S, the process will be started. The numbers which appear after K or S determine the order. So S89cron starts after S50cups, and K10jackd gets killed after K01upsplash, for example. (My initscripts are heavily customized, and are most likely different from yours.)

I always like to explain the technical rationale behind any console commands I ask someone to run. :)

---

### Post by rahrahmah on 2009-08-19
I am also having trouble with by boot up. I'm also running jaunty. I don't have the same problem, but my monitor turns itself off at about the point where yours starts freaking out, so it's possible that it's a similar error and just different hardware responses. I hope some help can be found, since I'm not getting a lot of responses in my thread. :(

---

### Post by AMV_Ph34r on 2009-08-19
OK. here's the output.
[http://i84.servimg.com/u/f84/12/04/26/14/screen10.png](http://i84.servimg.com/u/f84/12/04/26/14/screen10.png)

because the forums removed the tabbed spacing, i had to make a screenshot.

And thanks for explaining it, MaxIBoy. I like to know why I'm doing what I am to fix my comp. :)

---

### Post by MaxIBoy on 2009-08-19
Okay, it appears that either dbus, apport, or hotkey-setup is messing up your boot process.

Could you please also post the output of "ls ./rc1.d" too (forgot to ask before, sorry.) Since you're telling me that runlevel 1 (recovery mode) is failing as well.

---

### Post by AMV_Ph34r on 2009-08-19
OK, here it is:
[http://i84.servimg.com/u/f84/12/04/26/14/screen11.png](http://i84.servimg.com/u/f84/12/04/26/14/screen11.png)

---

### Post by MaxIBoy on 2009-08-19
Okay, remember when I told you that runlevel 1 was recovery mode? As far as I know, recovery mode does not need dbus to run. Therefore, we can try disabling it in runlevel 1 and seeing if we can at least get recovery mode to boot properly.

The easiest way to do this:

[LIST]
[*]First, make sure that your "broken" installation's filesystem is mounted as read-write within the liveCD environment. I believe it is read-write by default but only root can mess with it.
[*]Change to the rc1.d directory.
[*]To disable a daemon, change the S to a K. Then change the number to 100-(the current number.) So S88dbus becomes K12dbus. 
```
sudo mv S88dbus K12dbus
``` There is no default password in the liveCD environment, just hit enter when asked for one.
[/LIST]
Now, reboot and see if you can at least boot into recovery mode.


EDIT: It's looking like startupmanager messed with your initscripts when you used it. At least, that's what I think happened.

---

### Post by AMV_Ph34r on 2009-08-19
Do you mean changed K88dbus to S12dbus? There's no S88dbus in the folder.

---

### Post by MaxIBoy on 2009-08-19
Uh, whoops. Didn't read that carefully. :roll:

So, yeah, it turns out dbus is disabled in runlevel 1 after all. False alarm, sorry. 

Could you boot into recovery mode and tell me what the last thing it says is before it fails?

---

### Post by AMV_Ph34r on 2009-08-19
I booted into recovery mode and selected "resume boot". I assume that's what you wanted me to do.
This is the last line that it prints before freezing up:
"* Starting system message bus dbus[COLOR=White]-------------------------------------------------------------------[COLOR=Black][OK]"[/COLOR][/COLOR]

---

### Post by MaxIBoy on 2009-08-19
OH! So you can get to that menu all right?

Okay, I was misunderstanding you. "Resume boot" just resumes the normal boot process (i.e. goes into runlevel 2.) If you can see that menu at all, runlevel 1 is working perfectly. This narrows down the problem somewhat. 


I think, since it shows [OK] after "starting dbus," that dbus might not be the problem. The two initscripts which directly follow dbus, apport and hotkey-setup, are the most likely suspects here. Both are basically nonessential. Apport is the little pop-up which appears, offering to file a bug report when something crashes. hotkey-setup handles the "special" laptop keys. Both can be safely disabled for experimental purposes. Try disabling them in the way I described in a previous post.

EDIT: in fact, I think hotkey-setup might depend on HAL (hardware abstraction layer) having been started before it, since HAL is partly responsible for detecting "special" buttons in the first place. I don't have hotkey-setup installed so I can't examine the initscript to be sure. Go ahead and disable those, tell me if you can boot up properly after that.

---

### Post by AMV_Ph34r on 2009-08-19
I tried disabling HAL, apport and hotkey-setup, and it still won't boot up. It gets to the same place that it did before, and freezes up again. Any idea what else might be causing the problem?

---

### Post by MaxIBoy on 2009-08-19
Try disabling apport and re-enabling HAL.

---

### Post by AMV_Ph34r on 2009-08-19
I tried that too. Still nothing. Maybe I renamed the files incorrectly? I changed S20apport to K80apport, S20hotkey-setup to K80hotkey-setup, and S24hal to K76hal. (I think it was S24).

EDIT: I tried booting to the LiveCD again, and browsed to /etc/rc2.d, and the files I disabled were enabled again. I think for some reason Ubuntu re-enabled them when I shut down. Any idea why?

EDIT (again): Whoops... I was accidentally renaming the files on the LiveCD, not the hard drive. I renamed all three files on the hard drive, and it still didn't work. I'm going to do what you said and re-enable HAL while keeping apport disabled. Should I also keep hotkey-setup disabled?

the third EDIT: I re-enabled HAL, and still nothing's changed.

---

### Post by tgalati4 on 2009-08-19
Did you perform an update recently?  Sounds similar to this problem:

[http://ubuntuforums.org/showthread.php?t=1244576](http://ubuntuforums.org/showthread.php?t=1244576)

---

### Post by AMV_Ph34r on 2009-08-19
I don't think that's the same problem that I'm having. I've been running kernel 2.6.28.15 for a while without any problems, and my issue persists even when I switch kernels.

---

### Post by MaxIBoy on 2009-08-19
Okay, try this:

Highlight the normal boot option in grub, and hit "e" to edit it. (Your edits will not be saved permanently.) Edit the first line you see on the new screen which appears, and if it says "quiet" then remove that word. Also add "nosplash" if it wasn't already there.  This should provide extra useful output.

Also, I can't remember directly and don't want to reboot, does the recovery mode menu provide any kind of option to try to repair the boot process?

---

### Post by AMV_Ph34r on 2009-08-19
I tried deleting "quiet" and adding "nosplash", but when I hit "b" to boot, the computer restarted. Each time I try this, the same thing happens.

To answer your question, there isn't an option to directly repair the boot process, but there is one to update GRUB. There's also fsck, dpkg, and xfix options, but those also don't directly relate to booting.

---

### Post by MaxIBoy on 2009-08-19
Okay, your computer flat-out should not reboot when that is happening. Weird. 


Try editing your grub menu.lst from a liveCD environment and putting it there instead.

Also, look in /var/log on your hard drive filesystem, what do you see there? There are often crash reports and so on which appear.

---

### Post by AMV_Ph34r on 2009-08-20
Yeah, I figured there was a problem there, if it was restarting. I should mention that this computer, while most of the components are new, the motherboard and processor are old, and the MB's BIOS is corrupted. Not to the point where it is unusable, but sometimes weird stuff happens.

I edited menu.lst, and this time it didn't restart. However, though it showed more information on the boot diagnostic screen than last time, it still stops at the same spot, and the bottom quarter of the screen looks the same.

I also checked /var/log, but I wasn't sure exactly what to look for. I didn't find anything that openly said "crash log" or anything.

---

### Post by AMV_Ph34r on 2009-08-20
Yeah, I figured there was a problem there, if it was restarting. I should mention that this computer, while most of the components are new, the motherboard and processor are old, and the MB's BIOS is corrupted. Not to the point where it is unusable, but sometimes weird stuff happens.

I edited menu.lst, and this time it didn't restart. However, though it showed more information on the boot diagnostic screen than last time, it still stops at the same spot, and the bottom quarter of the screen looks the same.

I also checked /var/log, but I wasn't sure exactly what to look for. I didn't find anything that openly said "crash log" or anything.

---

### Post by AMV_Ph34r on 2009-08-22
I still can't get it to work, after trying multiple different things. If I copy all the contents of the hard drive to a second hard drive, then re-install ubuntu, will I be able to get all my files/programs/settings back by copying them back onto the first hard drive? I could copy everything but the folders that are causing the problem. Would this work?

---

### Post by AMV_Ph34r on 2009-08-24
MaxiBoy? You still there?

I still haven't made any progress.

---

