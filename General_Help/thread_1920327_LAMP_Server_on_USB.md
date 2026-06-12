---
title: "LAMP Server on USB"
date: 2012-02-04
forum: General Help
---

### Post by SyntheticShield on 2012-02-04
There are windows options out there where I can just put the files on a USB drive and plug it in and go, you dont have to reboot to load an operating system or anything like that.

Is there any such thing like that for a LAMP stack?

Everything Ive seen so far has been basically installing Linux to a bootable USB then install Apache, MySQL and PHP but I dont want to have to reboot anything, I just want to be able to plug in the USB stick and start the server.

I dont even know if its possible.  I have the web server installed on my Xubuntu computer at home and it works well.  But the majority of the computers I deal with in professional life are Windows.  I was hoping to come up with one solution that would allow me to start a webserver on either of the systems so that I dont have to worry about keeping all the files sync'd and so forth, just pop in the USB stick and go.

---

### Post by dragonfly41 on 2012-02-04
Perhaps you can point both of your servers to a shared docbase on your USB, rather that the default /htdocs/ (or /var/www/ in ubuntu).   Apache/PHP/MySQL can be installed on both Windows and Ubuntu.    Only the docbase would be on USB.   

Perhaps also have a script to backup common docbase USB to both servers.

---

### Post by SyntheticShield on 2012-02-04
Well, thats why I post questions up, 'cause you get so single minded about some things you just loose sight or dont consider other possibilities.

Thank you dradongly41, I will see if I can make that work.

---

### Post by dragonfly41 on 2012-02-04
I should add that I'm getting round to trying the same approach on my dualboot where I have apache and tomcat on both Windows Vista and Ubuntu.

Currently I'm looking at a common editor to use across these dual boot environments and I've recently read in this forum about Bluefish which I've just installed on both ubuntu and windows.   I'm scratching my head to see how localhost is mapped to docbase.

Alternative cross platform IDE is eclipse + Aptana but Bluefish seems lighter weight.

Yet another is jedit available on both windows and ubuntu.

---

### Post by SyntheticShield on 2012-02-04
> **dragonfly41 said:**
> I should add that I'm getting round to trying the same approach on my dualboot where I have apache and tomcat on both Windows Vista and Ubuntu.

Currently I'm looking at a common editor to use across these dual boot environments and I've recently read in this forum about Bluefish which I've just installed on both ubuntu and windows.   I'm scratching my head to see how localhost is mapped to docbase.

Alternative cross platform IDE is eclipse + Aptana but Bluefish seems lighter weight.

Yet another is jedit available on both windows and ubuntu.



I will tell you, I have used Bluefish and I like it.  But I recently discovered Geany and it is for both Linux and Windows.  I think I like Geany a little better.  I have tried Aptana and I just loathe that thing.  Its bloated, slow, etc.  It may be a fairly comprehensive piece of software, but I just dont like it.

If Geany would integrate some code completion (You know, for when you cant remember a tag or something like that) which Bluefish has to some extent, then I would be a complete Geany convert.  I use it more now, as it is, than I do Bluefish.  The one thing I really dont like about Bluefish is that it seems to dump a hidden file everytime you save a document.  If you are working on index.php for example, add some code and save it, then Bluefish saves the file and also make another file ~index.php and Im not crazy about that.  It would not be so bad if it would clean them up when you closed the editor, but it doesnt.

---

