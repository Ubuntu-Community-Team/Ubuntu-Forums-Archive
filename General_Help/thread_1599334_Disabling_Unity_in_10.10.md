---
title: "Disabling Unity in 10.10?"
date: 2010-10-17
forum: General Help
---

### Post by Carpentr on 2010-10-17
I just installed the netbook remix 10.10 on my laptop. I have been using Unity and I would much rather prefer a standard GNOME desktop. I know there was a way to change the netbook interface to a standard GNOME one on the 8.04 remix. Anyone know if there's a way to do it in 10.10?

Thanks.

---

### Post by kerry_s on 2010-10-17
log out, select gnome in the session menu, log in

---

### Post by Carpentr on 2010-10-17
> **kerry_s said:**
> log out, select gnome in the session menu, log in

Thank you very much. That was so simple I can't believe I missed it!

---

### Post by quixote on 2010-10-19
During install I got some message about not able to do something or other with unity (missing driver maybe?).  It seemed to install fine, and I have a regular gnome desktop.  No unity.  And no sessions menu anywhere at all, not in the login screen, and not in the System menu.

Problem is, I installed it in Virtualbox precisely to have a look at the unity desktop, and now I can't help but think that the install message and the lack of unity just might be related ... :P

I'm not sure how to troubleshoot this.  Any help much appreciated!

The actual machine is a Thinkpad X201s with Intel graphics.  Over 600MB memory is assigned to the UNR virtual machine, and it has a 10GB virtual HD.

---

### Post by kerry_s on 2010-10-19
the new unity is 3d accelerated, does virtualbox do 3d?

---

### Post by quixote on 2010-10-19
I've been searching around for an answer and found [this bug report]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/614088").  Looks like it won't run in vbox at all :frown:.

Apparently, UNR-unity assumes 3D graphics and won't work without it. As one of the commenters there says, it seems crazy to assume a 3D graphics default on an OS designed for underpowered systems!  And it seems they have no intention of fixing that till the next release. :shock:

I think I'm going to post my recent genius idea on ubuntu brainstorm: check with some actual users before release... [-X

---

