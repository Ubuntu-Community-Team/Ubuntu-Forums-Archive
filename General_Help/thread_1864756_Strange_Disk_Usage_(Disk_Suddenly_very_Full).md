---
title: "Strange Disk Usage (Disk Suddenly very Full)"
date: 2011-10-19
forum: General Help
---

### Post by jiewmeng on 2011-10-19
Just today, ubuntu says the OS drive is out of space. I was surprised ... my OS partition is 60GB with only programs. I looked at disk usage and it looked strange 

[IMG]http://i.stack.imgur.com/aEIEt.png[/IMG]

Why is my home folder using 58GB when the files are smaller relative? The biggest few files only add up to ~1.5GB. Then looking that there are 72 files in /home/jiewmeng, the rest of the few KB files cant add up to even 1GB I suppose?

[IMG]http://i.stack.imgur.com/ucG7L.png[/IMG]

[IMG]http://i.stack.imgur.com/7o8pz.png[/IMG]

[B]UPDATE

[/B]I identified the problem using ls -lah ... 

-rw-------  1 jiewmeng jiewmeng  58G 2011-10-19 20:38 .xsession-errors.old

Can that be deleted? Why is that file so big? Whats it for?

---

### Post by ArgusVision on 2011-10-19
Sounds like you have a program that is generating a lot of files. Did you install an automatic backup program or the like?
I had a similar problem once when I set up an application to make automatic backups, and boy did it ever.

---

### Post by ArgusVision on 2011-10-19
If I remember correctly xsession-errors.old is a log file of errors with your graghical display. Apparently, you're generating an amazing number of errors.

---

### Post by ArgusVision on 2011-10-19
My .xsession-errors and xsession-errors.old list several gtk applications and conky errors. Have you installed a new application recently?

As far as deleting the file is concerned I don't think it should cause any issues, but you may fare better by overwriting it than deleting it.

You may find clues to the offending app by looking at the .xsession-errors file. 

```
more .xsession-errors
```

You can exit the more command by using ctrl + C

---

### Post by jiewmeng on 2011-10-19
Ok I took a sniplet from the end of .xsession-errors. I don't know if its the latest? But its last modified 1 min ago. 

[http://pastie.org/2724277](http://pastie.org/2724277)

Shouldn't logs be automatically deleted? So that they don't take up so much space so quickly?

---

### Post by mcduck on 2011-10-19
Could you run "*df -h*" in a terminal and post the output here?

The Disk Usage Analyzer is not really a great tool for checking used/available disc space, that's not what it's made for and by default it will include all available filesystems instead of scanning the usage of a certain one, which makes it rather hard to determine used/available space on your filesystems. (the tool is intended for finding out *where* space is being used, which is why it reports the usage as percentages relative to the parent directory, and also includes all available filesystems by default. You *can* use it for checking used/avaiable space, but only if you configure it to only scan a certain filesystem at a time and not to follow any symbolic links, and also exclude certain directories like ~/.gvfs)

edit: you might also want to run "*sudo du --max-depth=1 /*"and perhaps "*du --max-depth=1 /home/jiewmeng &#8804; sort -nr*" to get more reliable information about where the space is used. The disc Usage Analyzer tends to count stuff like drives, encrypted directories and network locations mounted through GVFS into the used space which can cause some confusion...

---

### Post by jiewmeng on 2011-10-19
@mcduck, I deleted the file in question already, but from the run just now, the output went off screen, most are small I think I cant find xsession-errors.old

---

### Post by mcduck on 2011-10-19
> **jiewmeng said:**
> Ok I took a sniplet from the end of .xsession-errors. I don't know if its the latest? But its last modified 1 min ago. 

[http://pastie.org/2724277](http://pastie.org/2724277)

Shouldn't logs be automatically deleted? So that they don't take up so much space so quickly?
Log files are automatically deleted at boot, so if you have some really nasty problem that's logging insane amount of errors quickly, it can result in some log file growing very large.

Anyway, there doesn't seem to be anything important in that specific log. Is the file unreasonably large? If not, you are looking at the wrong file. Since you are running out of disc space, you'd be looking for a log file that's at least gigabytes in size, so going off screen doesn't mean much. Text doesn't take much drive space, so you'll need _a lot_ of text before a log file becomes large enough to have any meaningful effect in your disc usage...

---

