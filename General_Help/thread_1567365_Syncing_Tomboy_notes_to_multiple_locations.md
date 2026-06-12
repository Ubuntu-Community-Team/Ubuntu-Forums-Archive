---
title: "Syncing Tomboy notes to multiple locations"
date: 2010-09-03
forum: General Help
---

### Post by FuturePilot on 2010-09-03
Is there a way to sync Tomboy notes to multiple locations? I would like to be able to sync them to my UbuntuOne account and at the same time to my local NFS server, but from the looks of it Tomboy only lets you choose one location for syncing. Maybe there's a workaround for this or something?

---

### Post by gldearman on 2010-09-03
Does this help?

[https://wiki.ubuntu.com/UbuntuOne/Tutorials/Notes#Setup%20Tomboy%20to%20sync%20with%20Ubuntu%20One]("https://wiki.ubuntu.com/UbuntuOne/Tutorials/Notes#Setup%20Tomboy%20to%20sync%20with%20Ubuntu%20One")

---

### Post by FuturePilot on 2010-09-03
> **gldearman said:**
> Does this help?

[https://wiki.ubuntu.com/UbuntuOne/Tutorials/Notes#Setup%20Tomboy%20to%20sync%20with%20Ubuntu%20One]("https://wiki.ubuntu.com/UbuntuOne/Tutorials/Notes#Setup%20Tomboy%20to%20sync%20with%20Ubuntu%20One")

No, I already know how to set that up. Thanks though. 
I want to be able to configure two syncing locations.

---

### Post by sgosnell on 2010-09-03
The Tomboy notes are just in a folder.  There are several ways to sync them, including rsync.  I sync mine to Dropbox.  You can tell Tomboy where to put its files, and sync that folder to anything.  I think a cron job using rsync would work for syncing to your nfs server.

---

### Post by FuturePilot on 2010-09-03
> **sgosnell said:**
> The Tomboy notes are just in a folder.  There are several ways to sync them, including rsync.  I sync mine to Dropbox.  You can tell Tomboy where to put its files, and sync that folder to anything.  I think a cron job using rsync would work for syncing to your nfs server.

That probably would work, however I have multiple computers that sync to the NFS server and rsync can be dangerous in that situation. But that does give me an idea. Maybe Unison can be used instead of rsync.

---

### Post by tgalati4 on 2010-09-03
I like zim for notes.  You can set up zim on one machine and then run it on remote machines and multiple instances across several machines and it seems to work fine.  Updates to individual notes automagically get propagated to all instances of zim running on client machines.

ssh user@remotemachine zim &

It's easy to create a launcher on your desktop that runs the above command.  You can also add it to your bootup script.

To install:

sudo apt-get install zim

---

### Post by sgosnell on 2010-09-04
If you want to sync your Tomboy notes to multiple computers, the easiest thing is to use something like Dropbox.  I do that to sync mine.  I also use Dropbox to sync files to multiple computers, including Windows boxes.  UbuntuOne might do that automatically, but I've never used it.  I need to sync to Windows computers, so Dropbox works for me.  I even get my Tomboy notes on the Windows computers, for what it's worth.  If UbuntuOne syncs to multiple computers, just put your Tomboy notes there and you should get what you need.

---

### Post by FuturePilot on 2010-09-05
> **sgosnell said:**
> If you want to sync your Tomboy notes to multiple computers, the easiest thing is to use something like Dropbox.  I do that to sync mine.  I also use Dropbox to sync files to multiple computers, including Windows boxes.  UbuntuOne might do that automatically, but I've never used it.  I need to sync to Windows computers, so Dropbox works for me.  I even get my Tomboy notes on the Windows computers, for what it's worth.  If UbuntuOne syncs to multiple computers, just put your Tomboy notes there and you should get what you need.

I want to use UbuntuOne, but I also still want to have them synced locally. Basically I want some redundancy. Say for whatever reason I can't sync to UbuntuOne. (UbuntuOne down, my connection down, etc.) and I needed to sync my notes, well I'd pretty much be out of luck. The way I have it now I could still sync them without an internet connection since it's a local server on my network.

---

### Post by sgosnell on 2010-09-05
If you sync to UbuntuOne, it puts the files on your local machine(s), so you have the redundancy.  But if you want more, there are ways to do it.

---

### Post by jcoles on 2013-03-06
sgosnell, can you provide some detail about how to do this? 

AFAIK, on both Ubuntu and Windows PCs you somehow have to get Tomboy to store its files in the Dropbox folder. The user interface for Tomboy does not provide for configuration of the storage location. There's currently nothing in ~/.config/tomboy that explicitly sets the storage location. I find the notes files in ~/.local/share/tomboy. A symlink from here to the Dropbox folder might work in Linux, but Windows has no symlinks. 

How did you do it?

---

### Post by overdrank on 2013-03-06
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

