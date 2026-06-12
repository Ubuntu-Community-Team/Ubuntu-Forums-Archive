---
title: "Path of iso mounted using archive mounter?"
date: 2010-07-15
forum: General Help
---

### Post by Bazirker on 2010-07-15
OK I don't know what mental block is keeping me from figuring this out on my own seeing as it seems pretty simple, but here it goes...

I need to enter a file path into a program (happens to be AcidRip DVD Extractor) of a disc that I wish to access.  I have a particular ISO image that I'm mounting (happens to be a DVD I want to watch on my TV via a USB drive so I need to rip the DVD to a video file such as xvid), but when I mount it using the Archive Mounter that comes standard in Ubuntu 10.04, I can't figure out where the ^@%! it's mounted or how to set where I want to mount it.  So...help?  Thanks guys!

---

### Post by dcstar on 2010-07-16
> **Bazirker said:**
> OK I don't know what mental block is keeping me from figuring this out on my own seeing as it seems pretty simple, but here it goes...

I need to enter a file path into a program (happens to be AcidRip DVD Extractor) of a disc that I wish to access.  I have a particular ISO image that I'm mounting (happens to be a DVD I want to watch on my TV via a USB drive so I need to rip the DVD to a video file such as xvid), but when I mount it using the Archive Mounter that comes standard in Ubuntu 10.04, I can't figure out where the ^@%! it's mounted or how to set where I want to mount it.  So...help?  Thanks guys!

It is not an "Archive **Mounter**" it is an Archive **Manager**", it *mounts* nothing - disks must already be mounted to be accessed by it.

---

### Post by Bazirker on 2010-07-16
No, there is an Archive Mounter which is distinct in it's function from Archive Manager.  Here is an example of it being discussed: [http://jordanhall.co.uk/ubuntu-linux/how-to-mount-a-disc-image-in-ubuntu-linux-4212340/]("http://jordanhall.co.uk/ubuntu-linux/how-to-mount-a-disc-image-in-ubuntu-linux-4212340/")

---

### Post by Bazirker on 2010-07-18
Found the answer myself.  The image is mounted in /home/your_username_here/.gvfs

---

### Post by bemental on 2010-09-09
> **Bazirker said:**
> Found the answer myself.  The image is mounted in /home/your_username_here/.gvfs

Good job Baz.  That was quite a rude response for someone with 9,677 posts...

---

### Post by bemental on 2010-09-09
Although I still can't flip the executable bit of a file stored on the ISO.

Oh well, copy files over it is.

Thanks again Baz.

---

### Post by Orly01 on 2010-09-19
I write this just to say that I got crazy trying to figure that out. Of course once I didn't need the answer (I used Gmount-iso) I found this.

---

### Post by techiebiker on 2010-11-21
> **Bazirker said:**
> Found the answer myself.  The image is mounted in /home/your_username_here/.gvfs

I'm not finding the mount in ~/.gvfs

Do you know if my user account needs to belong to any specific group for Archive Mounter to work?

I run it and get no response in the UI. Nothing shows up in the logs.

I did install Gmount-iso (per your solution) but recall Archive Mounter working in the past and it was simpler. Just caused an icon to appear on desktop. Gmount-iso presents options and I liked the simpler function of AM better.

---

### Post by Bazirker on 2010-11-21
> **techiebiker said:**
> I'm not finding the mount in ~/.gvfs

Do you know if my user account needs to belong to any specific group for Archive Mounter to work?

I run it and get no response in the UI. Nothing shows up in the logs.

I did install Gmount-iso (per your solution) but recall Archive Mounter working in the past and it was simpler. Just caused an icon to appear on desktop. Gmount-iso presents options and I liked the simpler function of AM better.

It is possible that, since you're mounting a drive, you need to belong to a group that gives you the permission to do so, but I just messed around on my system and don't see what group that might be.  I kinda doubt that's the issue, as it would take some seriously locked down permissions to not even allow disc mounting (you wouldn't even be able to do things like use flash drives.)  

In the grand scheme of linux issues, I personally would throw that issue into the "kind of irritating but not worth the time it might take to fix it" basket and just keep using Gmount-iso  :)

---

### Post by mister_playboy on 2011-02-06
> **Bazirker said:**
> The image is mounted in /home/your_username_here/.gvfs

Thanks so much!  I couldn't figure this out of the life of me... sometimes Ubuntu actually makes things harder in its quest for simplicity. :p

---

