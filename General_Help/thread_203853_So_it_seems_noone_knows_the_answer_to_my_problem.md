---
title: "So it seems noone knows the answer to my problem"
date: 2006-06-26
forum: General Help
---

### Post by Drifter on 2006-06-26
I can't backup my files in quicken, gnucash, kmymoney or anything else.  I need to know how to backup to a cdrw drive using a formated rwdisk.  If you read this and u don't know how say it, what I get is 0 replies.  If there is a how to, I will be glad to go to it if you will point me there.

---

### Post by aysiu on 2006-06-26
So this really has nothing to do with Quicken, Gnucash or KMyMoney, right?

You're essentially asking, "I already have a CD-RW that I've burnt sessions to. How can I add a new session?"

Right? Is that the question?

Also, can you explain what you have tried and what errors you've received, if any?
In the meantime, you may also want to take a look at [this thread](http://www.ubuntuforums.org/showthread.php?t=203811).

---

### Post by jason.b.c on 2006-06-26
[QUOTE=aysiu]
You're essentially asking, "I already have a CD-RW that I've burnt sessions to. How can I add a new session?"

Right? Is that the question?

Also, can you explain what you have tried and what errors you've received, if any?
In the meantime, you may also want to take a look at [this thread](http://www.ubuntuforums.org/showthread.php?t=203811).[/QUOTE]

It dosen't look like he asked that question at all **Aysiu**..:confused:

---

### Post by Drifter on 2006-06-26
Yes it has to do with all of them, I have tried all, but I can't get the backup feature in any of them to work with my cdrw drive or a floppy drive for that matter.

---

### Post by aysiu on 2006-06-26
[QUOTE=Drifter]Yes it has to do with all of them, I have tried all, but I can't get the backup feature in any of them to work with my cdrw drive or a floppy drive for that matter.[/QUOTE]
Any error messages? Can you be specific about what happens other than "I can't"?

---

### Post by Drifter on 2006-06-26
Yes when I try to backup a message pops up and tells me that I can't access this drive.  I will try again and put the message on as it appears. This is what appears:  Unable to access the disk in drive z.  Please make sure the drive is ready and not write protected.

---

### Post by aysiu on 2006-06-26
Before you even back up, can you access the drive just to read it?

In other words, you put the CD-RW in the CD drive. Does it appear on your desktop as a CD icon? If so, can you see the contents that have already been written to it?

---

### Post by Drifter on 2006-06-26
Yes, I can see the contents and there is an icon on the desktop with the contents in it.

---

### Post by aysiu on 2006-06-26
Okay. So the drive is "ready," then.

Can you walk through the steps of how you're trying to add a session?

---

### Post by Drifter on 2006-06-26
As u may know each program like kmymoney etc has a backup under file.  When I click on that it wants to know where to backup to.  I browse to the drive that has the backup disk in it and it gives that message that I put above.  It also does the same thing if I try floppies.

---

### Post by Drifter on 2006-06-26
Aysiu, I want you to know that of all the people in here you have helped me the most with your directions to how to's etc.  But this drive problem has me completley stumped.

---

### Post by croak77 on 2006-06-26
What program are you using to burn a CD?

---

### Post by Drifter on 2006-06-26
It is not that I can't burn a cd, it is that I can't backup using the backup that is in kmymoney, quicken and gnucash, u know programs that have a backup feature under file.

---

### Post by croak77 on 2006-06-26
Can't you save to a file on your hard drive and then burn to a cd?

---

### Post by Drifter on 2006-06-26
I can do save to harddrive, but that defeats the purpose of the program, and will eventually fill up the harddrive would'nt it, I really don't know for sure about that.  But the quick answer to your question is yes.

---

### Post by croak77 on 2006-06-26
I couldn't see a 'backup' option in gnucash just Save or Save As. Am I missing something there?

---

### Post by Drifter on 2006-06-26
Well gnucash don't have a backup you are right, kymoney how ever has one, it is at present greyed out because i have nothing in my drive.  But it will not backup.  Quicken with crossover office to run it with works, but the backup feature will not work in it either.

---

### Post by croak77 on 2006-06-26
Well I'm not sure if all features of Quicken will work with Crossover or Wine. It's not designed with Linux in mind. Where is the Quciken data saved?  .wine/drive_c/Program\ Files/Quicken/Quicken_Data ? Or something like that?

---

### Post by Drifter on 2006-06-26
Yes itis saved in that directory, but I can't backup from there either.  How I can burn to disk, but I what I have is a formated rw, would it be better if I jsut used a blank rw and burn from a file in my home dir.

---

### Post by croak77 on 2006-06-26
Yes...it wouid be much easier to save to $HOME and burn from there. You could try making a symlink from .wine/drive_c/Program\ Files/Quicken/Quicken_Data to your save directory on $HOME but I have no idea if that would work or not. You might want to check the Codeweavers site and see if there is a solution there.

---

### Post by Drifter on 2006-06-26
Thank you I will give it a try.

---

