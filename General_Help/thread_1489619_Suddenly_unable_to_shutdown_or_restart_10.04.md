---
title: "Suddenly unable to shutdown or restart 10.04"
date: 2010-05-21
forum: General Help
---

### Post by rbean44 on 2010-05-21
I installed 10.04 on my old Dell Inspiron 600m laptop.  After using it for about an hour, I was suddenly had no option to shutdown or restart the system when logged in on the main and only account.  The 'Shut Down' applet on my bar was greyed out and the shutdown option was missing from the system menu.  
 
I removed the 'Shut Down" applet and was unable to re-add it afterwards (wasn't a selection when adding to panel).  If I log off, selecting shutdown or restart from the login screen does nothing.
 
'Sudo shutdown now' will shut it down, though it won't power the system off; it just hangs on an all-white screen.
 
I saw other posts suggesting Open Office Quickstart was the culprit, though I am not running this.

---

### Post by charlie cat on 2010-05-21
In order to shut down and power off from the command line, you must run:
```
sudo shutdown -h now
```The -h command means "halt or power off after shutdown", according to shutdown --help.
For the general shutdown problem, I have several suggestions:
1. Check out [this thread]("http://ubuntuforums.org/showthread.php?t=1466589") (post 13 looks promising)
2. Make sure you didn't accidentally uninstall something at some time.
3. Make sure you didn't accidentally force-quit something at some time.
If nothing works, you can always add a menu option with the command "gksudo shutdown -h now", though having to be root to shutdown the computer could be annoying.

---

### Post by rbean44 on 2010-05-22
Yeah, I figured out the -h thing pretty quick.

I did get this working again for a bit; it seems the default and only user account was not a member of the 'video' or 'users' group, plus some others I think it should be a member of by default.  At one point previously I lost audio on the PC, and found that my account had been removed from the 'audio' group somehow.  Re-adding it to 'audio' fixed this.  I added the account to groups I think should have been default, and I regained shutdown ability for about a day.  It has since regressed, and even when I add my account to these groups, the account is removed upon next reboot.

It seems like this is a permissions issue, and something is modifying group memberships on a regular basis.

---

### Post by rbean44 on 2010-05-22
Yep...I confirmed...something is periodically removing my sole user account from:

uucp
floppy
dip
netdev
plugdev
<username>

I re-added my account to these groups with 'sudo adduser' and the ability to shutdown the system was restored.  Still unknown what is changing this.

---

### Post by rbean44 on 2010-05-22
Well...this occurred again and I checked all my group memberships and they haven't changed.  Guess the problem occurs sporadically.

---

### Post by charlie cat on 2010-05-22
Could this be a rare Linux virus at work?  I'd suggest running clamscan on all of your files (from / down).
Of course, the only webpage I could find with a similar problem described hasn't gotten any answers about it...  though still, look at [this thread]("http://ohioloco.ubuntuforums.org/showthread.php?p=7745340") (last post).
Also, is this a fresh install (from LiveCD) or an in-place upgrade, possibly carrying strange things from previous releases?
One more thing: make sure you have all updates installed from update-manager.

---

### Post by rbean44 on 2010-05-22
I'll look into the virus scan.  I installed from a the most current ISO via USB memory stick two days ago.  Everything in update manager is installed.

I also have odd behavior in the Users and Groups tool.  When I click on 'change' for account name or account type, nothing happens; plus when I click on 'advanced settings' no dialog comes up.

---

### Post by charlie cat on 2010-05-23
Between the time you had all groups and the time you lost some, did you run the Users and Groups program?  It sounds like adduser is working properly, so it's possibly an error in Users and Groups only.
You might get some useful output if you run Users and Groups from the terminal.  The command is 'users-admin'.  Also try running it under sudo or gksudo.

---

### Post by rbean44 on 2010-05-24
The problem has disappeared for now...expect it to occur again soon though.

---

### Post by SteveCube on 2010-06-08
I'm having the same issue.  Out of the blue I boot my computer to Ubuntu and I can't mount, listen to audio, or shutdown my PC.  I tried to change the settings for my user and group but I couldn't even get the login pop up for administration rights to change it.  I got that to work though using "gksudo users-admin"  After changing the permissions and adding my user to certain groups it pretty much fixed everything.  That worked for a few days and then now it's doing it again but all my user settings are the same.

Something fishy is going on here.  I'm not sure what to do now.

---

### Post by charlie cat on 2010-06-09
SteveCube, did you get any output when you ran users-admin at the terminal?  If so, can you post it here?
You may also want to check out /etc/groups in nautilus and check the last time it was modified.  If this time was after you last made changes in users-admin, we'll know something else is messing with it.
Also look at [this bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/287932").  It's from several OS's ago, so it may be out-of-date, but you may get something out of it.  According to some of the later comments, rbean44, the graying out of the buttons/inability to authenticate can be caused by using a login manager besides GDM.  If this is the case for you, that will solve one problem, though not the main one.

---

### Post by alexpage on 2010-06-19
I have the same issue on my laptop... once I log in, the telltale signs are that Shutdown and Restart are grayed-out, and I'm not able to adjust CPU Frequency Scaling through my panel.  This has happened about 5-10 times now, and a single restart has always cleared the issue.

---

