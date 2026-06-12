---
title: "&quot;unlock keyring&quot; problem"
date: 2010-01-08
forum: General Help
---

### Post by ngronewold on 2010-01-08
As I try to add new bells and whistles to my system (the latest being Verizon's USB760 modem, needed for work) I keep running into this message:

---   'nm-connection-editor' (/usr/bin/nm-connection-editor) wants access to the default keyring, but it is locked


And it asks for a password.  But my login password does not work (I have auto login, but I have to type the password when I wake my laptop up from a nap). When installing Ubuntu nowhere did it ever ask me to provide a keyring password. I have only one associated with this machine and I have never changed it.

This same message comes up when getting into Evolution mail.  Here I simply click "deny" and get my email anyway.  But clicking "deny" to tell my computer to configure the USB760 doesn't seem to work.

Is there a quick and easy way to get rid of this pop-up once and for all?  And why doesn't my login password work for it?

More to the point, why is it doing this in the first place when I was never asked or allowed to provide any keyring password at all?  Does the computer come up with its own password?


By the way, Linux Ubuntu freed me from the horrible Windows Vista.  I'm never going back.  I've already cracked a few other minor quirks so I'm sure this one will get fixed as well.

Thanks!

---

### Post by bkratz on 2010-01-08
Look through this thread and see if helpful

[http://ubuntuforums.org/showthread.php?t=1315729](http://ubuntuforums.org/showthread.php?t=1315729)

---

### Post by ngronewold on 2010-01-08
Thanks, but looks like I figured it out just before I got back on and read your tip.  Basically all I did was set the default keyring to the login. Did some other stuff that I can't remember, but it basically allowed some earlier tinkering I did last week to take effect on all apps -- wireless, plug-in devices, and finally Evolution.

But now I know where to go once this problem emerges again. Cheers!

---

