---
title: "An issue that never seems to end"
date: 2010-05-22
forum: General Help
---

### Post by Jacob Krustchinsky on 2010-05-22
Hello,

I am fairly new to linux and I have a few questions regarding something I am trying to do. I accidentally wiped my 120GB external hardrive clean ( it was at about 95% capacity ) and I was able to recover 111.80GB back using ddrescue and all of those files now sit in a Recovery.img file.

1 ) I know I have to mount this file...yet every time I try to mount it back on my external HD permissions jump down my neck, and to add to it when I try to give my user full permissions for that drive it never works and resets to how it was.

2 )I have tried copying to .img to my drive so I could jsut worry about it later and free up some local HD space yet I don't have those permissions as well...

Help would be greatly appreciated.

---

### Post by -humanaut- on 2010-05-22
I don't quit understand your question you wiped out a drive then recovered it with an .img file? and What are you trying to do with the .img file?

---

### Post by dcstar on 2010-05-22
> **Jacob Krustchinsky said:**
> Hello,

I am fairly new to linux and I have a few questions regarding something I am trying to do. I accidentally wiped my 120GB external hardrive clean ( it was at about 95% capacity ) and I was able to recover 111.80GB back using ddrescue and all of those files now sit in a Recovery.img file.

1 ) I know I have to mount this file...yet every time I try to mount it back on my external HD permissions jump down my neck, and to add to it when I try to give my user full permissions for that drive it never works and resets to how it was.

2 )I have tried copying to .img to my drive so I could jsut worry about it later and free up some local HD space yet I don't have those permissions as well...

Help would be greatly appreciated.

Unless you give specific details of what the problems are you will get little useful help - we are not mind readers.

---

### Post by Drybones5 on 2010-05-22
I think he's trying to get permissions on the file to mount it.  Which would need root?

I think the program put the recovered files into a .img file which I have no idea what that is (wikipedia time)

---

### Post by Jacob Krustchinsky on 2010-05-22
> **-humanaut- said:**
> I don't quit understand your question you wiped out a drive then recovered it with an .img file? and What are you trying to do with the .img file?


The problem is that nothing is working. I have never worked with a .img file before and I don't know how to mount or open it. I just need some general help...i am lost in confusion.

---

### Post by AlexDudko on 2010-05-22
Doesn't it open with an Archive Manager? .img is usually a compressed archive.

---

### Post by jamesisin on 2010-05-22
First, make a copy of the disc image which ddrescue created.  Work from the copy.

Second, change the file extension from .img to .iso (they are the same but Ubuntu only understands the .iso--I don't know why).

Now as to mounting your (copy of) disc image, you should be able to do it using the Archive Manager (right-click the ISO, Open With, Archive Manager).  If that doesn't work, you can probably use the mount command from the terminal (probably sudo mount blahblahblah).

If you need to alter the permissions/ownership of the ISO file, you can do that using chmod and chown as necessary (also with sudo).

Does that get you in the right neighborhood?

---

### Post by Nythain on 2010-05-22
i can elaborate a little bit on that too :)

first, make a place to mount the iso, we'll call it /home/<you>/rescue
in a terminal
```

mkdir ~/rescue

```
then mount that bad boy
```

sudo mount -o loop <name of file>.iso ~/rescue

```
hopefully that went well and you can browse the image file
if you need any certain permissions, you can either A. do things as sudo or B.
```

sudo chown <username>:<username> /path/to/what/needs/new/permissions

```

hope that helps explain a little bit of that procedure a little bit

---

### Post by Jacob Krustchinsky on 2010-05-22
> **jamesisin said:**
> First, make a copy of the disc image which ddrescue created.  Work from the copy.

Second, change the file extension from .img to .iso (they are the same but Ubuntu only understands the .iso--I don't know why).

Now as to mounting your (copy of) disc image, you should be able to do it using the Archive Manager (right-click the ISO, Open With, Archive Manager).  If that doesn't work, you can probably use the mount command from the terminal (probably sudo mount blahblahblah).

If you need to alter the permissions/ownership of the ISO file, you can do that using chmod and chown as necessary (also with sudo).

Does that get you in the right neighborhood?


Thank you very much sir! Greatly appreciated :D

---

### Post by jamesisin on 2010-05-22
No problem.  Best of luck.

---

