---
title: "Drive persmissions? Losing my marbles here..."
date: 2010-04-15
forum: General Help
---

### Post by aHarmony on 2010-04-15
First off, Hello! I'm a new Linux user...had it with Windows and decided to go with Mac as my main desktop, but wanted to do something useful with my PC so it's now a file server running Ubuntu.

Naturally, I wanted to run before I could walk (I thought I'd figure it all out, but I'm stuck now!), and got NetaTalk (The Apple AFP server package for Linux) working, however my shares/hard drives are NOT letting me do anything with them - by that, I mean I cannot copy or save files onto any of my multiple file shares from the Mac OR directly on the server box!

From the server box, when I try to copy a file or save something, I get a message saying "You do not have permissions to create it in the destination", in regards to the folder I'm trying to copy into it. I realize this is probably something stupid that my newbness is making me overlook - I'm logged in as my admin account - the only one configured. 

From the Mac (on which the shares ARE totally readable and viewable), same thing - can't put a single file on the share, as it says "You don't have permission to do that"

So, it's not my NetaTalk share configuration because it won't work on the server either...

What could this be? How do I go about releasing my shares/drives from utter uselessness?

Thanks so much in advance.

EDIT: Also, my one NTFS drive/partition is giving me a different error: "only root can mount /dev/sdc1 on media/hexDATA2"   - I started to try to auto mount the drive, but it won't let me mount it as you can see! :(

EDIT2: Solved! I feel like an idiot...I was trying to chown the drives, not the mounts!

---

