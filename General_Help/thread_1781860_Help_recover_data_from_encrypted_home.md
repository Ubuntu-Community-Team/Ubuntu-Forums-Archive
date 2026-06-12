---
title: "Help recover data from encrypted home"
date: 2011-06-14
forum: General Help
---

### Post by bosto on 2011-06-14
Hello,

so, after long time of succesfull use of kubuntu, i encountered a 1st major disaster yesterday while using kphotoalbum. It has somehow frozen my machine in so mighty way, that it apparently corrupted a directory with majority of my pictures :(, which now appears to be empty :(.

My home lies on a separate partition, its encrypted aand using btrfs and I am using kubuntu 10.10. So, could anyone give me some clues how to unencrypt my home partition, that i could obtain an image of partition or whatever else usable for photorec to check for pictures?

Many thanks in advance.

---

### Post by wildmanne39 on 2011-06-14
> **bosto said:**
> Hello,

so, after long time of succesfull use of kubuntu, i encountered a 1st major disaster yesterday while using kphotoalbum. It has somehow frozen my machine in so mighty way, that it apparently corrupted a directory with majority of my pictures :(, which now appears to be empty :(.

My home lies on a separate partition, its encrypted aand using btrfs and I am using kubuntu 10.10. So, could anyone give me some clues how to unencrypt my home partition, that i could obtain an image of partition or whatever else usable for photorec to check for pictures?

Many thanks in advance.Hi, I did some searching and found this, it should take care of your problem.
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory)

---

### Post by bosto on 2011-06-14
Thanks bigtime, ill try it when i get back home :)

---

### Post by bosto on 2011-06-14
Hmm, the more i read bout the solutions aand eCryptFs, the more i have a feeling that i definetly lost my pictures :(

Wildmanne39, your links are great, but they all involve rescuing encrypted data in otherwise valid filesystem. The problem i have is, that my data is no more visibile thru filesystem. I dont have a problem accessing data in my home directory since my installation still perfectly works and mounts /home with no problem.

What _IS_ a problem is that i want my deleted files back. Id actually need a method to 'offline' unencrypt, that is, somehow without mounting, all data from partition, not just the one in filesystem.:S

---

### Post by HermanAB on 2011-06-14
Howdy,

That is the big drawback of the current crop of encrypted file systems.  They are typically not robust and you can easily lose all your data. So backups are very important when using encrypted systems.

---

### Post by wildmanne39 on 2011-06-14
> **bosto said:**
> Hmm, the more i read bout the solutions aand eCryptFs, the more i have a feeling that i definetly lost my pictures :(

Wildmanne39, your links are great, but they all involve rescuing encrypted data in otherwise valid filesystem. The problem i have is, that my data is no more visibile thru filesystem. I dont have a problem accessing data in my home directory since my installation still perfectly works and mounts /home with no problem.

What _IS_ a problem is that i want my deleted files back. Id actually need a method to 'offline' unencrypt, that is, somehow without mounting, all data from partition, not just the one in filesystem.:SHi, have a look here.
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)
[http://www.ubuntu-unleashed.com/2008/04/howtorecover-and-undelete-text-file-in.html](http://www.ubuntu-unleashed.com/2008/04/howtorecover-and-undelete-text-file-in.html)
[http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/](http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/)

---

