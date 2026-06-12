---
title: "Beginner: Remote Desktop Exceptions"
date: 2011-07-16
forum: General Help
---

### Post by TorZhan on 2011-07-16
Hi guys!

I just installed Ubuntu 11.04 on my laptop yesterday.
I'm using it mainly to stream media across the network.

Anywho, I setup remote desktop access so I can access the machine through my iPhone. (using Mocha VNC lite for iPhone, built in remote desktop on this machine).

There is a function that I choose to activate, so the machine prompts you when someone is trying to gain remote access, I think its great and all. But I'd like to make an exception to it, so that the machine recognizes my phones macID and doesnt require me to be near the machine when trying to connect via my phone.

The problem I have is that I am brand new to this and I have no clue wheres to even begin.
I tried to see any previous posts about this but couldnt find any info on this.

I would appreciate any pointers or help in the matter

---

### Post by TorZhan on 2011-07-16
*bump*

---

### Post by atca on 2011-07-16
I dont think you can set up per machine authentication settings.

I'd install tightvncserver as a secondary VNC server and set it up on a unique port and set the firewall to only allow your phone to access that port.

Tightvncserver will also be a lot quicker than the builtin ubuntu vino server.

---

### Post by TorZhan on 2011-07-16
Ill try it out. Going through the firewall seems more logical. Ill test and see where it takes me, thanka for the reply!

---

