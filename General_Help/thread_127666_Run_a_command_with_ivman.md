---
title: "Run a command with ivman"
date: 2006-02-09
forum: General Help
---

### Post by foof on 2006-02-09
I have two truecrypt drives in my system, I want them to be mounted when I insert an USB storage device, can I do this with ivman?

If so, can someone help me and explain how?
I want it to execute a script that is located on the actual usb device, so
it must first mount the usb device then execute the script on it.

I have a hard time finding any info about how to edit ivman conf files, can someone guide me in the right direction?

One more thing, I seem to have a little problem with ivman now.
When I insert my USB-memory Konquerer opens and says it cant find:
media:/sda2

Why? I can access it though from /media/cruzerdrive
Thanks!

---

### Post by foof on 2006-02-10
After doing:
sudo aptitude update
sudo aptitude upgrade

The automounting behaves a little different.
Now it Konquerer tries to open system:/media/sda2
But show only a blank page. If I reload the page it says:
Couldn't mount device. According to mtab /dev/sda2 is already mounted at /media/sda2

And it is, I can access my files at /media/sda2.
But why can't I access it at system:/media/sda2 ?

---

