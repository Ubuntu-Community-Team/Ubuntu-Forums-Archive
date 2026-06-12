---
title: "How do I install a tar.gz???"
date: 2009-09-06
forum: General Help
---

### Post by thegutterpoet on 2009-09-06
I have just downloaded, to my ubuntu desktop, the kompozer 0.8a4 file, as I have read that the older kompozer versions wont work with my 9.04 jaunty ubuntu...

the file is my desktop and is called:

kompozer-0.8a4-gcc4.2-i686.tar.gz

Clicking on it, opens up the files into an archive manager, but despite reading a few threads regarding installing tar.gz packages, I am having no success...So, apologies for any duplication of topics, but PLEASE help...

a web design program, is the only application I still need to use windows for...and this one, kompozer, from what I understand, is the nearest to dreamweaver I am going to find for linux...and for a novice web designer like myself, who needs solely to meddle somewhat with basic php and html pages on my site.

all help is greatly appreciated,

cheers.
Daniel

---

### Post by mthalis on 2009-09-06
Read this
[http://ubuntuforums.org/showthread.php?t=1242365](http://ubuntuforums.org/showthread.php?t=1242365)

---

### Post by shihkster1015 on 2009-09-06
a tar.gz file is an archive. you have to extract the files from the archive to install

download this link and double click to install
[https://sourceforge.net/projects/kompozer/files/current/0.7.10/kompozer-0.7.10-i386.deb/download](https://sourceforge.net/projects/kompozer/files/current/0.7.10/kompozer-0.7.10-i386.deb/download)

---

### Post by thegutterpoet on 2009-09-06
Thanks for the link to the deb file mate but that version apparently doesn't work too well with my 9.04 ubuntu...

---

### Post by 3rdalbum on 2009-09-06
"gcc4.2-i686"

Means it has been compiled (with GCC) for the i686 architecture. This is a precompiled binary.

Maybe this sounds like a dumb question, but did you try just reading the instructions that come with the package? Either there's something inside the extracted folder that you can double-click to run Kompozer locally, or there's a script that you can run as root to copy the program to a system-wide location.

---

### Post by P4man on 2009-09-06
dont always believe everything you read :)
Did you try installing kompozer from the repository? (add/remove programs?)
I just tried it and it seem to run just fine (version 0.7.10 )

edit: scratch all that, its a precompiled package

---

### Post by scouser73 on 2009-09-06
Let me refer you to [[COLOR="Red"]**Compiling: Easy How To**[/COLOR]]("https://help.ubuntu.com/community/CompilingEasyHowTo")

---

### Post by shihkster1015 on 2009-09-06
How 'bout you try downloading older versions of kompozer
i'm not using ubuntu right now, so sorry can't really help you
i'll install ubuntu when the final version for windows 7 comes out. and by then i'll probably use karmic koala

---

### Post by P4man on 2009-09-06
I just downloaded the tarbal:

[https://sourceforge.net/projects/kompozer/files/current/0.8a4/kompozer-0.8a4-gcc4.2-i686.tar.gz/download](https://sourceforge.net/projects/kompozer/files/current/0.8a4/kompozer-0.8a4-gcc4.2-i686.tar.gz/download)

and its already compiled. You only need to extract it somewhere and run kompozer (you can just double click it).

---

### Post by 3rdalbum on 2009-09-06
> **P4man said:**
> 
Did you try installing kompozer from the repository? (add/remove programs?)
I just tried it and it seem to run just fine (version 0.7.10 )

There are showstopping problems with the version of Kompozer from the repositories. Opening a menu will cause it to crash.

---

### Post by P4man on 2009-09-06
> **3rdalbum said:**
> There are showstopping problems with the version of Kompozer from the repositories. Opening a menu will cause it to crash.

Yep you're right. Got it to crash in 2 minutes. And thats the so called stable version :p.  0.8a4 doesnt seem to have that same problem, but I wouldn't vouch for its stability either :)

---

### Post by brgenst on 2009-09-13
> KompoZer 0.7.10 is not compatible with GTK &#8805; 2.14, hence the crashes on some recent Linux distros like Ubuntu 8.10 and 9.04. Please upgrade to [KompoZer 0.8 alpha]("http://kazhack.org/?tag/editor").       
[http://kompozer.net/](http://kompozer.net/)


I also need help installing tar.gz for 0.8 alpha.

---

### Post by MelDJ on 2009-09-13
try this link:[How to install ANYTHING in Ubuntu!]("http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually")

---

