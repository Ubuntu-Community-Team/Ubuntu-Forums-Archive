---
title: "Recover Data from Network Drive."
date: 2011-06-17
forum: General Help
---

### Post by kaspar_silas on 2011-06-17
Help, please.

I have a 1Tb Western Digital Network drive.

I was showing someone the photos on this on their XP computer and noticed that each file also had a capitalized version beside. I assumed this was a copying mistake and highlighted all the capitalized copies and deleted them. 

To my horror all files have vansihed. The next horror came in that XP apparently doesn't move deleted files to the recycle bin it just  deletes them.

I rapidly went back to my ubuntu machine and mounted the network drive. However none of my normal recovery file methods work on network drives.

PhotoRec doesn't list the drive.

and 

sudo ddrescue -r 3 ~/.gvfs/SFTP\ for\ [myname]\ on\ [address]/[path] ~/LOGFILE 

tells me permission is denied.

Is their any hope?

---

### Post by kaspar_silas on 2011-06-17
O incidentally if anyone knows a way to make a network drive appear as a normal drive that would also be good. Then I could just use photorec as normal.

I guess somewhere there is a file specifing the internal hard disks. Could I alter this and make a symbolic link between some /dev/[] and the mount at ~/.gvfs.

Would that work? It that a dangerous thing to do?

---

### Post by kaspar_silas on 2011-06-23
Okay so no one offered any help and I just couldn't work out an elegant fix to the problem myself. Not really ubuntu forums finest hour. But hey you can't win them all. 

Anyway, technically I have solved the problem. Basically I ripped apart the network drive and physically mounted the drive. Then ran forensic recovery (photorec) as normal. Resulting in -1 network capable drive but +4 previously lost jpgs.
 
So if you have found this thread as you have encountered a similar problem. In short, your screwed.

---

### Post by WantSomethingNew on 2011-09-13
I know this thread is marked as [SOLVED] but I thought I'd throw this in in case it works.  Perhaps it doesn't for me, but inspires someone smarter than me...

I too have a network drive from which I accidentally deleted files from.  In my case, they were backup files of family photos and videos.  You know, the kind of stuff you grab as you run out the door when your house is on fire.  Not the kind of stuff you accidentally delete during a moment of stupidity!

So here's what I've done so far, and all is looking promising.  I'll re-post later as a follow-up to note success or failure, whichever it turns out to be.

I followed [this guy's solution]("http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/") for mounting a network drive.  I've done this before on other Ubuntu systems in my house and it works for me so far.  After that I installed "testdisk" from the Software Center and ran "photorec" from terminal.  Photorec seems to have found my mounted drive and is crunching away.  It says it still has nearly 5 hours of work to do, so I'll check back tomorrow.

This is the first time I've added my 2-cents to the forum!  Thanks to all of you who know so much that have encouraged me to make the switch from Windows and make Ubuntu work!

---

### Post by WantSomethingNew on 2011-09-13
Elapsed time: 20h 38min and counting.  Not done yet...  Not sure how much longer it's going to take.

---

