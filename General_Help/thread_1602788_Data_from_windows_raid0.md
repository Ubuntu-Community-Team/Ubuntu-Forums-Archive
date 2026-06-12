---
title: "Data from windows raid0"
date: 2010-10-21
forum: General Help
---

### Post by dansskittles on 2010-10-21
I had windows and ubuntu for some time, the other day I had an issue with (msconfig). The easiest way to fix it is to fresh install windows. So I wanted to boot into ubuntu, take my windows files and toss them onto a external drive. So this is were I need help. I have 3 hard drives, 2 internal and 1 external. The 2 internal drives are 2 500 gig WD's in raid0. I can not find out how to retrieve my data from these drives at all. I can get the partition manager to tell me I have them, but I can not find them anywhere let alone get data off. And I have my work for my 10 page research paper on there and I should be working on it but have not been able to retrieve the work and put it on my laptop. If anyone can help that would be great thanks guys.

---

### Post by blueridgedog on 2010-10-22
Raid 0 is for performance, not fault tolerance and if created with a software system (such as windows software raid and not a hardware raid card or chip) can not be read outside of that software environment.  Your best bet at recover is to install windows to another partition and see if it recognizes the disks as a volume.  There are several tools that will try and recover data from such a software array, but they are for purchase:

[http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=recover+windows+software+raid+0](http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=recover+windows+software+raid+0)

---

### Post by ronparent on 2010-10-22
********. Start a live cd session and in a terminal enter 'sudo dmraid -ay'. With release 10.10 your all your windows partitions should be immediately mountable and you should be able to retrieve all of your files.

---

### Post by blueridgedog on 2010-10-23
> **ronparent said:**
> ********. Start a live cd session and in a terminal enter 'sudo dmraid -ay'. With release 10.10 your all your windows partitions should be immediately mountable and you should be able to retrieve all of your files.

Amazing...dmraid can now read the windows software raid?

---

### Post by ronparent on 2010-10-23
The express purpose of dmraid is to read the windows software raid or as the linux community likes to call it 'fakeraid'. It is the only way to share a raid partition between the two OS's.

---

### Post by Quackers on 2010-10-23
That's very interesting. I haven't used raid yet for that reason. I may now be persuaded :-)

---

