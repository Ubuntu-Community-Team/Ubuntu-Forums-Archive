---
title: "External hard drive help"
date: 2011-08-27
forum: General Help
---

### Post by thatguy93 on 2011-08-27
Hey guys.
Okay my old laptop that had ubuntu on it died a few weeks ago. I took the hard drive out, and bought a "masscool" 2.5" HDD enclosure for it. So it will become my external HDD.
Now I have an issue.
Since it has the full ubuntu filesystem on it, it is write protected on windows. On fedora 15, I am able to access the files, but many files are locked because you need to be root.
Now my question is, how can I remove the write protection/linux file system without losing my documents and pictures?
I am totally stumped.

thanks!

---

### Post by rickyjones on 2011-08-27
> **thatguy93 said:**
> Hey guys.
Okay my old laptop that had ubuntu on it died a few weeks ago. I took the hard drive out, and bought a "masscool" 2.5" HDD enclosure for it. So it will become my external HDD.
Now I have an issue.
Since it has the full ubuntu filesystem on it, it is write protected on windows. On fedora 15, I am able to access the files, but many files are locked because you need to be root.
Now my question is, how can I remove the write protection/linux file system without losing my documents and pictures?
I am totally stumped.

thanks!

From Fedora you should be able to chmod/chown all the files as the root user, just change everything to 777 I think. Do that from the terminal for the entire drive. Then you should be able to access the files without an issue, in Fedora. 

Hope it helps!

-Richard

---

### Post by thatguy93 on 2011-08-27
> **rickyjones said:**
> From Fedora you should be able to chmod/chown all the files as the root user, just change everything to 777 I think. Do that from the terminal for the entire drive. Then you should be able to access the files without an issue, in Fedora. 

Hope it helps!

-Richard

Can you give me an idea of exactly what I need to put in terminal.
I dont want to screw anything up lol

---

### Post by thatguy93 on 2011-08-27
> **allwimb said:**
> You have to convert the filesystem to FAT to be able to read/write into under Windows but you cannot change the filesystem without formatting so you need to copy all the data and they format it using FAT and recopy the copied data into it.

It actually wont allow me to copy any files because it is write protected.

---

### Post by rickyjones on 2011-08-29
> **thatguy93 said:**
> Can you give me an idea of exactly what I need to put in terminal.
I dont want to screw anything up lol

This command should set the file permissions to allow everyone to read/write:

```
chmod -R 777 /media/DRIVE/
```

Hope this helps!

-Richard

---

