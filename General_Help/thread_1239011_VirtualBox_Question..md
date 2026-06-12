---
title: "VirtualBox Question."
date: 2009-08-13
forum: General Help
---

### Post by Roasted on 2009-08-13
At work, we run primarily a Windows network. There's something that changed between XP and Vista that we're going to need to test more. I wasn't worried about it because the plan was to skip Vista and go straight to 7 in another year or two, however, I heard that this particular change that was different from XP to Vista is the same with 7 as well.

As a result, I was going to install Vista virtually on VirtualBox on my Ubuntu home computer to do testing with.

I can set up the image to be 99% done. At that point, once I figure out this last setting for Vista/7 to play nicely, I'm good to go. But I want to back up this 99% done VirtualBox Vista Image so when I screw it up, I can just revert straight back to before.

If I throw a "Backup" folder in the .virtualbox folder and copy the Vista virtual hard drive to that folder, then mess with Vista for testing purposes and screw it up, can I just delete the messed up Vista virtual hard drive, copy the 99% done one back to the same place the messed up one is and be back in business?

---

### Post by niteshifter on 2009-08-13
Hi,

Yes you can do that - just copy the .vdi file. Be aware that you cannot run, or have the two .vdi files where VirtualBox can see both of them.

Easier - and quicker is to use VirtualBox' snapshot feature.

---

### Post by Menthu_Rae on 2009-08-13
> **Roasted said:**
> At work, we run primarily a Windows network. There's something that changed between XP and Vista that we're going to need to test more. I wasn't worried about it because the plan was to skip Vista and go straight to 7 in another year or two, however, I heard that this particular change that was different from XP to Vista is the same with 7 as well.

As a result, I was going to install Vista virtually on VirtualBox on my Ubuntu home computer to do testing with.

I can set up the image to be 99% done. At that point, once I figure out this last setting for Vista/7 to play nicely, I'm good to go. But I want to back up this 99% done VirtualBox Vista Image so when I screw it up, I can just revert straight back to before.

If I throw a "Backup" folder in the .virtualbox folder and copy the Vista virtual hard drive to that folder, then mess with Vista for testing purposes and screw it up, can I just delete the messed up Vista virtual hard drive, copy the 99% done one back to the same place the messed up one is and be back in business?

Yes, pretty much. I have 2 copies of a virtual machine - one on my Desktop PC and one on my laptop. All I did was copy the "YourNameHere.vdi" file to the other PC, set up a VirtualBox guest with the same settings and add in the copied "YourNameHere.vdi" file as the primary hard disk.

There are other, better, perhaps more "proper" ways of moving Virtual Guest's or backing them up - but this method has worked fine for me so far.

As it stands though - your idea should work fine. :)

---

### Post by Roasted on 2009-08-13
> **niteshifter said:**
> Hi,

Yes you can do that - just copy the .vdi file. Be aware that you cannot run, or have the two .vdi files where VirtualBox can see both of them.

Easier - and quicker is to use VirtualBox' snapshot feature.

Hmm, really? That sounds promising. What kind of time is involved with backing up a snapshot vs restoring it? (if any)

I'm just trying to find the absolute quickest way to do this because when I make changes that don't work, that image is 100% useless to me due to how Windows Vista/7 corrupt the user profiles based on modified changes I'm trying to make.

---

### Post by asmoore82 on 2009-08-13
**[SIZE="4"]+1[/SIZE]** for Snapshots.
They are quick and "stackable" and when you are done with them,
you can "Revert" them which discards all of the changes.
You can also commit the changes permanently - I can't remember what Vbox calls this.

---

### Post by Roasted on 2009-08-13
Awesome. Thanks doods!

---

