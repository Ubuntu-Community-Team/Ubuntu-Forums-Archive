---
title: "Xorg freezing, but mouse still works?"
date: 2006-03-21
forum: General Help
---

### Post by UbunT00L on 2006-03-21
I have a problem where Xorg in Breezy will freeze.  My keyboard will not respond and I am unable to switch to a terminal as a result.  However, my mouse seems to keep working, I can move it around the screen but nothing will respond to clicks.  Luckily, I am still able to ssh into the system, but I cannot kill X for some reason.  Typing in "sudo killall -9 X" doesn't seem to do anything, and I still see X when I look at "ps ax".  **edit** I am able to kill X using the kill -9 PID option.  **/edit** I am able to reboot though, which is what I have been doing.

These are the last lines I saw in the Xorg.0.log during a freeze:

```
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Got unexpected buttonTimer in state 0
```

Has anyone else experienced this behaviour?

---

### Post by Treviño on 2006-03-21
[quote=UbunT00L]These are the last lines I saw in the Xorg.0.log during a freeze:

```
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Got unexpected buttonTimer in state 0
``` 
Has anyone else experienced this behaviour?[/quote]
Same here... :(

I'm using Kubuntu for months, but yesterday night I've rebooted after some days of uptime (and some installations, but nothing of strange I think) and my screen showed a back background with strange green lines. :-#
No way to reboot or doing anithing.
So, using a live cd I've moved the /etc/X11/xorg.conf file not to make Xorg load while booting; I've tried to reconfigure xserver-xorg also restoring the "ati" driver instead of "fglrx", but running startx only the black & green-stripped screen has changed :???:, now Xorg (both using ati and fglrx) seems to start, it shows a gray screen with a "X" mouse cursor (that I can move), and then, after few seconds, it crashes going back to the shell that shows the errors above.

I've reinstalled fglrx, downgraded the kernel (I've put an unstable .deb taken from a taiwanese repository), but the error remains.

Sometime I also get this:
```
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
```
I've searched the forum, but nothing helped me.

This thread: [http://ubuntuforums.org/showthread.php?t=75333](http://ubuntuforums.org/showthread.php?t=75333) seems useful, but not for me :(

---

### Post by Treviño on 2006-03-21
No help? :( :(
I can't run my kubuntu... :|

Btw I've found that maybe X starts, the problem is in kdm, because if I put something like 
echo "X has started" >> Xstarted
In a /home/user/.xinit file, each time i run startx, there's a new line on /home/user/Xstarted containing text "X has started"...
So maybe I must check the kde de in order than X.. mhmhm

Suggestions??

---

### Post by UbunT00L on 2006-03-22
Ok, I commented out the "load GLX" and "load dri" lines in my xorg.conf, and I haven't had a crash so far.  The downside of this is that I don't have direct rendering now and can't play 3D games.  I'm going to try just removing the "load dri" comment and the "load GLCore" comments, and leaving the "load glx" comment in.  According to the nvidia FAQ listed [here]("ftp://download.nvidia.com/XFree86/Linux-x86/1.0-4363/README.txt") that's what I should have originally done. I'll do that as soon as I get back home.

Treviño:  As for your problem, have you tried resorting back to the original xorg.conf that you had when you first installed?  If my problem persists, I'm going to try that too (I believe I made a backup before I started making changed to it).

---

### Post by Treviño on 2006-03-22
[quote=UbunT00L]Treviño:  As for your problem, have you tried resorting back to the original xorg.conf that you had when you first installed?  If my problem persists, I'm going to try that too (I believe I made a backup before I started making changed to it).[/quote]
Yes... I've tried to restore the original xorg.conf file, but that was not wrong!

Well... I've found the problem ](*,) and what's better, I've **solved it**!

The problem where not in X, as I said in my last previous (quick) post, but in KDM... I was able to run only "X" with a working "desktop" and mouse cursor.

The day before, in fact I've installed a software to map keyboards' multimedia keys, keytouch. I din't know that it was the cause of my problem, but now I'm certain of it.

To fix my problem I've done this:
```
sudo apt-get remove --purge keytouch keytouch-editor kdm
sudo apt-get install kdm
```
So, purging kdm and reinstalling it all worked! :D

After that I've tried to see if problem was really in keytouch, so I reinstalled it (always using the same package: the one downloadable from its website) ad it worked well, but, after a reboot X-KDM gave me, the same problems again...
I remade my fixing procedure and all come back working another time.

*MAYBE*, removing /etc/kde3/kdm/ files you can have the same result, but I think it's hard, because purging and reinstalling kdm didn't give me any solution.

Bye and thanks, I hope my story could help others members!

---

### Post by ubernoob on 2006-03-23
Same problem here. I logged into another shell and killed openoffice. That helped. The problem must be either openoffice and/or glx. I haven't loaded dri.

Edit: It was a doc file in openoffice with some picture that made the crash on my computer. I then tried it with Dapper and OpenOffice.org 2. That didn't crash.

---

