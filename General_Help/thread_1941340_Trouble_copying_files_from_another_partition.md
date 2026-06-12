---
title: "Trouble copying files from another partition"
date: 2012-03-15
forum: General Help
---

### Post by dangthe on 2012-03-15
Hello guys, I am a beginner Ubuntu user and need some help. I installed Ubuntu 10.10 yesterday on my laptop alongside Win7 through Wubi. I am learning web development and want to do so using Ubuntu. All the files I am using are on my second partition (Ubuntu being on the first alongside Windows). So now, I installed LAMP and need to copy my website files in /var/www/ so the Apache server can serve them, but I cannot copy my folders. I tried the mouse right-click copy > paste, but nothing happens. Tried this through console:
sudo cp /media/Storage/Work/Web/Web Files/ /var/www/

the "Web Files" being the folder where my website is on the other partition and /var/www/ being the Apache2 root folder, but I get an error that no such files or directories exist. Any help would be appreciated.
note: I have no problem copying the folders from my Storage partition to a USB stick

---

### Post by TeoBigusGeekus on 2012-03-15
Try with
```
sudo cp "/media/Storage/Work/Web/Web Files/*" /var/www/
```

---

### Post by jerome1232 on 2012-03-15
I just wanted to note the reason you were having trouble via command line was the space, you need to either encase the entire path in quotes as teo did, or escape the spaces with a slash.

ie

```
this/is/my\ path/to\ a\ folder/with/some/spaces/
or
"this/is/my path/to a folder/with/some/spaces/"
```

---

### Post by Mark Phelps on 2012-03-15
OK ... you said > All the files I am using are on my second partition

So, does this mean that all the files are on the Win7 OS partition?

I hope not ...

Because if that is true, making changes to files in that partition while running Ubuntu is asking for filesystem corruption -- and if that should happen, Win7 won't boot anymore.

---

### Post by dangthe on 2012-03-15
> **Mark Phelps said:**
> OK ... you said 

So, does this mean that all the files are on the Win7 OS partition?

I hope not ...

Because if that is true, making changes to files in that partition while running Ubuntu is asking for filesystem corruption -- and if that should happen, Win7 won't boot anymore.

No, the Ubuntu and Windows are on C:/ and all my files, pictures, videos are on D:/. The folders I need transferred are on D:/

---

### Post by gordintoronto on 2012-03-15
When you did the WUBI install, did you make the maximum possible file system for Ubuntu? If not, you're going to be frustrated at some point. WUBI is really to let you play around with Ubuntu until you decide whether you like it.

Ubuntu 10.10 seems like an odd choice, since it will "expire" at the end of next month.

Now to the problem you asked about: from Terminal, run: sudo nautilus
If you click on "438 GB Filesystem," or whatever the size of your D: drive is, you can navigate around to the files you are interested in. Highlight, right-click, select "copy," now navigate to www/var, select Paste. Done.

---

### Post by dangthe on 2012-03-21
> **gordintoronto said:**
> When you did the WUBI install, did you make the maximum possible file system for Ubuntu? If not, you're going to be frustrated at some point. WUBI is really to let you play around with Ubuntu until you decide whether you like it.

Ubuntu 10.10 seems like an odd choice, since it will "expire" at the end of next month.

Now to the problem you asked about: from Terminal, run: sudo nautilus
If you click on "438 GB Filesystem," or whatever the size of your D: drive is, you can navigate around to the files you are interested in. Highlight, right-click, select "copy," now navigate to www/var, select Paste. Done.

I gave it 30GB. Ubuntu 10.10 is the choice because after months of Ubuntu 11.04 and .10 being out, there is still no solution to the AMD Radeon issues. As for the copy / paste solution - it works! Thank you :)

---

