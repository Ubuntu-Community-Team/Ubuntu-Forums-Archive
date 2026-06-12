---
title: "Photorec stuck on sector.  Can I bypass?"
date: 2012-08-05
forum: General Help
---

### Post by Accessory on 2012-08-05
I have an Acer laptop that was formatted and also failing with lots of bad sectors. I've tried several tools, but nothing makes it through - locks up consistantly on certain sectors. Photorec is most likely my last hope. 
 
I know there are good parts of this drive, you can see the newly formatted drive/file/folders when hooked up to a Windows or Linux computer - takes a long time to populate files/directories due to the failing drive though. The fact this was formated will make data recovery difficult.
 
My question: Photorec gets stuck on certain areas of the drive. I've read that there might be a hack in the photorec.ses file. It's suppose to store the sector it left off at so if you need to restart photorec again it'll remember where you were. 
 
Can anyone help me change the photorec.ses file to skip the bad areas of the drive so it won't get stuck again. I figured I could note the sector it's stuck on, stop the program, edit the photorec.ses file and restart up again after the failing sectors. 
 
Hopefully someone can help. I've got a lot of hours into this and I just want to finish it up. Thank you!!

---

### Post by Accessory on 2012-08-07
I'm not having much luck.  I've searched all over the web to find out how to change the start sector, but nothing very clear on whether it works or how to do it.  Anyone?  Hack the photorec.ses file?
 
I just restarted another scan and selected jpgs only this time. Maybe this will go all the way through since it's just looking for 1 file type.  But I still would like to know how to alter the photorec.ses file. Sure would make a difference when trying to recover data on a crashing hard drive - would be a lot less frustrating and less of a waste of time.

---

### Post by sandhill on 2012-11-01
That's interesting thought about modifying the ses file.

But I would like a way to ask photorec not to do so many tries when it is having trouble reading a sector.

How is the number of tries set?

Because when a disk is failing, too many tries at reading a failed sector may wear it out before it gets to look at what had still been readable sectors.

Is it possible to make a copy of a disk ignoring that some data is errors and just write the whole  disk?

Silly me I thought to try whether clone might do something like that on a 40gb failing disk. I thought that bootmed would give me an option as to where it would clone! It did not warn me that it was going to overwrite my 1000gb storage disk.

Now I am trying to recover that disk too. Photorec stops without comment about 40% through or less.

I have tried twice, having difficulty trying to get it to access the ses file. It wants to start from the beginning each time.

---

