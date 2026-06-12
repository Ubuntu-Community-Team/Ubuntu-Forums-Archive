---
title: "Need your advice - linux peeps"
date: 2010-05-07
forum: General Help
---

### Post by maizuddin35 on 2010-05-07
hello guys.

right now. I have my ubuntu lucid lynx install in my primary harddisk.
I want to install Windows seven on my second harddisk, and I want to dual boot it.
I'm afraid that the grub will be lost. Because I've experience it when I install windows seven, then I can't boot my ubuntu back, but I solve it by reinstalling the grub back by using live cd, but this time, ubuntu is the only listed in the grub.

I want to install windows 7 back , because i have something to do. 

Need your advice, 

1.what should I do to prevent the grub lost.
2.how should I actually install win7 along with ubuntu.

--do I need to unplug my ubuntu hard drive and install win7 alone?
--do I need to leave it be.?
--

thank you ...

---

### Post by marshmallow1304 on 2010-05-07
To minimize the possibility of data loss, I'd do this

1) Unplug the Ubuntu drive
2) Install Windows on the other drive
3) Reattach all drives (make sure the Ubuntu drive is master)
4) Boot into Ubuntu and run the following

```
sudo update-grub
```



You might also look at Virtualbox if you have a few tasks for which you need Windows.

---

### Post by maizuddin35 on 2010-05-07
and..
now, I want to install win7 on my laptop too. My laptop now running linux mint helena. how to handle this?  I don't want to lost the grub, and not booting in back my linux.

---

### Post by maizuddin35 on 2010-05-07
thank you marshmallow1304.Ill try that.
is there any more , guys? idea or something...?
more option?

---

### Post by maizuddin35 on 2010-05-07
i've install virtual box, but I experience lack of performance, because of small RAM.

---

### Post by Carl Hamlin on 2010-05-07
The conventional wisdom when you're preparing to install a dual boot system is to install Windows first, and let it settle into the MBR, *then* put Linux on.

However, if you're unwilling/unable to do it that way, I'd give Marshmallow's suggestion a shot.

---

### Post by maizuddin35 on 2010-05-07
Yes. I know about installing windows first. just now, I had mess something that makes my windows corrupt, and I need to install it back. 
now, maybe,hopefully, marshmallow's suggestion is the one I need to try.

---

### Post by maizuddin35 on 2010-06-20
thanks for the reply post. it does work

---

