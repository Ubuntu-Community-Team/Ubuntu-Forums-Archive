---
title: "Migrate data from freenas to ubuntu server"
date: 2011-09-17
forum: General Help
---

### Post by Nimbu on 2011-09-17
I have been running freenas for a while now and while I can't complain too much about it, I would like to run a ubuntu server installation instead for extra flexibility. 

I have 2 ufs 500gb separate storage drives in my freenas box. I somehow need to transfer the data onto a 2tb external hard drive. And finally, restore the data after the ubuntu installation onto 2 ext3 or ext4 formatted disks.

What would be the best way to get my existing data onto my external hard drive and what filesystem format should it use? Would it be unsafe to simply copy the shared folders over the network (gigabit connection) onto the external hard drive?

---

### Post by tgalati4 on 2011-09-18
You should have a decent backup solution so that any file losses due to network transfer would be covered.

Can you plug the external HD directly to the freenas box? If so, then just mount it, format it as ext3 (I'm not sure if freenas supports ext4) and do a local copy of your data on the freenas box.

If you don't have a decent backup, then I wouldn't risk converting a working freenas box.  Instead, I would find another machine to set up the Ubuntu server.  One you have it running and your services set up, then you can do a network transfer of the data.  That way you still have a working freenas and backup and you won't mess up your shares with constant tweaking of the server.  Once you have the server running the way you want, then you can migrate the shares over.

My personal feeling is to never trash a working system.  Set up a new system, then retire the old system and repurpose.

---

