---
title: "User Restrictions"
date: 2009-11-24
forum: General Help
---

### Post by hellouthere on 2009-11-24
Hi, can't find any topics on the internet from people with an identical problem to me.

I'm setting up 5 pc's in a youth group for users to access the internet and possibly do some word processing.

This is ALL I want them to be doing so want to restrict all permissions and block any workarounds for changing preferences, backgrounds, screensavers, screen resolutions etc. I definately don't want firefox proxy settings fiddled etc.

The guest account on 9.10 doesn't seem very restricted and offers far more freedom than I would like. The room needs to look smart so we can't have changed screensavers and backgrounds.

Is there an easy way to restrict nearly everything for one account? I literally just want them to be able to login, browse the internet, word process and save to memory sticks.

I realise I may have to use multiple methods to restrict everything but i have no idea where to start!

Thanks in advance,

Mark Eisner

---

### Post by Darael on 2009-11-24
I have little experience here, but [http://library.gnome.org/admin/deployment-guide/](http://library.gnome.org/admin/deployment-guide/) should have just about everything you need.  Well, you'll need to set a password on your BIOS settings, boot device selector, and grub alternatives as well, so that they can't boot from another device, or boot into single-user mode from grub, without knowing the passwords.

---

### Post by hellouthere on 2009-11-24
That looks like exactly what I need, I'll have a closer look soon. Thanks for the help and the lightning ninja like reply.

---

### Post by Darael on 2009-11-24
No probs - though you may find the GRUB lockdown gives you a little trouble.  Just a heads up.  It was easy enough in grub 1, but I'm having trouble locating documentation on how to do it in grub2, which is the Karmic default.

---

### Post by hellouthere on 2009-11-25
thanks very much, i'm just playing with lockdown on a virtual machine at the moment to give a demo to the client.

---

