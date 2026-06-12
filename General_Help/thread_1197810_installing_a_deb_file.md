---
title: "installing a deb file"
date: 2009-06-26
forum: General Help
---

### Post by drdob on 2009-06-26
i know i am thick but i have read the instructions in man and help in the ubuntu books,and on this forum but, it will not work :confused::( i am trying to install a deb file and i down loaded it, and uncompressed the tar file. i have tried sudo dpkg clamav.0.95.2.deb ( clamav.0.95.2.deb this what i am trying to load) and it will do nothing. Can anybody out there please put me out of my confusion. thank you Drdob

---

### Post by blackened on 2009-06-26
Are you using the *-i* switch? If you'll read the man page, *-i* stands for *install*.

Also, you must either specify a full path to the deb file, or your working directory must be where the deb file is stored. So, if the deb file were on the desktop, then you would use:

```
sudo dpkg -i ~/Desktop/clamav.0.95.2.deb
```
or
```
cd ~/Desktop
sudo dpkg -i clamav.0.95.2.deb
```

You're probably just missing the -i switch though.

---

### Post by merlinus on 2009-06-26
On my machine, I can right-click on a .deb and select Open with GDebi Package Installer.

---

### Post by blueridgedog on 2009-06-26
Can't you simply double click the *.deb file?

---

### Post by merlinus on 2009-06-26
Works the same here...

---

### Post by blackened on 2009-06-26
> **merlinus said:**
> On my machine, I can right-click on a .deb and select Open with GDebi Package Installer.

Of course you're right, as long as you're using a GUI, but for those who either choose to (or have no choice but to) run only a CLI, GDEBI isn't an option.

---

### Post by philcamlin on 2009-06-26
double click the .deb

---

### Post by drdob on 2009-06-27
Thank you all for replying :D I have tried ::
 drdob@drdob-laptop:~$ sudo dpkg -i ~/Desktop/clamav.0.95.2.deb
   and the other one, and I get :
dpkg: error processing /home/drdob/Desktop/clamav.0.95.2.deb (--install):

 cannot access archive: No such file or directory

Errors were encountered while processing:

 /home/drdob/Desktop/clamav.0.95.2.deb

I have look on synaptic packet manager and I have  GDebi Package Installer. I think it is marked and so is gdebi core, how do I access it? I have right clicked and looked on the 'open with' but can not see it.:( i must have missed something, or done something wrong. drdob

---

### Post by wojox on 2009-06-27
open a terminal

```
sudo apt-get install clamav-daemon
```

---

### Post by howefield on 2009-06-27
> **drdob said:**
>  cannot access archive: No such file or directory

Sure you have spelled the file right ? (Possibly a hyphen and not a period between clamav and 0)

---

### Post by ~sHyLoCk~ on 2009-06-27
> **blueridgedog said:**
> Can't you simply double click the *.deb file?

That's fine. However, if you have a folder full of .deb files do this:~
```
sudo dpkg -i *.deb
```

---

### Post by drdob on 2009-06-29
thank you all for your replies :D I will try them all, but at the moment my internet connection is playing up (it is a ISP thing ) and it is taking hours to load a page!!  yours DrDob

---

### Post by 3rdalbum on 2009-06-29
> **drdob said:**
> i am trying to install a deb file and i down loaded it, and uncompressed the tar file.

I'm confused - you downloaded a deb and you uncompressed a tar? And double-clicking on the Deb package does not open the Gdebi package installer?

Are you sure it's a Debian package that you're talking about?

If you copy in this code block:

```
sudo dpkg -i 
```

(including the trailing space) and drag the file into the terminal, and press Enter, what happens?

---

### Post by alberto ferreira on 2009-06-29
Note that you can also be using a 64bit Ubuntu while trying to install a 32bit deb package or vice-versa

---

### Post by drdob on 2009-06-29
To : blackend, merlinus, blueridgedog, philcamlin, wojox, howefield, shylock, 3rdalbum, alberto ferreira,  thank you for your help I have done it now, thank goodness.:popcorn: Regarding “right-click on a .deb and select Open with GDebi Package Installer.” from merlinus, i have checked and I have Gdebi in my machine but I do not seem to be able to acsess it:confused: yours Dr Dob

---

### Post by anewman on 2009-07-27
> **wojox said:**
> open a terminal

```
sudo apt-get install clamav-daemon
```

This installs the old version.

---

### Post by magmon on 2009-07-27
What version of ubuntu are you running? I beleive clam AV is in the add/remove if all else fails, but you should be able to simply double click the file to make the gdebi installer work. If that's down, Im a total noob to coding so perhaps one of the more experianced users can help you.

---

### Post by drdob on 2009-07-28
thank you all :D for your help like I said _I Will_ get the hung of it one day ;-) Dr Dob

---

### Post by DeMus on 2009-07-28
When you downloaded a file and you need to uncompress it using untar it is probably not a .deb file what is inside the .tar.gz file.
I think you mix up two ways of installing a program:
1)
a .deb file which can be downloaded on many websites and which can be opened using Gdebi. When you start the download it gives you the choice of saving the file or open it using Gdebi. A .deb file is the standard Ubuntu/Debian way of installing programs.
2)
a.tar.gz file which needs to be uncompressed. The result is a folder filled with files. The ones you need to use now are configure, make and make install. This is the standard Unix/Linux way of installing files. I hate this way because I never managed to install a program that way.
You started this thread by writing you read a lot about it. Well do some more reading and you find it. For example read this:
[_https://help.ubuntu.com/9.04/index.html_]("https://help.ubuntu.com/9.04/index.html")
Success.

---

