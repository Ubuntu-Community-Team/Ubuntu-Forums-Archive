---
title: "Something is eating up all my disk space!"
date: 2010-08-27
forum: General Help
---

### Post by ZequeZ on 2010-08-27
When I check the disk usage through Nautilus RightClick->Properties it says I have 114gb used and 14gb free...

BUT! If I select all the files and click on properties it says that they are using only 36gb!!! I tried with the disk usage analizer, but it says that there are only 36gb being used!

Yes, I have "show hidden files" checked...

Any clue of what could be, or how to discover it?

Thanks, and sorry for my english :P

---

### Post by wojox on 2010-08-27
What does this post?

```
free -m
```

---

### Post by doktarZues on 2010-08-27
I found ~100GB stashed in my root trash folder that I couldn't get to otherwise.  I assume this is from me deleting files while in a sudo nautilus window.  Searching around it seems to be an unresolved bug at this point.  Not sure if that is your issue but definitely worth looking here:

/root/.local/share/Trash

Make sure you shift+delete it otherwise it may show right back up.

---

### Post by ZequeZ on 2010-08-27
> **wojox said:**
> What does this post?

```
free -m
```

```
             total       used       free     shared    buffers     cached
Mem:          2012       1698        314          0        390        616
-/+ buffers/cache:        690       1322
Swap:         2047          0       2047

```

I'm on a live CD because I was about to partition after I noticed this. Do I need to enter to the Ubuntu installed in disk?

---

### Post by wojox on 2010-08-27
I was thinking memory not hdd space. :oops:

Yes mount the drive and look at

```
du -h
```

That will show you everything in your Home Folder

---

### Post by ZequeZ on 2010-08-27
> **wojox said:**
> I was thinking memory not hdd space. :oops:

Yes mount the drive and look at

```
du -h
```

I was starting to wonder why would you need that command info xD.

Wait, I have to restart the computer then. It shows the live CD home xD.

---

### Post by ZequeZ on 2010-08-27
> **wojox said:**
> I was thinking memory not hdd space. :oops:

Yes mount the drive and look at

```
du -h
```That will show you everything in your Home Folder

I used "du -h | grep G" to catch the largest files... Well, it was the trash -.- (60gb)

Why do the disk usage analizer don't show hidden files and directories? -.-

---

