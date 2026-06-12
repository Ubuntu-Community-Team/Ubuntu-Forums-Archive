---
title: "Dropped laptop, lost unreadable partion"
date: 2010-06-13
forum: General Help
---

### Post by Matt_Rapp on 2010-06-13
Hi I just dropped my laptop while it was on. It is a dual boot vista and Ubuntu machine (9.04) and Ubuntu was running at the time. The machine didn't go down and after I got done using it I shut it down normally. Now it will not come back up because grub is saying there is something wrong with the disk geometry. It did give me a command line, I forgot the exact error message but I can look it up if needed.

I tried plugging the hard drive into a different machine under a live cd but everything was in the lost and found folder (80 GB) and the folder was unreadable. I backed up the windows partition successfully using windows explorer and now have been looking at testdisk and Stellar Phoenix Linux Data Recovery ($80) for the Linux partition. I don't know if it is ext3 or ext4, I may have bumped it up to ext4 from the default ext3 during the install. Also a few files on the windows partition were unreadable, so the disk definitely has some physical damage. I'm getting a new one along with a back up system for sure after all this is over.

I got tired of figuring out testdisk so I let the paid app run its free test overnight to see if I could recovery anything before I bought it, but it got hung up on a sector halfway through.

Going forward I think I will try Photorec next and then testdisk again if that doesn't work.

Does Photorec get almost all the normal office (doc xls), music (mp3) and video files (mp4) not just pictures?

Any suggestions? A link to a good tutorial would also appreciated.

Also what is the easiest way to wipe a disk after I get everything off?

---

### Post by quixote on 2010-06-15
Photorec recovers everything despite the name.  it was written for lost photos, that's why they called it that.  However, it doesn't recover them as files, but as direct disk reads. *[Edit: or maybe not.  Maybe as numbered files.]*  You then have to go through each recovered file, which will show up as ascii text and funny characters, and copy the parts you need to new files.  Obviously, you're only going to go to that trouble for files your really really need.  If the disk geometry is really hosed, that's your only alternative, I'm afraid.  You can supposedly fix geometry with testdisk, but I think you'd have to be a disk drive engineer to know how!

This is the link I go to first for this sort of thing: [http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Your other question (different topic, so really best to put it in a different thread) is one I'd like the answer to myself.  I saw this on Lifehacker: [http://lifehacker.com/5520289/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive](http://lifehacker.com/5520289/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive).  Haven't tried it myself.  In the course of trying to find it again, I saw that Lifehacker also had a [long post on data recovery]("http://lifehacker.com/5525534/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd").  It repeats a lot of the info in my first link, but it may also be useful to have a second take on it.

---

### Post by Matt_Rapp on 2010-08-25
I recovered most of the files using a 10.10 Alpha 1 Live CD and then bought an SSD. Problem Solved!

---

### Post by quixote on 2010-08-25
Good to know.  Thanks for coming back and letting us know :D

---

