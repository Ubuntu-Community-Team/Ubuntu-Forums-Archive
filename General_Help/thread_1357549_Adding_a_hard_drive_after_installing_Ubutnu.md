---
title: "Adding a hard drive after installing Ubutnu?"
date: 2009-12-17
forum: General Help
---

### Post by Cityscape on 2009-12-17
I want to install Ubuntu 9.10 (dual-boot with XP). Both OS's and maybe documents will be stored on the main physical (but 2-3 partitions) hard drive. I have a second documents drive I also want too.

I'm a still a newbie when it comes to linux and I've made mistakes installing Ubuntu before. Can I take my second documents drive out of the PC while installing Ubuntu and then put it back in when Ubuntu is installed.? Will it recognize the drive and function the same way as if I'd had it in the whole time? Thanks :)

---

### Post by Grenage on 2009-12-17
That will be fine, you'll just need to add the drive to /etc/fstab if you want it to auto-mount at boot.

---

### Post by spydeyrch on 2009-12-17
When you say "documents" drive, do you mean a /home partition or do you mean that you just have a second hdd that you use to store items on it (such as documents, pics, videos, etc.) Basically the second drive is an extra storage drive, right?
 
If that is the case and it is not your /home partition (if you have set up a seperate one), then yes, you can take it out, do what  you need to do, and then later put it back in. 
 
-Spydey:guitar:

---

### Post by Cityscape on 2009-12-17
> **spydeyrch said:**
> When you say "documents" drive, do you mean a /home partition or do you mean that you just have a second hdd that you use to store items on it (such as documents, pics, videos, etc.) Basically the second drive is an extra storage drive, right?
 
If that is the case and it is not your /home partition (if you have set up a seperate one), then yes, you can take it out, do what you need to do, and then later put it back in. 

Yes the second drive would just have documents, music, videos and the like on it. Actually it is my old XP OS drive with the Windows System files/folders deleted.

---

### Post by Darael on 2009-12-17
> **Cityscape said:**
> Yes the second drive would just have documents, music, videos and the like on it. Actually it is my old XP OS drive with the Windows System files/folders deleted.

You'll be fine then - if you want it under a folder other than /media/[disk-label] then you'll need to edit /etc/fstab, but we can guide you through that. And if /media/whatever is fine (it'll appear in your places menu anyway) then you're pretty much good to go, just plug it back in and Ubuntu will recognise it and make it available when next you boot into it. It's good like that :)

---

### Post by YoTeach on 2009-12-26
I have an additional, though related question:

I have setup Ubuntu 9.10 with Netatalk and Avahi so that I can use it as a File and Print server and backup my Macbook using Time Machine through my home network.  I did all the work of getting it all up and running with a 10 gig hard drive as a proof of concept, and now I need to add a larger drive.  Should I put a new drive in, and completely do the process over again, or should I "slave" the new larger drive and add it as a shared location in Netatalk and use that as my Time Machine backup?

---

