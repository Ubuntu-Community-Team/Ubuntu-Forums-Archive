---
title: "Recovery GRUB"
date: 2010-02-06
forum: General Help
---

### Post by wrixis on 2010-02-06
I knew how to recovery GRUB when GRUB was replaced by Windows system o when somthing went bad, doing changes in the menu file, etc., but with GRUB 1.97 Beta I don't know how to do this kind of things. For instance, to recovery GRUB I did:


```
 sudo grub 
```

```
 find /boot/grub/stage2 
```

```
 root (hdx,y) 
```
X and Y depends on the output of find

```
 setup (hdx) 
```

```
 quit 
```


But now I don't know.


To do changes i edited menu.lst, but now I don't know again.

---

### Post by Leppie on 2010-02-06
there's many guides on grub2, even several on this forum:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)


the wonders of a search engine...

---

### Post by wrixis on 2010-02-06
Thanks. To recovery GRUB I found:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Are there any short way to do it like in GRUB (One)?

---

### Post by Leppie on 2010-02-06
what is it exactly you would like to do?
recovery of grub2 is normally much quicker than recovery of grub legacy imho.

---

### Post by wrixis on 2010-02-06
Anyways, if i don't need to do any changes, 

```
nano /etc/default/grub
```

and

```
update-grub
```

are not necessary. Right?

---

### Post by Leppie on 2010-02-06
well, that depends on what's going on...

---

### Post by wrixis on 2010-02-06
Ok, ok, sorry. The information is too useful and I can do changes again in the configuration. But now I was asking in case of lost the grub. I mean, I have ubuntu and windows, and sometimes I have to reinstall windows but windows remove grub and for that I used to do the commands I told you. I want to know an equivalent method and after read the link I'm wondering if are there any short method like in GRUB One.

---

### Post by Leppie on 2010-02-06
there is a quick way to recover grub2 after having installed something like a windows os onto your system.
you will have to boot off an ubuntu livecd (like karmic or lucid, as long as has grub2). then you need to mount your ubuntu partition, for example:
```
sudo mount /dev/sda5 /mnt   ##most people use /dev/sda5 to install ubuntu into on a double boot system
sudo grub-install --recheck --root-directory=/mnt /dev/sda  ##re-install grub2 into the mbr of the first drive, amend if different drive is needed
```and that's it.

---

### Post by wrixis on 2010-02-06
Thanks Leppie!

---

### Post by Leppie on 2010-02-06
you're welcome

---

