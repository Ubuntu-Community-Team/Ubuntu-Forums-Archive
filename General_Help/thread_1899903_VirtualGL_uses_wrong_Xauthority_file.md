---
title: "VirtualGL uses wrong Xauthority file"
date: 2011-12-24
forum: General Help
---

### Post by Howy on 2011-12-24
Ok, so, I've been experimenting with a way of being able to play 3D games wherever, whenever. My solution was VirtualGL + TurboVNC; quick and simple in use. Performance is good across WLAN and even better across LAN, and I can't wish for more. Only 1 problem: I don't want anyone to randomly log in to my own user and mess around with an administrator account. I have previously run the TurboVNC server on my own user, played around and so on. It worked as it should've.
However, when I made a new user for exclusive use with TurboVNC and a representative for LAN gaming, it goes wrong. When I try starting the server as my virtualgl-user (made by me with access to the virtualgl group thingy)
it uses the wrong Xauth file, giving it no permission to access hardware acceleration and rendering.
This is the error: (sensitive information taken away)
```
xauth:  timeout in locking authority file /home/{admin user}/.Xauthority
```
It's basically using the wrong Xauthority file, but I'm not sure how I should approach this problem. It is not suitable to loosen security on this user, I just want to know how I can make it use the correct Xauthority file. I checked the configuration in /etc for TurboVNC, and it seems legit/okay. ( :P )

Is this an error with xauth or VirtualGL, or what?
ssh -X works fine, and apps act normally from there.

---

