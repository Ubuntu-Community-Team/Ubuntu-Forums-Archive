---
title: "More than 1024 MB Ram?"
date: 2006-05-01
forum: General Help
---

### Post by HoLoPo1nT on 2006-05-01
Hello folks,

I have recently installed 1.5 GB Ram to my Ubuntu machine but it only sees 1024 MB of it.

Is there a way to utilize all of the memory I have installed or is 1024 the max the OS will see?

Thanks,

HoLo

---

### Post by NeghVar on 2006-05-01
There is a config filke that will allow you to access more of it, I remember reading about it, try a search of the forums and the wiki and you should find it.

---

### Post by Jason_25 on 2006-05-01
Which kernel are you running?  The default i386 kernel doesn't support that much.

---

### Post by GazzaK on 2006-05-02
Jason - are you sure?  my install of Breezy 5.10 see's all of my 3GB

---

### Post by christhemonkey on 2006-05-02
3GB!!!

wow!

I think the i386 does have high memory support enabled as default.

---

### Post by zuccs on 2006-05-02
I am fairly sure my ubuntu 5.10 reads my 2GB just fine....it seems to be running like it is.

Where do I go to to find information like that? Processor speed, RAM etc....?

---

### Post by Zorro on 2006-05-02
Applications -> System Tools -> System Monitor 

That will tell you ;) 

And I have a standard install, and it see's all my 1.5gig.. I would suggest to the original poster to ensure his bios is seeing it.... If so, I'm not sure where to go from there.. :(

---

### Post by HoLoPo1nT on 2006-05-02
Hello there,

Thanks for the replies folks...will do some more research and see what's up.

I am using Kernel 2.6.12-10-386

Thanks,

HoLo

---

### Post by Engnome on 2006-05-02
hardinfo is very good at detecting system specifications.

sudo apt-get install hardinfo

then Applications --> System tools --> System information

---

### Post by rattaro on 2006-05-02
Do you have integrated video?  I once made this mistake.  If you have integrated video, and allocate memory to it, it will take away system memory.  I'm not sure if this is your case, but it was for me, and that was a little funny when I finally figured it out.

---

### Post by oyvindaa on 2006-05-02
[QUOTE=Engnome]hardinfo is very good at detecting system specifications.

sudo apt-get install hardinfo

then Applications --> System tools --> System information[/QUOTE]


Installed hardinfo, and in the "Computer" section it says this (among other things): Distribution: Debian GNU/Linux testing/unstable.

Why is it saying it's "testing/unstable" when it's the full version?

---

### Post by bluenova on 2006-05-04
AFAIK Ubuntu is taken from the latest cvs version of Debian when they start building a new version of ubuntu.

---

