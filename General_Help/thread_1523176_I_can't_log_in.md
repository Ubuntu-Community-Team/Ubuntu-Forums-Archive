---
title: "I can't log in"
date: 2010-07-03
forum: General Help
---

### Post by mryup on 2010-07-03
Hi formites! I have a problem. I was busy in ubuntu [10.04], trying to  launch a game through wine, the game loaded incorrectly and as I'm still  fairly new with ubuntu I tried different combination of keys trying to  force-stop the game.

The combinations included the keys ctrl, alt, del, q, w and F4
 Pushing the keys had no visible effect so I hard booted the pc. 
After boot I get the logon screen (which I normally didn't get because it  logged in automatically) and I enter my user name and pass, the screen  goes black and I get the logon screen once again. This procedure loops  indefinitely.

Can somebody please help with a remedy?!

---

### Post by Jamesss on 2010-07-03
Sounds like you have a similar problem to me ([thread 1523153](http://ubuntuforums.org/showthread.php?t=1523153)). You could try to log in from the command line by pressing ctrl-alt-F1 and entering your username and password and confirm if this is the same error. I have read somewhere online that seems to suggest it might be related to pam but I have no idea how to fix this. 

Also, if your system hangs and you need to reboot, you can always try [Ctrl-Alt-SysRq+r,s,e,i,u,b](http://wwww.ubuntuforums.org/showthread.php?p=8263198). I would always try that over a hard reset.

hth

James

---

### Post by mryup on 2010-07-03
> **Jamesss said:**
> Sounds like you have a similar problem to me ([thread 1523153]("http://ubuntuforums.org/showthread.php?t=1523153")). You could try to log in from the command line by pressing ctrl-alt-F1 and entering your username and password and confirm if this is the same error. I have read somewhere online that seems to suggest it might be related to pam but I have no idea how to fix this. 

Also, if your system hangs and you need to reboot, you can always try [Ctrl-Alt-SysRq+r,s,e,i,u,b]("http://wwww.ubuntuforums.org/showthread.php?p=8263198"). I would always try that over a hard reset.

hth

James

It does sound the same, however, when I log in via CLI, mine doesn't display any errors, etc.

I have read something about pam, and checked the logs and evidently there is something about pam.

---

