---
title: "The only part of Ubuntu i struggle with"
date: 2010-10-21
forum: General Help
---

### Post by TimEnid on 2010-10-21
installing tar files. 

I downloaded Banshee 1.8.0, this is the name of the file "banshee-1-1.8.0.tar.bz2"

i saved the file to my Downloads folder. I have no idea what to do next. I tried to install from the synaptic, but it only has version 1.7.6. 

And there is no deb file. Can someone please help me out. Ive tried googling for directions, but they are not too clear to me. appreciate the help.

---

### Post by TBABill on 2010-10-21
It's a compressed file, similar to zip files. [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

---

### Post by James78 on 2010-10-21
Also, .tar.gz, .tar.bz2, etc, files commonly have source code in them. So if it does, you will have to compile it, then install it.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by TimEnid on 2010-10-21
> **TBABill said:**
> It's a compressed file, similar to zip files. [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

im just having trouble installing them. i typed in "tar jxvf banshee-1-1.8.0.tar.bz2", but i keep getting no such file directory

---

### Post by boombox1387 on 2010-10-21
> **TimEnid said:**
> im just having trouble installing them. i typed in "tar jxvf banshee-1-1.8.0.tar.bz2", but i keep getting no such file directory

Blegh, extracting tar files from the command line was one thing that I never took the time to try to understand.  :) Assuming you have a GUI handy, you can just right-click and choose "extract here." That will do all the extracting for you.

From a command line, then you'll want to build Banshee from source.  In this case, you should cd into the extracted folder, then run:

```
./configure
```
then
```
make && sudo make install
```

But really, if you just want to use the latest Banshee, the easiest way to get it is [through its PPA.]("https://edge.launchpad.net/~banshee-team/+archive")  Or from the command line, just run: "sudo add-apt-repository ppa:banshee-team/ppa".  Subscribing to the PPA will automatically keep Banshee up-to-date through Ubuntu's regular update manager, so you can just check for updates to get the latest version (1.8.0 in this case).

---

### Post by James78 on 2010-10-21
> **boombox1387 said:**
> But really, if you just want to use the latest Banshee, the easiest way to get it is [through its PPA.]("https://edge.launchpad.net/~banshee-team/+archive")  Or from the command line, just run: "sudo add-apt-repository ppa:banshee-team/ppa".  Subscribing to the PPA will automatically keep Banshee up-to-date through Ubuntu's regular update manager, so you can just check for updates to get the latest version (1.8.0 in this case).
Like I say. Never build something from source when you don't need too. PPA's and the already available repositories have most packages. :P

---

### Post by TimEnid on 2010-10-23
> **boombox1387 said:**
> E]

But really, if you just want to use the latest Banshee, the easiest way to get it is [through its PPA.]("https://edge.launchpad.net/~banshee-team/+archive")  Or from the command line, just run: "sudo add-apt-repository ppa:banshee-team/ppa".  Subscribing to the PPA will automatically keep Banshee up-to-date through Ubuntu's regular update manager, so you can just check for updates to get the latest version (1.8.0 in this case).

this is the option i went with. thanks.

---

### Post by perspectoff on 2010-10-23
Just click on the file from Nautilus, Dolphin, or whatever file manager you're using.

That will brink up Ark, the archiving program, which will give you the options for extracting.

Folder permissions can sometimes be tricky. If you are trying to extract into a folder for which you don't have permission, it won't work. (This is true of many system folders which have root permissions).

You can often add

 sudo

before the tar and get it to work.

Alternatively, you can extract to a folder for which you do have permissions and then subsequently copy (as root or sudo) to the folder that requires root permissions.

Also note that some older versions of tar used I instead of j for bzip2 files, so that

 tar Ixvf filename

---

### Post by perspectoff on 2010-10-23
> **James78 said:**
> Like I say. Never build something from source when you don't need too. PPA's and the already available repositories have most packages. :P

Kind of true and kind of not.

Not every package distributes its updates through PPAs. Many, many Linux programs don't even bother with .deb packages (yet, lol).

Further, PPAs are often not maintained by the original program developers and can themselves be out-of-date.

But often the PPAs are indeed an easier way to go than installing and comiling from source, especially for newbies. It is important to recognize that PPAs are not officially reviewed by Ubuntu/Debian developers, though, and can contain a mixed bag of software. Appropriate caution is warranted when using PPAs.

---

### Post by James78 on 2010-10-23
> **perspectoff said:**
> ... Many, many Linux programs don't even bother with .deb packages (yet, lol).

Further, PPAs are often not maintained by the original program developers and can themselves be out-of-date.
That'd qualify under needing to build it from source. ;)

---

