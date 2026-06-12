---
title: "Remote Desktop"
date: 2010-06-10
forum: General Help
---

### Post by borderfox on 2010-06-10
Hi all.  For my next project at the weekend, I want to try and setup some form of remote desktop system.  I am running Ubuntu 10.04LTS - as is the remote machine which is 3 hours flight time away from me.
 
Can someone kickstart the research I need to do on this by pointing me in the right direction? 
How difficult will it be (particularly for a linux newbie) to implement?
 
Any tutorial links that anyone has would be very welcome.

---

### Post by ambroseya on 2010-06-10
VNC. It's the simplest. I've had it on long enough I don't have any good links off the top of my head but google for setup vnc and you get a large amount of instructions, including youtube video howtos. The hard part is only securing it in a way you can reach it from outside your lan, something I haven't done, as I've always been on the same lan for it.

edit to add: when I said securing the connection from outside the lan was the hard part, I personally know many people that have done it, so it is by no means terribly difficult.

---

### Post by Peter09 on 2010-06-10
Well it depends exactly what functionality you want to get. 
 
Try FREENX for a full desktop experience. I think its in the repos' but not sure. It will give you a secure encrypted connection to a remote destop. It allows you to login (rather than view an existing desktop).
 
If you what just to run apps remotley and copy files the ssh-server by its self is good enough.

---

### Post by pricetech on 2010-06-10
Another option is NX Client, Node Server from nomachine.com.

Whatever you use, your going to have to forward a port in your router to your Linux box.

I haven't used FreeNX, so I can't compare ease of use, but NX from nomachine is pretty simple to set up.

---

### Post by nnamdi on 2010-06-10
have u used teamviewer before it is also nice tooo

---

