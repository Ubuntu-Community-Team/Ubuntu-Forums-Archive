---
title: "Ubuntu erasing my text files"
date: 2011-07-12
forum: General Help
---

### Post by Steve Warner on 2011-07-12
I have been having trouble with Ubuntu apparently erasing text files that I have been working on via Open Office. 

This morning, when I tried to open an rtf file that I'd been working on just an hour earlier, I got a message asking about ASCII Filter Options.  When I hit "Cancel", nothing happened.  Clicking on "Help" was ... well, no help. 

I did NOT click on "OK" since something like this had happened to me some months before, when I was writing into an .odt file. That time, clicking on "OK" gave me a single blank page ... which was all that was left of what had been twenty-plus pages of text.    Since then, I have been writing exclusively in .rtf, and making sure I had a back-up copy of the file elsewhere on the hard drive. 

Well ... this morning, I opened the file, worked on the text a bit, backed up the file as per usual, and printed out one page of the text.    I closed the file, did some other work, and when I came back to re-open the .rtf file ... there was that same old ominous message asking about ASCII Filter Options.    I did a quick check and discovered that my file AND the back-up were showing 0 Bytes. 

Is there anyway to to recover what I've lost?  And if not, is there anyway to keep this from happening again? 

On a possibly related matter:  I have recently had trouble getting Ubuntu to shut down.  I click on "Shut Down", but Ubuntu just sits there for a while and then restarts instead.  This has been an intermittent annoyance that has been increasing of late.            

Any suggestions?  Thanks!

---

### Post by mali2297 on 2011-07-13
Just a far-fetched thought... 

Might you be using some other file system than ext3 or ext4?

---

### Post by Steve Warner on 2011-07-13
> **mali2297 said:**
> Just a far-fetched thought... 

Might you be using some other file system than ext3 or ext4?

I don't know what that means.  What is "ext13 or ext14"?

---

### Post by proma on 2011-07-13
> **Steve Warner said:**
> I don't know what that means.  What is "ext13 or ext14"?

It's a unix-like file system, like NTFS or FAT in windows. Type this in a console:
```

df -T

```

---

### Post by psusi on 2011-07-13
It sounds like your system is crashing when you try to shut down, and thus, didn't save the file.  You really should find and fix that problem.

As a workaround, either run "sudo sync" in a terminal to force everything to be flushed to the disk, or hit alt-sysrq-s after you have saved the file.

---

