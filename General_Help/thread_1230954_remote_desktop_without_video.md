---
title: "remote desktop without video"
date: 2009-08-04
forum: General Help
---

### Post by iitywygms on 2009-08-04
Is it possible to use remote desktop without video?  Using the video part really slows things down. I don't need the video portion because all the computers are hooked up to monitors, they just have no keyboard or mouse. (used for mythtv)
Is that possible?  If so, how?
Thanks

---

### Post by warp99 on 2009-08-04
You can shell into the computers using SSH for command line operations and X forwarding if needed. What exactly do you want to accomplish?

---

### Post by iitywygms on 2009-08-04
I basically want to be able to control the mythfrontend, which is a gui.  
I do use ssh for alot of things, but sometimes it does not do exactly what I need.

---

### Post by warp99 on 2009-08-04
Mythtv already has a remote option that allows you to control any front end from the command line or another application using telnet:

[http://www.mythtv.org/wiki/Telnet_socket](http://www.mythtv.org/wiki/Telnet_socket)

If you just need to check listing, schedule recordings, change settings on front/backend machines, etc. then you can install mythweb on the backend machine and use the web interface. I access mythweb all of the time from remote locations using SSH and a socks proxy.

[http://www.mythtv.org/wiki/Mythweb](http://www.mythtv.org/wiki/Mythweb)

One of these solutions should be able to help you.

---

### Post by iitywygms on 2009-08-04
Thank you, that will be very helpful.
I still wonder if I can do remote desktop without the video.  
An example of when I would find that useful.  Say I want to go to youtube on the computer hooked up to my tv, using my laptop to control the mouse.  Doing this with remote desktop, with video, makes for a slow response.
What I am really looking for is just a way to use my laptop keyboard and mouse, to a different computer, over the network.
Can I disable video in remote desktop?

---

### Post by warp99 on 2009-08-04
Hmmh, I know that the remote desktop client that's include with Ubuntu does not have this feature, but another client may. Sorry I can't be more helpful.

---

### Post by geirha on 2009-08-04
Sounds like you want [Synergy](https://help.ubuntu.com/community/SynergyHowto)

---

