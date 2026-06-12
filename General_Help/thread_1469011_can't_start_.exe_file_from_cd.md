---
title: "can't start .exe file from cd"
date: 2010-05-01
forum: General Help
---

### Post by compiz addict on 2010-05-01
I was going to try to install the Sims 2 under WINE, but when I try to open the AutoRun.exe file from the CD, I get a permission denied error, because the exe doesn't have execution privileges. Here's the real problem: I can't give it execution privileges, because it's on a read only disk. So, is it possible to start it anyway? Also, the game uses 4 CDs, this is the first one. Will that cause a problem (like something along the lines of "please insert next disk" when the next disk is already in.)?

---

### Post by compiz addict on 2010-05-01
Ok, found a solution to the first program:

```

cd /media/NameOfYourCD
sudo su
wine executableName.exe

```

So now it's installing from the first disk. Hopefully all goes well, if not i'll post another reply.

---

### Post by 3rdalbum on 2010-05-01
> **compiz addict said:**
> Ok, found a solution to the first program:

```

cd /media/NameOfYourCD
sudo su
wine executableName.exe

```

So now it's installing from the first disk. Hopefully all goes well, if not i'll post another reply.

Don't install Windows programs as root. Windows programs get installed into the .wine folder inside your home directory. If you run a Windows program installer as root, then it will go into root's home directory, not into yours.

Cancel your installation and do the same thing, but without "sudo su". Or type "wine" and then drag the exe file onto the terminal.

---

### Post by compiz addict on 2010-05-01
Just as a feared. It's asking for the second disk, and as I forced unmount on the first CD (sudo umount -l /media/Sims2_1) I don't know how to mount the second one.

---

### Post by mc4man on 2010-05-01
As 3rdalbum posted - one of the workarounds is 
wine /path/to/<the setup>.exe
Ex.
wine /media/COD1/Setup.exe

Then for 2nd disk, in a terminal
wine eject

some other methods
[http://ubuntuforums.org/showthread.php?p=9213444#post9213444](http://ubuntuforums.org/showthread.php?p=9213444#post9213444)

---

### Post by compiz addict on 2010-05-01
ok, so after I eject the first disk, how to I mount the second?
When I put the CD in, and go straight to "Computer", I see my CD/DVD drive pop up, for about 5 seconds, and then go away.\

EDIT:
made a new thread for my new problem:
[http://ubuntuforums.org/showthread.php?p=9214853#post9214853](http://ubuntuforums.org/showthread.php?p=9214853#post9214853)

---

