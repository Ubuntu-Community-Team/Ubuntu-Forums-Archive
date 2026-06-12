---
title: "Music from windows??"
date: 2010-07-30
forum: General Help
---

### Post by JustinZTerrible on 2010-07-30
I have 2 hard disks in my pc one is a 1tb for windows 7 the other is 160gb for Back Track 4. I have amarok installed, but no codecs yet..

Will sudo apt-get install ubuntu-restricted-extras get me the right codecs? also I was wondering how to mount my windows disk to get the mp3s.. please help

---

### Post by Revolutionary101 on 2010-07-30
```
sudo apt-get install ubuntu-restricted-extras
```
Will get you the codecs you need. Also to mount your Windows HDD go to Places and you should see a drive listed as C:\ or 1 TB file system. Then click on that to mount the drive.

---

### Post by JustinZTerrible on 2010-07-30
where do I go to find it marked as C:/ ?

---

### Post by jerenept on 2010-07-30
> **JustinZTerrible said:**
> where do I go to find it marked as C:/ ?

Windows uses a drive letter scheme for organizing partitions. Ubuntu uses mount points (/media/Disk and so forth).

It will not be listed as C:\, but will be listed as "1 TB Filesystem"

---

### Post by JustinZTerrible on 2010-07-30
but under where? I understand that windows uses letters to mark them and that it will be "1tb file system"..lol.. /me is going to feel really dumb if it's something simple

---

### Post by jerenept on 2010-07-30
Places menu.....

at the top of the screen?

---

### Post by anon.jdh on 2010-07-30
Another thing that may help is looking for the size of your Windows partition. If you have it installed on a 60GB volume, for example look for the one that's 60GB.

Once you click on it and mount it, you'll recognize some Windows folders that would only be under C:\ but Ubuntu's not going to call it "C" it will call it (for ex.) "60GB File system" if I remember correctly.

---

### Post by JustinZTerrible on 2010-07-30
see I was thinking i'd have to do command line work.. you know?

---

### Post by Revolutionary101 on 2010-07-30
> **JustinZTerrible said:**
> see I was thinking i'd have to do command line work.. you know?

No, command work is rarely needed in Ubuntu unless you have a hardware problem or something serious like that.

---

### Post by JustinZTerrible on 2010-07-31
but command line is way more fun then gui..

---

### Post by JustinZTerrible on 2010-07-31
I would like to learn alot more command line stuff if anyone would teach.. idk where to start really

---

### Post by JC Cheloven on 2010-07-31
> **JustinZTerrible said:**
> I would like to learn alot more command line stuff if anyone would teach.. idk where to start really
There is a lot of stuff in the net. Do a little search! For example in Ubuntu documentation you have this:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by JC Cheloven on 2010-07-31
Sorry, related to your OP: I think you'll need to add the medibuntu repository prior installing ubuntu-restricted-extras. [Here]("https://help.ubuntu.com/community/Medibuntu") is how.
Cheers

---

