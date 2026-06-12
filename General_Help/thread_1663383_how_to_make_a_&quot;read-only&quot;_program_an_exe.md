---
title: "how to make a &quot;read-only&quot; program an executable."
date: 2011-01-09
forum: General Help
---

### Post by PyGuy on 2011-01-09
Hello, I'm new to the forums and was hoping I could get some help with installing Sonic R on Ubuntu 64-bit Desktop Edition. I insert the disk, get into the directory and double-click "Install.exe" and it gets the error where it's not marked as "executable". I thought "no problem", and went to the properties to make it executable. To my surprise, I CAN'T make it executable because it's "read only". I can't make it "read and write" because it's "read only"... #-o
This is frustrating because I actually BOUGHT the game...when I was 6-years-old or something...You can't blame me for wanting a nostalgia trip...

In short, is there a way I can run an install EXE, bypassing the "read-only" stuff? I can only get to the Sonic R Directory from the disk...

---

### Post by 0949er on 2011-01-09
im pretty sure you need to edit your "/etc/fstab" as follows:

```

/dev/sr0 /media/dvd-rom auto ro,user,**exec**,noauto,unhide,uid=1000,gid=1000 0 0

```where /dev/sr0 is the path to your cd-rom drive.

oh, and you know that .exe's dont natively run on linux right? I am assuming you are trying to run the setup with wine?

---

### Post by mike555 on 2011-01-09
You do know that Linux won't run Windows programs, right ?

some people might tell you about a program called "WINE" but it only runs some Windows programs and in my opinion is more trouble then it is worth ...

---

### Post by Verbeck on 2011-01-09
> **PyGuy said:**
> 
In short, is there a way I can run an install EXE, bypassing the "read-only" stuff? I can only get to the Sonic R Directory from the disk...
try 
right click > open with other application > use custom command [I]wine
[/I] 
(assuming that you've got wine installed already from the software-center)

---

### Post by hhh on 2011-01-09
.exe is a Windows-only file extension...
[http://en.wikipedia.org/wiki/EXE](http://en.wikipedia.org/wiki/EXE)

Sonic R is a Sega game that hasn't been ported to Linux...
[http://en.wikipedia.org/wiki/Sonic_R](http://en.wikipedia.org/wiki/Sonic_R)

You may be able to get this game running in Linux using Wine...
[http://appdb.winehq.org/](http://appdb.winehq.org/)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5962&iTestingId=18407](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5962&iTestingId=18407)

---

### Post by Spyderkid on 2011-01-09
If your using wine then do this....

(Your lucky it works very well on wine)


[SIZE="2"]AND IF YOU DON'T HAVE WINE INSTALL IT FROM THE SOFTWARE CENTRE (THE NON-BETA RELEASE) THEN DO THIS....[/SIZE]


>you can't without disabling important safety stuff (and im not going to tell you that obviously (partly because I don't know how))

sooooo...

I assume your using some kind of DVD or CD-ROM so when its in do this...
```

cd /media/FILENAME
wine setup.exe 
```

If it says that theres no Setup.exe have a look for it in other directories on the disk. (IF THERES NO setup.exe TRY install.exe BUT TRY seup.exe FIRST

ALSO ON THE FIRST BIT WHERE IT SAYS [FONT="Courier New"]cd /media/FILENAME[/FONT] MAKE SURE YOU PUT THE / AT THE BEGGINING OF MEDIA IT WON'T WORK OTHERWISE





(you can't run Many windows programs on Linux [spotify works well on wine though])

---

