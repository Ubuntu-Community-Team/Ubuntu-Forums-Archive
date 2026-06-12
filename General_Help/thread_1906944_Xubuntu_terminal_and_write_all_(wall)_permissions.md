---
title: "Xubuntu terminal and write all (wall) permissions"
date: 2012-01-10
forum: General Help
---

### Post by Calcipher on 2012-01-10
I am having a bit of a problem with Xubuntu's terminal (11.10x64, Terminal 0.4.8).  When I issue a command like 'shutdown -h 15:00', I'd expect the computer to shutdown at 15:00 (which it does), but I'd also expect it to send out a system broadcast message to all sessions every 15 minutes or so mentioning that the system was going down for shutdown soon.  Oddly, this message doesn't appear, not even in the session that ran the shutdown command.  

I did some digging and it seems that shutdown uses wall to send these messages out.  Looking deeper, I noticed that each terminal can have write access turned off through the mesg command.  I checked, however, and it seems that mesg returns 'y' for all terminals.  Further, even disabling mesg doesn't disable root's ability to write to your terminal.  Further testing (using wall manually as root and not) confirms that no sessions get the wall messages. 

Edit: Wrote 11.04 because I'm an idiot.  Fixed to 11.10

So, I guess I was hoping someone had some clue as to why writes are failing like this.

---

### Post by Toz on 2012-01-10
I can confirm that I'm seeing the same issue on my Xubuntu 11.10 install. Also interesting is that if I go to TTY1 and log in there, I will see/receive the wall messages. 

I think this might be related to a bug I filed a while back about lightdm not registering logins (see: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297")). If I run w, who, or last, it doesn't seem to record my current graphical login (but does if I log into a tty terminal). This being the case, I'm wondering whether wall just doesn't know that there is a session to send the message to.

---

### Post by Calcipher on 2012-01-10
> **Toz said:**
> If I run w, who, or last, it doesn't seem to record my current graphical login (but does if I log into a tty terminal). This being the case, I'm wondering whether wall just doesn't know that there is a session to send the message to.

Hrm, that is possible.  I, too, noticed the lack of information from w and its ilk.  I'll add myself to your ticket.

Edit: I tested your theory by sshing into my localhost.  Once done, walls are broadcast to the ssh session.

---

