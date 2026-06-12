---
title: "What's with all the memory usage? :("
date: 2006-03-27
forum: General Help
---

### Post by Piggah on 2006-03-27
I havn't really cared for a while about memory usage, since it's not been a problem with a gig of ram. I have noticed that I'm using TONS of memory for just about nothing. 

On average, I'll have gaim, firefox, rhythmbox and some gdesklets running and I'll be using 400 or megs of ram. It just doesn't seem right. It gets crazy when I start to seriously multitask. It's not a huge problem for me since I do have plenty of ram I guess, but I've just been wondering if there's something I can do about it. I thought that memory leaks might be a possibility, but I don't know how check for them. 

Any suggestions or some info on why I'm using soooo much memory? Is this fairly common? =\

Thanks :)

---

### Post by aysiu on 2006-03-27
Read this:
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by taurus on 2006-03-27
And don't forget to count all the deamons that you have running when you boot your system!!!  Turn off stuff that you don't use and the system will go easy on your RAM!

---

### Post by sprinkles on 2006-03-27
[QUOTE=Piggah]I havn't really cared for a while about memory usage, since it's not been a problem with a gig of ram. I have noticed that I'm using TONS of memory for just about nothing. 

On average, I'll have gaim, firefox, rhythmbox and some gdesklets running and I'll be using 400 or megs of ram. It just doesn't seem right. It gets crazy when I start to seriously multitask. It's not a huge problem for me since I do have plenty of ram I guess, but I've just been wondering if there's something I can do about it. I thought that memory leaks might be a possibility, but I don't know how check for them. 

Any suggestions or some info on why I'm using soooo much memory? Is this fairly common? =\

Thanks :)[/QUOTE]

I asked about this when I started using Ubuntu, and apparantly it just reserves all the memory it might need.

---

### Post by Barrakketh on 2006-03-27
Another thing to note is that "images" (namely, shared objects, Windows name: DLLs) are "mapped" into memory as opposed to loaded.  The memory might not be really used, but it's easily accessible by the program that can make use of it.

This is also true for X's memory usage.  The RAM in your video card is also mapped into memory, and it makes it seem as if X is using much more memory than it really is.

---

### Post by terranz on 2006-03-27
[QUOTE=taurus]And don't forget to count all the deamons that you have running when you boot your system!!!  Turn off stuff that you don't use and the system will go easy on your RAM![/QUOTE]

I stopped three services from running on startup but when I shut down I can see that they are being stopped.  Each time.

---

### Post by nanotube on 2006-03-28
even if a service is not running, the system will /try/ to stop it, and in the process display "stopping bla bla". so that is not a problem. :)
you should of course check while the system is running, whether the processes are present, in which case that would indicate that you did not properly disable them. but even if you do, the "stopping" message will still show up.

---

