---
title: "Program to Backup Across DVDs?"
date: 2010-03-09
forum: General Help
---

### Post by cforput on 2010-03-09
Back in the DOS days (yes I am dating myself) there was a backup command that would back the selected files across a series of floppy disks. Is there such a command in Karmic to backup across multiple DVDs?

I would like to do some backups of my data and other important files but I have more than 4 GB of information. I have seen posts on ways to write a compressed file but that still stores it on the HDD and I would like the files on DVDs in case the HDD crashes.

---

### Post by richardjh on 2010-03-09
You can use tar to do this you need to look at the -L option in the man page to set a "tape length".
This will split the backup across multiple DVDs.

The data wont be readable on disk though and you will need to extract the backup back to hard drive for restoring files.

Another option is [discspan]("http://sourceforge.net/projects/discspan"). I have never used it but appears to do what you want.

---

### Post by Letrazzrot on 2010-03-09
What about dar?  I've only used the command line version, but supposedly there are gui applications built around it, as well.

[http://dar.linux.free.fr/](http://dar.linux.free.fr/)

---

### Post by cforput on 2010-03-26
Wow, why is everything in Ubuntu (linux) SO complicated. I looked at both discspan and DAR. By the time I read through everything and figure out how to use it, I can do what I usually and that is to look at the directories and manually figure out which ones to consolidate to a single DVD, drag those directories over to the DVD drive and write the files to the DVD. 

Isn't there anything simple out there? All I need is something that:

1. Allows me to input the directory I want to backup (with everything under it)
2. Tell it where to back it up to
3. Start copying files to the destination (DVD in my case) 
4. Each time it get ready to copy a new file, verifies there is enough room. If there is then copy the next file. Loop until full
5. Once there is no more room, burn the DVD
6. Prompt for a new DVD.
7. Repeat until all files have been copied. 

If I knew how to program, I would!

I don't need any special formats which means I won't need any special programs if I need to restore. 

Maybe I didn't ask the right way the first time. Isn't there something that a dummy like me could use without having to read pages and pages of stuff that doesn't make sense and I don't care about?

---

### Post by macogw on 2010-03-26
Mondo/Mindi are for bare-metal recovery onto a series of DVDs, though I've never used them (I backup to a secondary hard drive figuring both won't die at once).

---

### Post by ReturnPrivacy on 2011-09-26
Hi, has anyone figured out how to burn a lot of files across spanned DVDs yet? I looked at the page for DiscSpan, but it says "DiscSpan 2.2.tar.bg" or something similar. I looked all over the page and couldn't find any instructions on how to install it? All I know how to do is the apt-get install thing or the synaptic program finder. Can anyone explain how to install DiscSpan? I think it is just an add on for Brasero burner? I'm surprised I couldn't find any instructions anywhere on DiscSpan and how to  install it? Does this program even work?
Thanks.

---

