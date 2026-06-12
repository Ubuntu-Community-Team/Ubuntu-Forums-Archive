---
title: "jaunty 9.04 / x11vnc / ssh / putty / tightvnc problem"
date: 2009-09-23
forum: General Help
---

### Post by merchiston on 2009-09-23
I followed the thread on [https://help.ubuntu.com/community/VNC/Servers#x11vnc-before-login](https://help.ubuntu.com/community/VNC/Servers#x11vnc-before-login) to get the ability to remote login over a secure ssh channel. All works fine on 8.04 (hardy), but the vnc process dies immediately after login with 9.04 (jaunty).
 
Has anyone found a solution to this?
 
TiA
 
James.

---

### Post by krunge on 2009-09-23
> I followed the thread on [https://help.ubuntu.com/community/VNC/Servers#x11vnc-before-login](https://help.ubuntu.com/community/VNC/Servers#x11vnc-before-login) to get the ability to remote login over a secure ssh channel. All works fine on 8.04 (hardy), but the vnc process dies immediately after login with 9.04 (jaunty).
 
Has anyone found a solution to this?

Perhaps you are seeing this problem:
[INDENT][http://ubuntuforums.org/showthread.php?t=965695&highlight=noxfixes&page=2](http://ubuntuforums.org/showthread.php?t=965695&highlight=noxfixes&page=2)[/INDENT]See post #13.

The workaround is to add:```
-noxfixes
``` to the x11vnc cmdline.  This avoids a bug in the Xserver involving the Cursor shape.  If this is your problem, feel free to add your case to the bug reports.

---

### Post by merchiston on 2009-09-23
Karl
 
Thanks for this.  When I add -nofixes to my cmdline, it complains (no such option).
 
Is this right?  On my putty cmdline:
 
sudo x11vnc -nofixes -safer -localhost -once -nopw -auth /var/lib/gdm/:0.Xauth -display :0
 
Where does the -nofixes go?
 
Should I keep KillInitClients=false or =true in /etc/gdm/gdm.conf-custom?
 
James

---

### Post by krunge on 2009-09-23
> **merchiston said:**
> Karl
 
Thanks for this.  When I add -nofixes to my cmdline, it complains (no such option).
 
Is this right?  

Not quite.  It is "-noxfixes" not "-nofixes".
> 
Should I keep KillInitClients=false or =true in /etc/gdm/gdm.conf-custom?

Yep, keep all the stuff you had working previously in.  All the "-noxfixes" is doing is to avoid the Xorg bug crash that was introduced.

Report back here if it works.

BTW, if you read more of the thread I pointed to, you will see supplying this option will disable reading the mouse cursor shape.  So just a few canned cursors will be used.  The thread suggests some workarounds if you want the cursors .

---

### Post by krunge on 2009-09-23
> **krunge said:**
> 
Yep, keep all the stuff you had working previously in.
To be clear: keep KillInitClients=false.  We don't want GDM to kill x11vnc after the user logs in.

---

### Post by merchiston on 2009-09-24
Karl
 
Thanks - I must have seen too many of these posts too late at night to miss the "x"!
 
It works!  At least for one of my 9.04 servers.  On the other, I get an immediate connection closed (which is worse than before!), so I suspect something else at work...
 
I do get the cursor issue as you suggest, so will follow up the posts to resolve.
 
Thanks.
 
James.

---

### Post by merchiston on 2009-09-24
Karl
 
Your solution worked for one of my jaunty boxes, but not the other.  I'm struggling to find the solution now - can you (or anyone else) point me to where I should look for clues?  Log files for vnc?  xorg?  
 
TiA
 
James.

---

### Post by krunge on 2009-09-24
> **merchiston said:**
> Your solution worked for one of my jaunty boxes, but not the other.  I'm struggling to find the solution now - can you (or anyone else) point me to where I should look for clues?  Log files for vnc?  xorg?  
If you look at the thread I mentioned you will see suggestions for where to look to troubleshoot.

I believe the key one is /var/log/Xorg.0 and /var/log/Xorg.0.old.  Or they may be slightly differently named.  That is where to look for Xorg server crash.  /var/log/messages may have info too (e.g. from kernel.)

However, my guess is on this one box you have the GDM KillInitClients incorrectly set up.  E.g. you changed a config file, but gdm is ignoring it.  Etc.

---

