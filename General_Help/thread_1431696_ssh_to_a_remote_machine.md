---
title: "ssh to a remote machine"
date: 2010-03-16
forum: General Help
---

### Post by janjust on 2010-03-16
Hey guys, (sorry if this was already discussed)

I have a Ubuntu machine I'm trying to ssh into from my mac.

The problem I'm having is I can't ssh into it UNLESS I'm already logged on manually AT the machine.

I think this is because the static IP connection that I have on my manual machine only connects when I'm logged in directly. In other words the machine doesn't connect unless someone is directly logged in AT the machine.

Is there a way to establish this link automatically before I'm logged in?
I tried searching the forum for a similar problem but was unable to find anything specific in this direction.
Please direct me further or help on how to solve this issue.

Thank you,
               janjust

---

### Post by lloyd_b on 2010-03-17
> **janjust said:**
> Hey guys, (sorry if this was already discussed)

I have a Ubuntu machine I'm trying to ssh into from my mac.

The problem I'm having is I can't ssh into it UNLESS I'm already logged on manually AT the machine.

I think this is because the static IP connection that I have on my manual machine only connects when I'm logged in directly. In other words the machine doesn't connect unless someone is directly logged in AT the machine.

Is there a way to establish this link automatically before I'm logged in?
I tried searching the forum for a similar problem but was unable to find anything specific in this direction.
Please direct me further or help on how to solve this issue.

Thank you,
               janjust

Are you using wired or wireless networking?  For wired connections, it's pretty easy to set up a static connection that starts with the machine, so you don't have to log in and get Network Manager to start up the networking.

I assume it's possible to do the same with wireless, but I'm not familiar enough with wireless to help you do so.

Lloyd B.

---

### Post by Iowan on 2010-03-17
I suspect the remote machine is controlled by Network Manager (which doesn't activate interfaces until login. You can try setting up a connection in */etc/network/interfaces*... but there's some ongoing discussion/research as to whether NM still plays nicely with it - or if NM must be removed (purged, even...).

---

