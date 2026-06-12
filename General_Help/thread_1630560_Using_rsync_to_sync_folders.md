---
title: "Using rsync to sync folders"
date: 2010-11-25
forum: General Help
---

### Post by rmcellig on 2010-11-25
I am thinking of using rsync to sync my Music folder to another folder called Music on an external USB drive. I will be using the Scheduled Tasks front end to schedule the syncs. What should the syntax look like when I put it in Scheduled tasks. I want this to be as simple as possible.

Thanks!!!

---

### Post by aeiah on 2010-11-25
```
rsync -a --delete /path/to/source/ /path/to/destination/
```

the -a flag is archive. it'll preserve timestamps etc
--delete will remove anything in your external music directory that you've previously deleted in your local music directory

you may want to use -n --progress to test it. progress will print loads of stuff out. -n is the dry-run option. it won't actually do anything, it'll just tell you what it would have done if you'd have left the -n off, so its useful to make sure you aren't doing anything silly (like mixing source and destination up)

---

### Post by QLee on 2010-11-25
Yes, and in addition to the good advice aeiah gave, you may want to do this with a script which first checks that the removable device is attached before continuing. If your, path to destination, is a folder that exists even when the device is unmounted, you might get unwanted results, like filling up your root filesystem, which could then be masked when the drive was connected.

---

### Post by rmcellig on 2010-11-26
Hi QLee!

I'm a bit confused as to how to implement what you describe. I want to keep this as simple as possible. Thanks!!! I am still a newbie wading through the waters of Linux. :)

---

### Post by QLee on 2010-11-27
[QUOTE=rmcellig]
I'm a bit confused as to how to implement what you describe. I want to keep this as simple as possible. Thanks!!! I am still a newbie wading through the waters of Linux. :)[/QUOTE]

Sorry about the time frame for answering but I dropped off the forum for the day shortly after posting to you in the other thread.

I see from that thread that you didn't fully understand my advice here at first. Please feel free to ask for clarification on anything I suggest if you don't understand it, usually I can come up with a more detailed or clearer explanation. What I did was make the mistake of "assume", eh. Because we're in the General forum and your question seemed clear, I assumed you just needed the caution. Your question is answered in the other thread.

---

### Post by rmcellig on 2010-11-27
I will post my rsync code when I am ready to do it. i have my radio show tomorrow so I have to get ready for that. :)

---

### Post by rmcellig on 2010-11-27
OK, here is the test code I am using:

rsync -acrv /home/randy/Documents /media/USB2/testbackup

What should I put in the code so that when I delete something in the Documents folder, it wil also be deleted in the testbackup folder when I perform a sync.

How can I have it so the code will check if USB2 is available, if it is, do the sync, if not, do nothing.

---

### Post by QLee on 2010-11-28
[QUOTE=rmcellig]OK, here is the test code I am using:

rsync -acrv /home/randy/Documents /media/USB2/testbackup[/QUOTE]

I meant my suggestion to be that you make a new post (new thread, new question) for suggestions (perhaps mentioning please check my script), many users (perhaps even the ones most able to code) will not look through this older post.

[QUOTE=rmcellig]What should I put in the code so that when I delete something in the Documents folder, it wil also be deleted in the testbackup folder when I perform a sync.[/QUOTE]

Did you notice the --delete in the code that aeiah gave you here? There are other options for "delete", if you enter, man rsync, in a terminal window you can read the whole manual and all of the option possibilities. Since you are doing this locally you won't have to concern yourself with rsyncing to a remote location.

[QUOTE=rmcellig]How can I have it so the code will check if USB2 is available, if it is, do the sync, if not, do nothing.[/QUOTE]
That's what drs305 gave you in the other thread. In fact drs305 gave you a skeleton script for exactly what you want to do.

---

### Post by rmcellig on 2010-11-28
Thanks QLee!! Sorry for all this confusion. Now I have to find the thread that drs305 posted. I will take a look at that again. Thanks!!

---

