---
title: "Remote login for Ubuntu 9.10"
date: 2009-11-02
forum: General Help
---

### Post by NJDon69 on 2009-11-02
I'm looking for a remote login solution that does not require the user to be logged in as it does using VNC. This was possible with previous releases. I understand the need gdm has changed. Any suggestions would be greatly appreciated. Thank you for your assistance.

---

### Post by Youresorock on 2009-11-02
I was really surprised they removed so much from bootup.  I used to use the login via SSH all the time.  On a local network you didn't even know it wasn't your computer.   VNC has always sucked, and the built in server does require you be logged in, which is silly.

You'll need a thirdparty VNC server that creates a second xorg screen.  I'm going to test if you can still log into a 9.10 box over SSH remote session from a 9.04, and if so, I'll try to hack that feature back in. :D

Just be glad you're not running a Mac.  It's impossible with standard tools to connect at anything other than 32bit lossless VNC.  Good luck with that.

Windows has us beat with remote desktop, just no contest.  Still won't use it tho.  :P

---

### Post by NickJones on 2009-11-02
Ah! Tis annoying! I have to log on to VNC??!?!?!

---

