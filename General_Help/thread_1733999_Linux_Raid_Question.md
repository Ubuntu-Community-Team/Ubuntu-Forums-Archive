---
title: "Linux Raid Question"
date: 2011-04-19
forum: General Help
---

### Post by hothail on 2011-04-19
I use mdadm for raid.

Right now, what I do is swap out my linux hard drive with a windows one for other reasons. I unplug my raid drives though.

Now, when I boot linux back up, my raid drives always go into recovery mode and seem to resync everything from scratch. 

Is this normal? Or is there anyway I would be able to stop this? There is no reason for them to resync from scratch when nothing happened to the drives when they were powered off.

---

### Post by hothail on 2011-04-20
Bump. Anyone know what would cause a recovery for raid?

---

### Post by blueridgedog on 2011-04-20
There may be a power off flag or some such issue with SMART monitoring that knows they have been powered off and disconnected.  Just a guess.

---

### Post by hothail on 2011-04-20
Ah alright. Would there be a way to shut off this check?

---

### Post by blueridgedog on 2011-04-20
Is this any help?

[http://arstechnica.com/civis/viewtopic.php?f=16&t=1114990#p20565587](http://arstechnica.com/civis/viewtopic.php?f=16&t=1114990#p20565587)

---

### Post by hothail on 2011-04-20
Yes thank you, this is the first bit of useful information I've read about this.

---

### Post by blueridgedog on 2011-04-21
I think you can configure mdadm so that you do not get the rebuild, but I am just researching along with you.  I have not used it (I generally use hardware raid).  Perhaps a forum member that has more experience with it will chime in.

---

### Post by hothail on 2011-04-22
Hopefully, a concise answer to this would be great. Googleing doesn't seem to lead to a specific answer for this...

---

### Post by deconstrained on 2011-04-22
This seems like an unusual problem with an unusual cause, so my best guess is that it's a hardware-related issue along the lines of what blueridgedog suggested already.

I will say this, however: you don't have to unplug your RAID drives unless you're concerned about the extra power they consume idling as you use Windows. As long as you don't touch them while booted to Windows they should be just fine.

---

### Post by hothail on 2011-04-22
Oh thanks, I was concerned that windows would alter them in some way which would cause the recovery. Maybe it really is due to me unplugging them. I'll have to test this out at some point.

---

### Post by deconstrained on 2011-04-23
Nah, it shouldn't have affected them. I've set up RAIDs using Ubuntu and then moved them to an Arch Linux machine, and they worked just fine and didn't need to resync. Something unusual is definitely happening.

---

### Post by hothail on 2011-04-25
Yeah, well it must have been due to me unplugging them. I plugged all the hard drives back in the other day, and ran windows like usual.

Booted up linux just about an hour ago, and it didn't need to resync.

This is solved, just don't unplug your raid drives haha :)

Thanks for your help guys!

---

