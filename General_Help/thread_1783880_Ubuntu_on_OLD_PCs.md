---
title: "Ubuntu on OLD PCs"
date: 2011-06-16
forum: General Help
---

### Post by DominicRowland on 2011-06-16
I am currently working as a volunteer teacher in a school in rural Zambia and although I know next to nothing about computers the other teachers know less which makes me head of ICT...

I recently found some OLD! pcs in a store and discovered they actually work. However they are running Windows XP and are very slo
w. Is there a version of Ubuntu which might be worth installing? 

I also found an Ubuntu 9.04 installation CD gathering dust. How would that compare to XP speedwise?

Thanks in advance.

---

### Post by mike555 on 2011-06-16
You should use version 10.04 because it is supported till April 2012 ......... But you need to check each computer , to see if it'll run Ubuntu , basically 512 Ran and 800mz. processor is lowest that will run Ubuntu decent ........
  if less then 512 RAM then a lighter version of Linux (like Puppy ) might be better .

---

### Post by nothingspecial on 2011-06-16
How old?

How much RAM?

I think you would be better off with lubuntu.

---

### Post by Topsiho on 2011-06-16
Ubuntu usually runs perfectly on older computers, which used to run with Windows XP.

The minimum RAM (working memory), however, should be 256 MB, more is better, and the CPU should be fast enough (more than, say, 500MHz).
The hard disk should be large enough, say 10 GB or more.

There are lighter versions of Ubuntu, such as Xubuntu, and others, I hope that other readers will comment on these.

9.04 is obsolete by now, as it has been supported for only 18 months, just like the other versions are, EXCEPT the versions 6.06, 8.04 and 10.04, which were/are LTS-versions: a bit more dependable, less state of the art, and supported for 3 years on the desktop. So you should get hold of a 10.04.2 version (2nd, eh, how do you call it, edition, to prevent having too many updates after installing). You can download this free from Ubuntu.org, if you have a fast internet connection. Otherwise you should find another way to get it.
Support means that you can update to repair security issues, which have been reported, and to improve installed applications, if you want on a daily basis. Means that your internet connection should be fast enough, sometimes the download is substantial. And: that's why you should NOT use 9.04, if you want to use the internet.

The latest Ubuntu, 11.04, expects a graphics card that knows 3d acceleration, and a driver for this, so for this reason I do not recommend it, especially not on an older computer. But comments on this from other readers are welcome :)

Topsiho

---

### Post by DominicRowland on 2011-06-17
The best one has:

9GB hard disk
800 MHz
128MB RAM 

so I guess 10.04 is out then... 
Never heard of Puppy but I will check it out when I have some time.

---

### Post by zealibib slaughter on 2011-06-17
with those specs then i would go with puppy.

---

### Post by mike555 on 2011-06-17
Puppy is excellent , although a bit of a pain to install , you should read ;  
[https://www.ehow.com/how_5063994_install-puppy-linux-hard-drive.html](https://www.ehow.com/how_5063994_install-puppy-linux-hard-drive.html)    ... or watch a video on how to install on youtube ......

---

### Post by snowpine on 2011-06-17
Give Puppy, SliTaz, and/or TinyCore a try. If your students are kids, then Puppy might be ideal because it is "cute" and playful, although you might want to watch out because Puppy always runs as root user (or at least it used to last time I tried it).

You might also look into "thin client" technology which means a faster computer acts as the server and the slow computers act as terminals: 

[www.ltsp.org](www.ltsp.org)
en.wikipedia.org/wiki/Linux_Terminal_Server_Project

---

### Post by KeyserSoze93 on 2011-06-17
I'd either set them up as the clients or use Puppy. I'm not sure how fast the new Ubuntu-based(?) Puppy runs but the previous version to that works great on old PCs.

I managed to run Puppy on a relatively ancient laptop (can't remember whether it ran XP or 98 before) and it's very user friendly.

It shouldn't really be a problem that it runs as root since the worse anyone can do is mess up that actual PC - in which case you can just reinstall.

If the students are sharing computers then perhaps they could use floppy disks (yeah, I know, but they're cheap) or USB sticks to store their documents in case the PCs do get messed up (or simply break.)

There's really no point trying to get the machines to run a new Ubuntu. Most of my current crop of PCs would struggle with newer versions using the default GUI - I tend to prefer lightweight desktops like Fluxbox.

---

### Post by Topsiho on 2011-06-17
If it's an option you could also try and install some more ram (256 MB is sufficient, 512 is far better), as then you could install the most user friendly version of Linux, Ubuntu.

I don't know the age of your students, if they are younger, than gcompris, which you'll find in the repositories, is quite nice. If they are older, let's say high school or even higher education, you'll find marvellous programs like Octave (open source clone of Matlab) and others.

If Puppy has them too in their repositories, well, you could of course go for Puppy :) I don't know about the lighter versions of Ubuntu. They have the same repositories as Ubuntu itself, I guess.

When installing ram, please be careful you install the correct type. As different makes not always cooperate well you might have to change all ram. But if you can experiment (test with memtest, which is available as a menu option when booting Ubuntu, or from the LiveCD)
you might try this first.

Did you have a look here?:

[http://edubuntu.org/download](http://edubuntu.org/download)

Topsiho

---

### Post by goldshirt9 on 2011-06-17
bastardise some pc's to make a few good pc's.
that way the ram will be better 
if possible that is

---

### Post by LordNeo on 2011-06-17
You should definetively go for Lubuntu or Xubuntu instead of a plain Ubuntu (no matter how old the version is).

---

### Post by Topsiho on 2011-06-17
I have been thinking: Edubuntu can be set up as a server and a number of thin clients, the latter with lower specs. Canonical has done their best to make this as easy as possible.

You can read more at:

[http://www.edubuntu.org/documentation/10.10/installation-guide](http://www.edubuntu.org/documentation/10.10/installation-guide)

This means you should set up a server, with higher specs, and a number of clients, for which 128 MB ram is a bare minimum ...

I have no experience with edubuntu, though,

Topsiho

---

### Post by DominicRowland on 2011-06-20
Thanks for all the replies. 
I will give Wary Puppy a try but a few of the machines only have 28MB of RAM...

The school also has some hardware for Thin Clients but neither I nor anyone else knows how to make it work. 

Some details here [http://ubuntuforums.org/showthread.php?t=1784022](http://ubuntuforums.org/showthread.php?t=1784022)

Thanks

---

### Post by Sylslay on 2011-06-20
Based on my expirence with linux: 


I recommended:

This is the LXDE edition of Linux Mint 9, codename Isadora, based and compatible with Ubuntu 10.04 Lucid Lynx and its repositories. Very stable linux.

[http://www.linuxmint.com/rel_isadora_lxde.php](http://www.linuxmint.com/rel_isadora_lxde.php)
[http://www.linuxmint.com/edition.php?id=60](http://www.linuxmint.com/edition.php?id=60)


And 
LXDE edition of Linux Mint 9, codename Isadora

Sould be easy to install, as Ubuntu and is ready out of box 
include all codec, tweaks etc..

or simply Ubuntu 10.04.2

---

### Post by LapsedCatholic2010 on 2012-05-07
What does it mean that support for 10.04 will expire in April 2012? Will updates no longer be available?

---

### Post by dniMretsaM on 2012-05-07
> **LapsedCatholic2010 said:**
> What does it mean that support for 10.04 will expire in April 2012? Will updates no longer be available?

Yes that's what that means. It expires in 2013, however, not 2012. You can always upgrade to the next LTS (which is 12.04). For future reference, please don't bump old threads.

---

### Post by oldos2er on 2012-05-08
Old thread closed.

---

