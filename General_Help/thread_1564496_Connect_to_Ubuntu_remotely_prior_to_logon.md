---
title: "Connect to Ubuntu remotely prior to logon"
date: 2010-08-30
forum: General Help
---

### Post by prroots on 2010-08-30
I'm running Ubuntu on a Zotac home theater PC. I wish to connect from another PC prior to login. The reason is that the home theater system has no convenient display. I've succeeded in getting a connection prior to logon from a PC using TightVNC. I've also tried Teamviewer running in Ubuntu without success. I'm now experimenting with X windows, but it seems complicated. TightVNC is working well ecept that it opens a new session and I'd rather share the same session on Display 0. I'd appreciate any feedback on how best to connect to my Ubuntu home theater PC prior to logon and share the same session. Thanks
pete

---

### Post by prroots on 2010-09-04
Anyone have ideas? Thanks
Pete

---

### Post by dcstar on 2010-09-05
> **prroots said:**
> Anyone have ideas? Thanks
Pete
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by prroots on 2010-09-05
Thanks [dcstar]("http://ubuntuforums.org/member.php?u=7532"). As mentioned, I've been successful logging on with TightVNC prior to logon. It works great. If there are no other ideas, then this will be my solution. 
Pete

---

### Post by prroots on 2010-09-07
I've discovered that the keyword for this topic is 'headless'! This is the circumstance under which people want to achieve this capability. I'm hoping to find a definitive article (targeting newbies) on how to do this with Ubuntu V10.4. Most people recommend connecting with SSH and then starting VNC. Apparently this provides for better security. I'd really like to connect on Display 0, but so far no luck. The other issue is mounting the Windows partition. This happens automatically when I log on from primary display. Finally, I've had no luck changing the screen resolution when connecting with VNC so I end up having to scroll around to find the entire Ubuntu screen. I'd sure appreciate a reference on this topic for my version of Ubuntu. Thanks
Pete

---

### Post by prroots on 2010-09-16
i've finally got everything working well. It's surprising that I had to pull bits and pieces of info from so many places. One would think that there would be a neat little tutorial someplace on how to do this. I did learn that a program called x11VNC is designed to connect remotely to Display 0. I disqualified it because the lag time was too great. I ended up using tightvncserver on Ubuntu. I log in via SSH with PuTTY on my Windows computer and then invoke a little script that starts up tightvncserver on Display 1 with the correct resolution. I also had to create a script that runs on boot up to mount the drive that I use when connected remotely. The only problem now is that this configuration does not support cut & paste between my Windows vnc and Ubuntu tightvncserver. As a work around, I use IM to pass things. I understand x11VNC supports cut & paste, but again I had to disqualify it based on poor performance. If other Ubuntu newbies need more details, just ask.

---

### Post by prroots on 2010-09-20
I've finally got cut & paste to work using a program called vncconfig which gets installed along with vnc4server. The most helpful reference was: 
     [http://manpages.ubuntu.com/manpages/hardy/man1/vnc4config.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/vnc4config.1.html)

The actual command line used in file xstartup was:
   vncconfig -display $DISPLAY -iconic -nowin &

On bootup, I start PuTTY to connect to my remote Ubuntu box and can then invoke one of two scripts to start  vnc4server on either Display 0 or Display 1. I'm really amazed that this solution is not more widely publicized.
Pete

---

### Post by krunge on 2010-09-21
prroots:  Could you send your x11vnc output it prints out when it start up that looks something like this:
```

21/09/2010 15:27:04 
21/09/2010 15:27:04 fb read rate: 157 MB/sec
21/09/2010 15:27:04 fast read: reset wait  ms to: 10
21/09/2010 15:27:04 fast read: reset defer ms to: 10
21/09/2010 15:27:04 The X server says there are 10 mouse buttons.
21/09/2010 15:27:04 screen setup finished.
21/09/2010 15:27:04 

```
I'm trying to debug the slow response you saw.

Thanks.

---

### Post by prroots on 2010-09-22
> **krunge said:**
> prroots:  Could you send your x11vnc output it prints out when it start up that looks something like this:
```

21/09/2010 15:27:04 
21/09/2010 15:27:04 fb read rate: 157 MB/sec
21/09/2010 15:27:04 fast read: reset wait  ms to: 10
21/09/2010 15:27:04 fast read: reset defer ms to: 10
21/09/2010 15:27:04 The X server says there are 10 mouse buttons.
21/09/2010 15:27:04 screen setup finished.
21/09/2010 15:27:04 

```I'm trying to debug the slow response you saw.

Thanks.
Sorry, but my system is is no longer accessible. Will get back to it sometime in October.
Pete

---

