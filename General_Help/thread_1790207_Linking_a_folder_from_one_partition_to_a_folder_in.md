---
title: "Linking a folder from one partition to a folder in another"
date: 2011-06-24
forum: General Help
---

### Post by Khodeir on 2011-06-24
Hello all, 

I know the title didn't make much sense. That's actually part of the problem. I can't describe what it is i want to do efficiently enough for Google to come up with relevant results. So here goes:

I have a pretty big movie collection that sits in /home/user/Videos. Now this folder is being monitored by a couple of media players like Moovida and I'm also using it as the main source of media for the Mediatomb server that I access from my ps3. 

Of course, i didn't assign enough disk space for my /home folder when i did the partitions a couple of years ago, so now i have two (bad) options:

1. I resize my /home partition and take a 100GB or so off my useless /usr partition.
2. I move a chunk of my collection to /usr and add /usr/Videos to the relevant media software.

I don't want to do either of those because 1 is way too time consuming and risky (I cant rely on my power to remain on for the 12 hours that this resize operation would undoubtedly take) and option 2 just seems messy and i dont like it. 

What I want to do is move a bit of the collection to /usr/Videos and have that location mounted (for lack of a more appropriate term) onto the /home/user/Videos directory so that all the movies i have on /usr/Videos appear (to the media software) to be stored on /home/user/Videos. 

This is sort of the same thing as the Windows 7 libraries where all added folders seem to reside in the library. Anyone got any ideas? 

Thanks for helping, 
Khodeir

---

### Post by FormatSeize on 2011-06-24
> **Khodeir said:**
> 
[...] 12 hours [...] 
 

Why does it take 12 hours?
 
As for the linking part, have you tried the following:
```
ln -s /home/user/Videos /usr/Videos
```

---

### Post by nothingspecial on 2011-06-24
If you are using Ubuntu (or not, but nautilus), click the file to highlight it, hold down Ctrl-Alt, then drag it to where you want it.

---

### Post by Khodeir on 2011-06-24
It takes 12 hours (at least) because the /usr partition is on the left of the /home partition, so the process consists of 1) resizing the /usr partition 2) moving the 800GB /home partition to the left and 3) Resizing the /home partition.

I have tried ln -s and Ctrl +Alt + Drag (they are equivalent methods of creating symlinks) and it doesn't do what it's supposed to. I don't think the software i'm using is capable of following symlinks. Mediatomb does, but not all of them do.

I think what i'm trying to do can be likened to how the /home folder, despite being a seperate partition, is seen as part of the / directory (which is a seperate partition altogether.) This analogy works because if you were to scan the / directory with mediatomb or Moovida, folders from within the /home partition would be included.

---

### Post by nothingspecial on 2011-06-24
> **Khodeir said:**
> . I don't think the software i'm using is capable of following symlinks. Mediatomb does, but not all of them do.


Are you sure your software can't handle symlinks, and if not there may be a way to get round it.

I would not be happy with software that didn't handle them.

---

