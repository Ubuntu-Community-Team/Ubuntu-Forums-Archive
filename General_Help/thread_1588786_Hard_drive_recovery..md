---
title: "Hard drive recovery."
date: 2010-10-05
forum: General Help
---

### Post by serdar132 on 2010-10-05
Hello everyone.

A few months ago I took my Ibook G4s hard drive and started to use it as a external harddrive. Recently I have formated my pc, so I put a lot of imporant documents to that external hard drive.

I was copying these files to the windows 7, then windows (not surprisingly) freezed copyin, and I had nothing else rather then unplug the hardrive. And now neither Ubuntu nor Windows recognize the format of the disk so I can not see or access any document inside the external.

SI basicly I need help to access to my external, or at least recover data

Thanks
Serdar

---

### Post by Quackers on 2010-10-05
I haven't used it, but I have heard quite good things about Testdisk.

---

### Post by Grenage on 2010-10-05
Indeed; Testdisk/Photorec should be able to help you.

---

### Post by serdar132 on 2010-10-06
Thanks!
I ran Test Disk, and I recovered my files. I have another problem now! THe files that I have recover are shown as root, so I cant write the files only read them.

How can I change that permission to read and write?

---

### Post by Grenage on 2010-10-06
If the files are in a directory, and you want to give everyone rights to everything:

```
chmod +R 777 /home/directory
```

But that gives everyone the rights to do anything to them.

---

