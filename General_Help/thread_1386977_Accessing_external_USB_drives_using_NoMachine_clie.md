---
title: "Accessing external USB drives using NoMachine client"
date: 2010-01-21
forum: General Help
---

### Post by OobleCaboodle on 2010-01-21
Hi. I have an Ubuntu jaunty fileserver. I connect to the machine from time to time using the Nomachine client on windows.
Everything is setup and working perfectly, except for one thing. When I acces the server remotely, I cannot access any external USB drives connected to it. The drive mounts fine, and is available when logged on locally to the machine, just not when logged in via Nomachine.

I'm using the freeNX server, and installed it according to the steps detailed on the how to guide...
[https://help.ubuntu.com/community/FreeNX]("https://help.ubuntu.com/community/FreeNX")

Any help would be appreciated, thanks.

---

### Post by Lekensteyn on 2010-01-21
What do you mean with, "I can't get access to any USB drives"?
Any errors?
USB devices are mounted on /media/
ls /media shows all available mounted drives.

---

### Post by pricetech on 2010-01-21
I'm not using freeNX.  I'm using the Client, Node, Server from nomachine on my Linux box and I'm having no problems.

---

### Post by OobleCaboodle on 2010-01-22
> **Lekensteyn said:**
> What do you mean with, "I can't get access to any USB drives"?
Any errors?
USB devices are mounted on /media/
ls /media shows all available mounted drives.

The drive would show up under Computer:/// and /media/ but it would not mount at all, I got no error message, it just simply refused.

Curiously though, it is now working, although I have changed no settings whatsoever.
Does that mean this is solved?
hmm.

---

### Post by Tiler on 2010-06-30
I have consistently encountered this problem on multiple Ubuntu/Nx setups.  I forget what the change is, hence I'm here looking for it again but it occurs when I am connected remotely via Nx and try to plug in the drive.  Currently in Lucid it just says, "Cannot mount"

When I *terminate* that Nx session, physically go to the machine and plug in the drive, it mounts as expected.  Then, I may go connect remotely via Nx and it is already there, mounted in the new session.  

I believe there's an FSTAB edit posted somewhere.  I couldn't find it quickly but my workaround has been to give up on the completely headless setup and leave a kb and mouse attached to the Ubuntu PC.

I hope this helps.

---

