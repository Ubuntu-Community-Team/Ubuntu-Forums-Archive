---
title: "Unlock keyring issue"
date: 2010-06-09
forum: General Help
---

### Post by leviathan8 on 2010-06-09
[B]Hello dear Ubuntu community. I'm a newbie around this forum, but i'm an older ubuntu linux user. 
Everything worked fine until today.[/B]
**I made some compiz configs, an sudo apt-get upgrade (distro upgrade)**, [B]and then I rebooted so the changes can make their effects.
Well everything is good, until a little window pops up, requesting my keyring. Ok, nothing wrong here, except that I can't press ANYTHING. I cannot use my keyboard to type in my password, can't move mouse, can't do anything.
I need help regarding this issue. Any solutions are welcome. Thanks for your time reading this.

Also, here is a pic, maybe helps a bit:
[IMG]http://i46.tinypic.com/acvexy.jpg[/IMG]
[/B]

---

### Post by leviathan8 on 2010-06-09
**Bump             .**

---

### Post by leviathan8 on 2010-06-09
**Bump once again. Any ideas?**

---

### Post by germanix on 2010-06-09
Do a new start and see if the problem persists. Cannot get worse than it already is.

---

### Post by leviathan8 on 2010-06-09
[B]I rebooted over 10 times, I tried even to install different programs, edit codes (as followed by tutorial), but absolutely nothing. Believe me I would give my heart to make ubuntu work again. Maybe a dev could help me. I think it can't be worse than this :p

Note: I made this by CTRL + ALT + F8. That got me into the prompt screen. Also tried rebooting by Alt + Prtscn + b.[/B]

---

### Post by germanix on 2010-06-09
Well friend I sympathise with your problem but as your own signature says:
Actions do have a reaction and it seems to me that your actions have put you in some hot water.
You mention a distro upgrade that you made. Perhaps you could be somewhat more specific in what you upgraded from and to what? Or was this a completely new install? Upgrading from an older version to a newer can sometimes cause a problem. better is always a new install.
I realise it is now to late for that and that you have a problem that needs to be fixed. You would probably have to boot up in safe mode and do some changes but unfortunately I am no genius with such matters to be able to help you myself with this specific issue.
Lets hope for your sake that some expert take pity and helps.
May the force be with you!

---

### Post by leviathan8 on 2010-06-09
> **germanix said:**
> Well friend I sympathise with your problem but as your own signature says:
Actions do have a reaction and it seems to me that your actions have put you in some hot water.
You mention a distro upgrade that you made. Perhaps you could be somewhat more specific in what you upgraded from and to what? Or was this a completely new install? Upgrading from an older version to a newer can sometimes cause a problem. better is always a new install.
I realise it is now to late for that and that you have a problem that needs to be fixed. You would probably have to boot up in safe mode and do some changes but unfortunately I am no genius with such matters to be able to help you myself with this specific issue.
Lets hope for your sake that some expert take pity and helps.
May the force be with you!

**I just made a update. I forgot to mention that when I updated from the "Update Manager"** **program, ~3-4 packages couldn't be downloaded because the FTP server couldn't be accessed. I tried later after that, and made the update directly from the terminal. Hopefully, it worked, but after the reboot, the  keyring issue came up. From this point I couldn't do anything. I tried starting ubuntu in Recovery mode, made a dpkg check, some other memtests, and then booted ubuntu normally. All this, still useless.**

---

### Post by germanix on 2010-06-09
When all else fails:  Boot from the live disk and back up your files to a external drive if you have not already done that and do a new install. A hassle I know but probably much quicker than waiting for the right solution to come along.

---

### Post by leviathan8 on 2010-06-09
**I even booted with live cd, to make some checks on the chroot, but couldn't find anything wrong - or didn't figured it out. Anyway, if no solution will come up, distro reinstall is the only way to solve this. Anyway, still hoping that someone will figure out something. Until then, patience. Time will tell.**

---

### Post by diagram30 on 2010-06-09
> **germanix said:**
> When all else fails:  Boot from the live disk and back up your files to a external drive if you have not already done that and do a new install. A hassle I know but probably much quicker than waiting for the right solution to come along.

Why would you ever recommend anyone who's only got a broken X server or any script running after the X server starts up to reinstall? His problem lies in something his gnome-session tries running and obviously asks for elevated privileges, but his input is apparently not being taken into consideration.
Best bet for him would be rebooting into recovery mode, then starting the X server via 'startx' versus the gdm way (I'm assuming he has gdm) and just running gnome-session-properties to stop whatever program could be asking for elevated privileges from running right after the user logs into their gnome session.

---

### Post by leviathan8 on 2010-06-09
> **diagram30 said:**
> Why would you ever recommend anyone who's only got a broken X server or any script running after the X server starts up to reinstall? His problem lies in something his gnome-session tries running and obviously asks for elevated privileges, but his input is apparently not being taken into consideration.
Best bet for him would be rebooting into recovery mode, then starting the X server via 'startx' versus the gdm way (I'm assuming he has gdm) and just running gnome-session-properties to stop whatever program could be asking for elevated privileges from running right after the user logs into their gnome session.

[B]That could be a solution. Can you please explain these more detailed?
I want exactly the steps to be made. I would really appreciate this. Thank you.
[/B]

---

### Post by germanix on 2010-06-09
> **diagram30 said:**
> Why would you ever recommend anyone who's only got a broken X server or any script running after the X server starts up to reinstall? His problem lies in something his gnome-session tries running and obviously asks for elevated privileges, but his input is apparently not being taken into consideration.
Best bet for him would be rebooting into recovery mode, then starting the X server via 'startx' versus the gdm way (I'm assuming he has gdm) and just running gnome-session-properties to stop whatever program could be asking for elevated privileges from running right after the user logs into their gnome session.
Well that is very nice of you to assist in this matter. i did say if all else fails and he gets no further help from anyone in this forum. Now you have given some advice but unfortunately in such a technical gibberish that a newbie will certainly not be able to understand. I am sure your help is appreciated but if you post and offer help to newbies in the forum you should consider explaining it in such a way that newbies can understand and follow. I have been using Ubuntu for two years now and have read books on the subject but I have no idea what you mean and what I would now have to exactly do to solve the problem. I am sure the poster of this problem probably has the same problem.

---

### Post by germanix on 2010-06-09
Found this in one of the forums. May be worth a try. 


Happily, true system "lockups" or "crashes" are pretty rare with Linux, but apparent lockups in which the screen goes black and/or the mouse and keyboard stop responding can happen - that is actually a crash of the X server only, or possibly some other process has run amok and is consuming 100% of the CPU resource. If, immediately preceding the lockup you did NOT see a "kernel panic" message, then it is probably not a system crash, and you (and your filesystem) will have a brighter future if you will execute a graceful shutdown and reboot. Here is what to do.

First, the mnemonic to remember:

Raising Skinny Elephants Is Utterly Boring

BEFORE you reach for that power switch, give the Alt-SysRq combo a chance to do a graceful shutdown/reboot. Press and hold down "Alt-SysRq" ("SysRq" is the key otherwise known in DOS-world as "PrtScn", normally near the right end of the top row of keys) and then, one at a time, S-L-O-W-L-Y in sequence, " r s e i u b ".

Probably you will be amazed to see your "locked up" system do a shutdown and normal reboot.

Reference: [http://linuxgazette.net/issue81/vikas.html](http://linuxgazette.net/issue81/vikas.html)

---

### Post by diagram30 on 2010-06-09
> **leviathan8 said:**
> [B]That could be a solution. Can you please explain these more detailed?
I want exactly the steps to be made. I would really appreciate this. Thank you.
[/B]

I did not fully comprehend whether you are able to access a tty (ctrl+alt+f1/2/3/4/5/6). Should you be able to access it, run: (# denotes command being ran as root, $ as a regular user)

# service gdm stop
$ startx 

Should this method work, you would just access a terminal and run gnome-session-properties, check for whatever process tries to start up once with your session and asks for elevated privileges, and try turning it off. (alternatively, if this process is essential to your work being done, you could append the "sleep" command in such a fashion that the command field of your task would look like this "sleep 1 | rest-of-command --and-its-switches".)
If all else fails, post back.

---

### Post by jrg3 on 2010-06-09
Also, if you do get to the point where you are able to type, and you are still receiving the Gnome Default Key prompt, the Gnome Default Key is the first password you ever logged in with. You may have changed it since then and that's probably what initiated the prompt. But if you can remember it, that's what you'll want to type.

(Unless at any point you changed the default key. And you'll know if you did... it's nothing you can do by accident.)

---

### Post by alexeix on 2010-06-09
I'm running the latest version of Kubuntu and after installing updates (as prompted) last night, I'm experiencing exactly the same problem.

The Keyring window is displayed when I've logged in, but I am unable to type any text.  However, I can move the cursor around the screen as normal.

When I press the physical power button on the PC, Kubuntu goes to a 30 second log-out timer.
When it logs out, I can subsequently log back in again, but with the same issue.

This is a major problem...

I will try the RSEIUB trick, but can't see how it will make any difference to my situation, since I can do a reboot anyway.

(am using reliable Windows7 to report this issue...rushes for cover)

---

### Post by alexeix on 2010-06-09
A quick search on the forums, shows that a number of users are suddenly experiencing this issue, e.g. 
[EMAIL="http://ubuntuforums.org/showthread.php?t=1504990&highlight=keyring+password"]http://ubuntuforums.org/showthread.php?t=1504990&highlight=keyring+password[/EMAIL]

---

### Post by diagram30 on 2010-06-10
> **alexeix said:**
> A quick search on the forums, shows that a number of users are suddenly experiencing this issue, e.g. 
[EMAIL="http://ubuntuforums.org/showthread.php?t=1504990&highlight=keyring+password"]http://ubuntuforums.org/showthread.php?t=1504990&highlight=keyring+password[/EMAIL]

Oddly enough, Debian unstable (x86) does not have these issues with Gnome. I have a vanilla gnome session on my box (which I rarely use) and this does not happen to it, even with the latest update.

---

### Post by leviathan8 on 2010-06-10
**Thanks for tips germanix and diagram30. I will try both as soon as I get on ubuntu. Also, jrg3, I didn't changed the password, it's the old one.**

---

### Post by leviathan8 on 2010-06-10
**Ok, I'm starting right now. If it won't work, I'll come back.**

---

### Post by leviathan8 on 2010-06-11
**I managed to startx, disabled some stuff in gnome session, but the keyring still pops up...**

---

### Post by alexeix on 2010-06-11
I managed to log-in again a couple of days ago, but I don't know why it worked - luck or did I do something differently?!.

Now, I've started up my PC today and the Keyring problem is back.
This is wwhat I would class as a 'system down', since once I log in, I can't do anything else.

Any suggestions how to troubleshoot/resolve this from the command line?
I like Kubuntu, but I really don't have time for this...

By the way, the ALT-PrtScre, RSEIUB suggestion didn't do anything.

Thank **** the World Cup has started!

---

### Post by alexeix on 2010-06-11
Would this work?

[http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/]("http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/")

---

### Post by alexeix on 2010-06-11
Okay, so I ran the following command, rebooted and now I don't get the 'locked' keyring prompt which you can't enter text into!

"sudo apt-get remove gnome-keyring"

I strongly suspect this issue was caused by an auto update, because I had done nothing else to change my system.

Kubuntu lives to fight another day on my computer...

But only just.

---

