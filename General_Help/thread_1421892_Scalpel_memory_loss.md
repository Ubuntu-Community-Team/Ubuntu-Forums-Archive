---
title: "Scalpel memory loss"
date: 2010-03-04
forum: General Help
---

### Post by ewan86 on 2010-03-04
I decided to use scalpel to recover some lost video files. I set it to search for mpeg video files, it was doing its job then because there were too many files being recovered it crashed as I had no memory left on my hard drive. Ubuntu then wouldn't log onto GDM as it didn't have enough memory, so I freed up hard drive space by deleting files from the terminal.

When I eventually managed to log on I deleted the scalpel output folder but this hasn't returned the same amount of free memory I used to have and I am still dangerously short, down to less 500MB!!

I have searched using disk usage analyzer, and gnome-do, but I cant find the files causing this problem.

I know this was my fault for taking on a task I didn't really have the expertise for...but has anyone any idea where the hard disk space may have gone??

---

### Post by lavinog on 2010-03-05
How are your partitions set up? (do you have a separate home partition?)

try this command:
```

du --maxdepth=1|sort -n

```
Look in the largest folders.

Just to make sure: We are talking about disk space and not memory correct?

---

### Post by ewan86 on 2010-03-05
> **lavinog said:**
> How are your partitions set up? (do you have a separate home partition?)

try this command:
```

du --maxdepth=1|sort -n

```
Look in the largest folders.

Just to make sure: We are talking about disk space and not memory correct?

Hi,

when I Run that command it is not recognised (see attachement). My laptop has two separate hard drives installed, 20gb each, one drive is totally dedicated to ubuntu and has all the things that would be there for a standard set up.

I mean hard disk space as opposed to RAM. Sorry if I'm not very clear my lingo isn't quite up to scratch!!

Thanks for your help!!

---

### Post by lavinog on 2010-03-05
sorry, typo on my part:
```

du --max-depth=1|sort -n

```

---

### Post by ewan86 on 2010-03-06
> **lavinog said:**
> sorry, typo on my part:
```

du --max-depth=1|sort -n

```

Hey thanks works now. Is this the contents of the home folder? What does the . before the / mean? What is the biggest folder at the bottom that is marked just as a .? Where can I find that?

Thanks again :)

---

### Post by lavinog on 2010-03-06
./ means current folder (the folder where you ran the command, which would be your home folder in this case)

../ means parent folder

You can free up some space be deleting the thumbnails folder...It will rebuild itself when you view a folder in nautilus with thumbnails.
I am not sure why your .cache folder is so big, but you can cd ~/.cache and use the du command again to see why it is.

---

