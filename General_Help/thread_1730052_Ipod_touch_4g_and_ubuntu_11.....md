---
title: "Ipod touch 4g and ubuntu 11...."
date: 2011-04-15
forum: General Help
---

### Post by LatinaLover93 on 2011-04-15
I know there is some bult in support, with banshee and all. But how would i sync other things like my photos and whatnot? im dual booting ubuntu and windows 7 at the moment and the only thing holding be back from going full ubuntu is my ipod, itunes, and jailbreaks. Is there anything that will do everything itunes does on ubuntu, for free?

---

### Post by bashologist on 2011-04-15
Is it jailbroken?

Here's how you could sync files from your device.

```
mkdir /mnt/ipod photos
ifuse --root /mnt/ipod
cp /mnt/ipod/var/mobile/Media/DCIM/100APPLE/* photos/
```

If you're interested in shell scripts for syncing photos or books from you computer to your device then I might be able to help. You would need to have the device mounted with ifuse tho.

---

### Post by LatinaLover93 on 2011-04-15
Now whats ifuse?? Sorry but i havent used ubuntu since ubuntu 8 so....things changed alot

---

### Post by bashologist on 2011-04-15
I dunno what's ifuse, but I hear that it makes the penguin play with the fruit. It just basically mounts your device so you can see the files and transfer them etc. What version of ubuntu are you using now? Is ifuse available on your system? Are you jailbroken?

---

### Post by LatinaLover93 on 2011-04-15
im using ubuntu 11 with ipod touch 4g ios 4.3.1 unteatherd jailbreak

---

### Post by bashologist on 2011-04-15
That's good, that's what I'm using too. Did you just want to transfer the photos to your computer or the other way around too? Are you comfortable with shell scripts? Was there anything else?

Also on a side note I wouldn't remove your windows 7 or anything and switch to a full Ubuntu only.

Sometimes you can only do things on Windows. For example I've been using Ubuntu for years and it can play most media files but it still can't yet play vc-1 interlaced codec which bluray rarely uses so I've gotta go to my Windows 7 partition if I'm wanting to play that.

---

### Post by LatinaLover93 on 2011-04-15
i wanna put them onto the ipod, but the other way around would be nice  too, just in case. n no im not familiar with them, im only familiar with  batch scripting but thats windows cmd. No theres nothing else, Banshee does my music and ubuntu 11 allows me some functionality with the ipod file system by default, which is awesome

---

### Post by bashologist on 2011-04-15
Try the program tripod, it's described as "iPod photo uploader". If there's no other way I could release my personal shell scripts which might be kinda risky.

---

### Post by LatinaLover93 on 2011-04-15
Seached in software center but not in there, googleing it now but not finding it for ubuntu 11. Do i just go with the 10.10 version or is there a repository im supposed to add

---

### Post by bashologist on 2011-04-15
Just installed it to find out (I don't know another way). It's in the universe repository for 10.04, don't know about 11.

sudo apt-get install tripod

Get:8 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/universe tripod 0.7.0-2ubuntu1 [69.1kB]                                                                                                               

Also just to let you know I havn't tried tripod before so let everyone know if it works and stuff?

---

### Post by LatinaLover93 on 2011-04-15
i'll test it but ubuntu 11 doesnt have it (by default, at least) i have the tar.gz for it though found on their site [http://code.google.com/p/tripod/](http://code.google.com/p/tripod/) but how would i install it?

---

### Post by LatinaLover93 on 2011-04-15
though it was uploaded novem 2007, so i doubt it will have ipod touch support.

---

### Post by bashologist on 2011-04-15
Well I've got a pretty simple script for uploading photos just needs to work out a few bugs then I'll post it. Are you able to use ifuse?

---

### Post by LatinaLover93 on 2011-04-15
i have it but i dont know how to use it

---

### Post by bashologist on 2011-04-15
Alright so I posted my script. You might wanna let someone besides me test it first before you try it tho.

[http://ubuntuforums.org/showthread.php?p=10681500](http://ubuntuforums.org/showthread.php?p=10681500)

---

### Post by LatinaLover93 on 2011-04-15
will do

---

