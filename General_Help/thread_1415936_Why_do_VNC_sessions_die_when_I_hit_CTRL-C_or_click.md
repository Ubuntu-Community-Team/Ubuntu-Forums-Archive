---
title: "Why do VNC sessions die when I hit CTRL-C or click &quot;copy&quot; in a text editor?"
date: 2010-02-25
forum: General Help
---

### Post by diablo75 on 2010-02-25
This is something that has annoyed me for YEARS and I don't know why it is the way it is.  Maybe it's the nature of the default VNC viewer client I use in Ubuntu (xvnc4viewer) or maybe it's the server that comes with Ubuntu by default (vino).  All I know is that, if I VNC into a system that's not been VNC'ed into since boot, and hit CTRL-C to copy some text I have highlighted, the session is killed.  And recently (in the past month) I've noticed that once this happens, I have to SSH into the system to restart it because I can't reconnect via VNC... as if the port hasn't been released or it's failing to listen like it's suppose to.

Does anyone else have this problem or perhaps someone out there able to shed some light on why this little glitch seems to happen.  In the past, after the session was killed by clicking "copy" in nearly any application that offered it, I could just reconnect.  It was a minor annoyance because I could click copy endlessly from that point on and the same problem wouldn't repeat.  But now it seems to lock up the server and prevent me from reconnecting and I don't know of any other good way to work around this other than restart the server, which means the next time I click copy, the same thing is going to happen and I'll be forced to restart the server AGAIN and that, to me, is intolerable.

---

### Post by moorsey on 2010-03-18
just searching for the exact same thing and found this, so, bump!

I use VNC from my Windows machine to access my Ubuntu server, same thing happens here.

Thoughts anyone?

Cheers

---

### Post by rnerwein on 2010-03-18
hi
i never worked with VNC but that behavior looks for me as a config issue. CTRL-C is a EscapeChar.
like in ssh ~. = disconnect. i guess there is a configuration file around where you can configure
your EscapeChars. must be in the man pages for VNC.
i hope this will help.
ciao

---

### Post by diablo75 on 2010-03-18
> **rnerwein said:**
> hi
i never worked with VNC but that behavior looks for me as a config issue. CTRL-C is a EscapeChar.
like in ssh ~. = disconnect. i guess there is a configuration file around where you can configure
your EscapeChars. must be in the man pages for VNC.
i hope this will help.
ciao

Hmmm, no info on a config file available in the manual for vncviewer (man vncviewer)...  So still looking for something like that.  But the way you make it sound, it almost seems like it would be a problem with the shell that vncviewer is being run in (bash... I think).  The weird part about this theory is:  Sure, CTRL-C is kind of a global shortcut you can use in a terminal window to Cancel processes that are running, but if that's the case, why does the same problem happen by just clicking on a button that says copy (on the remote PC, via VNC)?  Would that mean that when a person opens any application, clicks Edit>Copy, their machine is actually typing a quiet CTRL-C for the user?  Because then the CTRL-C aspect about all this might affect both the server and client sides.  But I really don't know what is true in any of that mess I just came up with.

---

### Post by moorsey on 2010-07-11
just wanted to bump this one, the same thing happened again and the annoyance spurred me to posting again!

Right clicked on a web address in firefox, clicked copy and now remote access is disabled, I have no other access setup to the machine, so now I either have to cycle the power, or hook up KVM to turn remote desktop back on.

Any other thoughts on this?

---

### Post by racertim on 2010-09-23
Bump, I've had this problem for a while and it is getting old. I'm using mRemote and every time I do it, I cannot connect through VNC until I manually reboot the system.

---

