---
title: "Any changes made as user are not saved"
date: 2011-03-27
forum: General Help
---

### Post by decomp on 2011-03-27
Hello!

I recently installed a base system from a 10.10 alternate cd and then selected a few packages to build myself a light install. 

I'm using lxdm as my login manager (desktop manager) and openbox as my window manager, with lxpanel and nm-applet autostarting after loading openbox. that's it so far.

My problem is that almost any changes I make as a user are not saved. ie I tried to make a wireless network available to all users with network manager but it immediately reverts. I tried to make changes to permissions through the gui 'users and groups' tool, (with i installed visa gnome-system-tools package in synaptic) but all changes are immediately forgotten. 

I also cannot mount another partition using pcmanfm. I get the response 'authentication is required.' any ideas?

These sound to me like permissions issues. what groups do I need to be a part of?

Thanks!

update: I checked my groups and I wasnt a member of any so I googled around for whats normal and added myself. Im now a member of the groups:
```
adm disk dialout cdrom sudo audio www-data video plugdev games users fuse lpadmin admin netdev
```

But still nothing. changes are not remembered.

---

### Post by decomp on 2011-03-27
I suspect this might be due to my openbox session not being started by lxdm with console kit, but I cannot find how to edit this.

---

### Post by dragonfly41 on 2011-03-27
I installed Ubuntu 10.10 *inside* my Vista configuration using Windows installer and Grub dual boot through Vista (when it was working) and not in a separate partition .. just to experiment with Ubuntu.   Ubuntu was a lifeline since Vista soon crashed on me.

I've been switching into Ubuntu demo mode each time I boot up (to avoid a full installation of Ubuntu which might erase my Windows files).   In "demo mode" all my sessions are lost each time I reboot .. but I would expect that in demo mode.

I guess you are saying that in a full Ubuntu installation you are losing session data?   I have not got as far as a full Ubuntu installation yet so can't comment on that.

---

