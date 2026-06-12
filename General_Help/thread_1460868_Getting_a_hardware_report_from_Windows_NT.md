---
title: "Getting a hardware report from Windows NT"
date: 2010-04-23
forum: General Help
---

### Post by quadproc on 2010-04-23
Folks,

I am about to convert a Windows NT system to linux and, before I do this, I would like to get a hardware report from the system.  I would like to get things such as CPU type, memory size, graphics type, NIC type, etc.

I recall having seen this sort of information on an NT system long ago but I cannot find it now.  Does anyone know where to look?

Thanks.

quadproc

---

### Post by ajgreeny on 2010-04-23
My simple answer to your question is, I'm afraid that I haven't a clue.

However, before you start to wonder why I answered at all, just run the Ubuntu Live CD, and in the terminal use command ```
sudo lshw > hardware.txt && gedit hardware.txt
``` and then print out the hardware.txt file if you want hard copy.

If you prefer an html output use ```
sudo lshw -html > hardware.html && firefox hardware.html
``` and you will get a more easily readable html page readable in firefox.

---

### Post by doas777 on 2010-04-23
I think this is what you are looking for:
[http://support.microsoft.com/kb/308579](http://support.microsoft.com/kb/308579)

---

### Post by quadproc on 2010-04-23
> **doas777 said:**
> I think this is what you are looking for:
[http://support.microsoft.com/kb/308579](http://support.microsoft.com/kb/308579)
That is close, but unfortunately it is targeted for XP and later versions; NT doesn't have a hardware manager, at least not one that comes with the OS.  Replacing NT with a decent OS will be cause for a celebration here.

The other suggestion from ajgreeny is a good idea; I will see if I can get what I am after from a Live CD.

Thanks for your responses; now marking this thread as solved.

quadproc

---

### Post by oldfred on 2010-04-23
For windows I ran this. I liked that it also reported all those serial number that you need in windows to reinstall stuff. Of course in Ubuntu you do not need any serial numbers.:)

[http://www.belarc.com/free_download.html](http://www.belarc.com/free_download.html)

---

### Post by tonymoloney on 2010-05-05
Hey, that's a really useful tip.

It seems to me that if I'm looking at a foreign Windows system, all I have to do is boot a live Linux CD then run that command in a terminal.

Or would I run into a problem when sudo asks for a password?

---

### Post by cascade9 on 2010-05-05
> **quadproc said:**
> That is close, but unfortunately it is targeted for XP and later versions; NT doesn't have a hardware manager, at least not one that comes with the OS.  Replacing NT with a decent OS will be cause for a celebration here.

NT sort of does (depending on the version, this may or may not move, its been so long since I used NT3.51 and NT4.0 I forget)- 

Control Panel-> System-> Hardware Profiles

See also- 

 Start-> Programs-> Admin. Tools-> NT Diagnostics

Easier to use blarc advisor like oldfred posted, or everest. 

[http://www.lavalys.com/community/blog/2010/03/everest-v550-now-available](http://www.lavalys.com/community/blog/2010/03/everest-v550-now-available)

Pity that lavalys stopped providing the free 'home' edition of everest, it was one of the best of the hardware detection programs. BTW, it wont run on NT3.51 or earlier...NT4+ works.

---

