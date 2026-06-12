---
title: "Losing free space on USB?"
date: 2011-01-18
forum: General Help
---

### Post by cod500 on 2011-01-18
Hello, I am new to Linux and this forum. I have Ubuntu and mint persistent on a usb for my laptop. I have noticed that all of my free space is gone just from browsing the internet using applications and I can't get it back. I have tried bleachbit but it has only retrieved 150 mb back. Where do a the files go? How do I delete it? Thank you.

---

### Post by Zimmer on 2011-01-18
Why not run the disk useage analyser (Accessories) and see what you can find... how much cache do you allow your browser in its settings BTW? 

also thumbnails can be a significant issue...

---

### Post by cod500 on 2011-01-18
> **Zimmer said:**
> Why not run the disk useage analyser (Accessories) and see what you can find... how much cache do you allow your browser in its settings BTW? 

also thumbnails can be a significant issue...


Right now I'm on the computer with Linux mint 9 xfce and I do not see a disk usage analyzer in accessories. Do I have to download it?

---

### Post by Zimmer on 2011-01-18
it is part of the package called  gnome-utils
The program itself is called BAOBAB

---

### Post by Zimmer on 2011-01-18
[http://forums.linuxmint.com/viewtopic.php?f=90&t=46441&start=0](http://forums.linuxmint.com/viewtopic.php?f=90&t=46441&start=0)

alternative for you

---

### Post by cod500 on 2011-01-18
> **Zimmer said:**
> [http://forums.linuxmint.com/viewtopic.php?f=90&t=46441&start=0](http://forums.linuxmint.com/viewtopic.php?f=90&t=46441&start=0)

alternative for you

I actually searched that thread before posting here again. I don't even understand how that was solved. He said "there is an xfce panel app you may want to look at." and the other guy said "there it is" I have no clue what he found or where he found it. I guess I wil keep searching. I can't find that Baobab thing in in software manager either.

---

### Post by pl@yer on 2011-01-18
From the CLI

you can probably get some space back if you clean up cached debs.
```

apt-get clean

```

you could look for files larger than 50MB and report their size with this command. 
```

find / -type f -size +50M -exec du -sh {} \;

```

you could look to see where the space is being used. Starting at / (root of the file system) then cd to the bigger dirs and rerun the command etc...etc...
```

du -sh /*

```

Disk usage analyzer is pretty sweet though. I would check to see if it is available in your distro.

```

apt-cache search disk|grep -i usage

```

---

### Post by cod500 on 2011-01-18
I got the disk analyzer, I still have no clue where the files went. Free space in home folder just dwindles away.

---

### Post by hwttdz on 2011-01-18
Use baobab to scan your home directory.  Find those places that have high percentage use, investigate to see if you can get rid of some of those files.  It also sounds like browser cache might be using up a bit much space, so in your browser clear your cache and then change the amount of space it's allowed (you might want to not use cache at all if you're really pressed for space).

---

### Post by cod500 on 2011-01-19
> **hwttdz said:**
> Use baobab to scan your home directory.  Find those places that have high percentage use, investigate to see if you can get rid of some of those files.  It also sounds like browser cache might be using up a bit much space, so in your browser clear your cache and then change the amount of space it's allowed (you might want to not use cache at all if you're really pressed for space).

After a full day of turning of my browser cache, I have not been losing much memory. I guess the browser cache took the memory but I could not get it back so it kept taking my persistent space. Thank you the help.

---

### Post by dcstar on 2011-01-20
> **cod500 said:**
> Hello, I am new to Linux and this forum. I have Ubuntu and mint persistent on a usb for my laptop. I have noticed that all of my free space is gone just from browsing the internet using applications and I can't get it back. I have tried bleachbit but it has only retrieved 150 mb back. **Where do a the files go?** How do I delete it? Thank you.

[http://ubuntuforums.org/showpost.php?p=6304135&postcount=7](http://ubuntuforums.org/showpost.php?p=6304135&postcount=7)

---

### Post by cod500 on 2011-01-20
> **dcstar said:**
> [http://ubuntuforums.org/showpost.php?p=6304135&postcount=7](http://ubuntuforums.org/showpost.php?p=6304135&postcount=7)


So it's probably better to make the usb within ubuntu itself from a live cd.

---

