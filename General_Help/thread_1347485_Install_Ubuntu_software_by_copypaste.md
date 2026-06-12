---
title: "Install Ubuntu software by copy/paste?"
date: 2009-12-06
forum: General Help
---

### Post by KingNeil on 2009-12-06
I have an external HDD with my previous Ubuntu installation on it, and would like to restore some of the software I had installed onto an entirely new Ubuntu install. 

Specifically, I want to copy Skype onto my new machine. You ask: why don't I just download it? Well, I'm not on the best Internet connection right now.

So, I know most software is stored in /usr/bin or /usr/lib, so is it possible to copy/paste from one drive to another, or is it more complicated than that?

---

### Post by sikander3786 on 2009-12-06
I don't think it will be possible. However there is another software meant to save your downloaded .deb files to be run some other time. Take a look here

[http://ubuntuforums.org/showthread.php?t=646526](http://ubuntuforums.org/showthread.php?t=646526)

---

### Post by KingNeil on 2009-12-06
I know what a DEB file is, but I don't have one on my old installation. 

I've heard that everything in Linux is a file, so presumably you can simply copy a few files here and there and get the software installed. If this doesn't work, why not? If it does, how does it work?

---

### Post by sikander3786 on 2009-12-06
Well I don't think if that is possible. Because all the software has many "dependencies" (other files on which the software itself depends). I am not sure how will you be able to copy all the related files. Let's wait for some one else to reply.

---

### Post by Iowan on 2009-12-06
It might be possible - but not simple. Besides the executable file(s) there will be startup files and configuration files.  There are (most likely) dependencies on other files and possibly links (symlinks?). Life will be easier if the hardware stays the same - otherwise, some of the configuration files may need to be adjusted.

I see my typing is a little slow - again.

---

