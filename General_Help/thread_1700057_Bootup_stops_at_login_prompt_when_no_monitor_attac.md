---
title: "Bootup stops at login prompt when no monitor attached"
date: 2011-03-04
forum: General Help
---

### Post by SESteve on 2011-03-04
I'm setting up a machine with Ubuntu 10.10 to run headless. The other machines on my network are Macs. I'm not a Linux guru by any stretch of the imagination but I generally know my way around and spend a fair amount of time in Terminal on the Mac. I haven't set up a Linux machine before.

I was able to use [this article]("http://missingreadme.wordpress.com/2010/05/08/how-to-set-up-afp-filesharing-on-ubuntu/") to get the machine working as an AFP file server. And [this link]("http://www.sanityinc.com/articles/mac-screen-sharing-with-linux") helped me get screen sharing working (although I'm using x11vnc, not tightvncserver).

I have Ubuntu set to automatically log in with my user account. x11vnc is set to run under System -> Preferences -> Startup Applications (I originally tried running it from /etc/rc.local but that didn't seem to work).

Everything was working great with the keyboard, mouse, and monitor connected. When I disconnected them and booted the machine, screen sharing didn't work. I reconnected the monitor and saw that the bootup process was stopped at the login prompt. After some testing I determined that when there is a monitor connected, Ubuntu boots all the way into my user account. When there's no monitor connected, it stops at the login prompt. (Keyboard and mouse connections make no difference.) Of course there's the chance that it's logging in and back out when there's no monitor connected, but it's hard to know without a monitor connected.

Is there something I need to do to get the automatic login to happen when there's no monitor connected?

---

