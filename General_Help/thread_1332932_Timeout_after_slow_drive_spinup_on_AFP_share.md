---
title: "Timeout after slow drive spinup on AFP share"
date: 2009-11-20
forum: General Help
---

### Post by eicos on 2009-11-20
Hi, all. I have Ubuntu 9.10, and an Airport Extreme that I'm using to share a 1 TB external drive over encrypted AFP. I'm using afpfs-ng 0.8.1, a wonderful program by Alex De Vries, to mount the share through FUSE. With Alex's help, I've finally gotten the login to work and the disk to mount automatically at startup. So far, so good. 

Now, the AE does a good job of spinning down the drive after a short period of inactivity. The problem, then, is that when the OS wants to read from the cold share, it has to wait for the drive to spinup... which happens very slowly. It is perhaps 10-15 seconds before the drive is accessible. Thus, that first operation will throw an error and have to be cancelled. The second attempt will work. However, I would like to know if it's possible to change a setting so that all components involved will wait gracefully. I am not sure whether the timeout is originating in afpfsd, FUSE, or some other part of the operating system.

Thanks!
-Danny

---

### Post by komputes on 2009-11-20
I observed the same thing when I used afpfs-ng. This project definitely needs a little more love and desktop integration.

---

### Post by alexthepuffin on 2009-11-21
One of two things is happening: either the AE is maintaining the session and is just slow to respond, or it actually suspends the connection for reconnection when it wakes up.  

If you can provide me a network capture during the spin down and startup with afpfs-ng, that'll help me figure that out. If you can provide me a network capture using a Mac OS X client going through the same, that'd be even better as I can get afpfs-ng to mimic the 'correct' behaviour.

If it is the former, a simple change in the timeouts might help.  That would be to change "#define DSI_DEFAULT_TIMEOUT 5" in include/dsi.h to something more like 60. That's technically not following the specification.  The effect is that any file operation (read, write, open, etc) will block for 60 seconds before timing out and giving you the EIO error.

With regards to afpfs-ng needing more love... patches are always welcome!  The desktop integration doesn't have an obvious solution; when I took a stab at it a year ago, kio-slave was in rough shape and was just a waste of time.  There are some fuse KDE interfaces, but I haven't looked at them lately.



- Alex, the author of afpfs-ng.

---

