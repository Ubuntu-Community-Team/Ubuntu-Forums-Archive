---
title: "Editing and saving documents on cd"
date: 2012-04-11
forum: General Help
---

### Post by eve40 on 2012-04-11
One difference I've noticed between my laptop (Ubuntu) and my desktop (Windows XP) is that, using my desktop, I can open documents on a cd, edit them and save the changes to the cd without having to re-save ALL the documents on the disc. But, using Ubuntu, I can't seem to do that. Is there a specific setting that's missing on the writer itself or is there something else I can do to allow for editting cd documents? I find it so much easier than having to reload everything just because of one document change. I am a complete amateur when it comes to Ubuntu, although I'm not doing to bad in my opinion lol. Any help would be appreciated!:p

---

### Post by roelforg on 2012-04-11
> **eve40 said:**
> One difference I've noticed between my laptop (Ubuntu) and my desktop (Windows XP) is that, using my desktop, I can open documents on a cd, edit them and save the changes to the cd without having to re-save ALL the documents on the disc. But, using Ubuntu, I can't seem to do that. Is there a specific setting that's missing on the writer itself or is there something else I can do to allow for editting cd documents? I find it so much easier than having to reload everything just because of one document change. I am a complete amateur when it comes to Ubuntu, although I'm not doing to bad in my opinion lol. Any help would be appreciated!:p
 
That has to do with the way windows burns disks.
First you work on the "CD" just like when you work on a usb drive.
Then you select Burn to save the "Folder" to cd,
if you don't, it's kept somewhere to be used later on.
In linux that mode isn't there (one could write a fuse-based implementation for this, but then people will ask why their stuf isn't "saved"),
you work in a local folder and then reburn the disk (assuming you have a rw disk and burner).

---

### Post by eve40 on 2012-04-11
So basically, what you are trying to tell me is, it can't be done on Ubuntu as on Windows? That is a pity, but I guess a person has to adjust to your circumstances. Thanks so much for the input. If you do, by any chance, find a way to change these settings please do let me know! :)

---

### Post by Mark Phelps on 2012-04-11
That's possible in MS Windows because they have special drivers that allow you to treat R-W optical media as if it is a live filesystem.  Those drivers (as far as I know) don't exist for Linux, so you are forced to burn "sessions" to the optical media instead.

---

### Post by roelforg on 2012-04-11
> **eve40 said:**
> So basically, what you are trying to tell me is, it can't be done on Ubuntu as on Windows? That is a pity, but I guess a person has to adjust to your circumstances. Thanks so much for the input. If you do, by any chance, find a way to change these settings please do let me know! :)

You didn't read my post.
It can be done,
but it is a lot of work.
This has to do with the differences between the way win presents the cd and how linux does it,
as folder (win) or as device (linux)..
There's no "setting" for this.
Try google, someone probably already did create a fuse-cd-fs thingy.

---

