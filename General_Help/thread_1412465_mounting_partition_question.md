---
title: "mounting partition question"
date: 2010-02-21
forum: General Help
---

### Post by Dithers on 2010-02-21
Recently I mounted a larger partition into my home directory since I was running out of space, Everything went smoothly, but it caused me to wonder about something I cant figure out. While playing with the mount unmount commands when I was copying everything over... before editing my fstab.

Is there a way to access the files that existed in a directory before you mount a partition to that directory?

after mount the original files are gone.
unmount and they are back, Where do they go?

just curious!

---

### Post by nixclusive on 2010-02-21
When you mount a partition in a directory, the pre-mount contents are still there but inaccessible as long as the directory is being used as a mount point. :)

---

### Post by jenaniston on 2010-02-21
> **Dithers said:**
> . . . I mounted a larger partition into my home directory since I was running out of space . . .

Is there a way to access the files that existed in a directory before you mount a partition to that directory?

after mount the original files are gone.
unmount and they are back, Where do they go?

just curious!

interesting . . . 
But if I understand you right . . . I don't see why a mkdir and then mount to /mnt/*emptydirectoryname*
would have any sort of space limitation that your mount to /home/ would not also have . . .

if anything, I wouild have thought that /home/ as a mount point could be probably *limited* **more **- as  it already has files of course. 
Run df -h or something ? . . . wonder *where *they really are held/stored temporarily.  

There probably could be some space limitation to how much can really be in any directory . . . 
so is there some "overflow" area . . . I dunno.

Interesting and a bit quirky question.

---

### Post by Dithers on 2010-02-22
> **jenaniston said:**
> I don't see why a mkdir and then mount to /mnt/*emptydirectoryname*
would have any sort of space limitation that your mount to /home/ would not also have . . .




Actually I copied everything from /home to a new partition on a new HD, deleted it all, then changed the mount point of the new partition to /home in fstab and restarted. <i>just make sure you get all the hidden files too</i> 

I learned all the files in the dir originally disappear when the mount is made when I mounted it as a test before editing fstab.

---

