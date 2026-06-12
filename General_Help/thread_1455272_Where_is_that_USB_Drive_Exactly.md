---
title: "Where is that USB Drive Exactly?"
date: 2010-04-15
forum: General Help
---

### Post by oldefoxx on 2010-04-15
Here is an odd one.  I use VirtualBox with Ubuntu, and of course there is no forum I know of that addresses issues between the two.  Most would say that it must be a VirtualBox problem, but part of it relates to how Ubuntu acts, and i don't see any leverage point with Ubuntu to undo the state that comes up.  So that is what I want to speak to.

You plug in a USB Drive and power it up, and Ubuntu sees it, right?  You may not be authorized to mount it, but you use your password to deal with that.  Two pages then tend to open up, one with a list of all drives or partitions by label, and another of the contents of the USB drive as seen from its root.

At this point VirtualBox is able to link the USB drive to a client, assuming that the Settings have enabled it to do so.  The links are by the bridge or adapter designations rather than the drive designations, but you can experiment or work out which one is involved.  Now the client can access the USB drive.  But this is in place of doing anything with it in Ubuntu, a way of protecting the drive from multiple operations from two sources.  So that is good.

But something is getting lost somewhere.  Ubuntu sometimes closes that second page, sometimes leaves it open.  The client may initially see the USB device. but on a reboot of the client or something, will not get it back again.  VirtualBox won't change settings as long as the client is active, and may still let you set or clear a USB setting if the client is shut down, but Ubuntu can't seem to see the device at all any more.  I mean it is wierd.

Now all I am wondering is, what do I have available under Ubuntu to see where I stand with that USB device and get it back on track?  If I turn the device off and on, or unplug and plug it in again, I can get around the problem.  But what do I have for actually checking on and managing the attached USB devices?  It could be a big help here.

---

