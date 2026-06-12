---
title: "Newish to Ubuntu, have questions."
date: 2012-09-15
forum: General Help
---

### Post by GratefulDean on 2012-09-15
I finally acquired a laptop (Dell Precision M4300) whose sole purpose will be for me to get to know Linux. I have installed 12.04 on it as the only OS.  What I would like to do is partition the remaining 145gb into 3 total partitions so that I may install various distros alongside 12.04 to play around with.

Again, I will not be using this for word processing, email, games, etc.  I want to understand what Linux is about at the fundamental level. I don't get it.  Debian? KDE vs Unity vs Gnome? How is one thing different than the other? You see, I am a noooooooob.

 I briefly flirted with Ubuntu (Maverick Meerkat) on a primary machine but kept buggering up the works and since it was my primary I had to give up until I could get something I wasn't relying on for work.

So, the questions:

1) How do I create the partitions?  In 10.10 I remember it being pretty straight forward in Disk Utility.  Now, not so much.  I also picked up GParted but still can't figure it out.

2) At the moment I have a 4GB extended Partition and 4GB swap, do I need to create additional swaps for each partition?  Should I just expand the existing extended and swap partitions?  Or is 4GB OK?

3) Might I get away with 3 or even 4 partitions?  What's the minimum size partition one could get away with in Linux?

4) What are some excellent resources for a noob such as myself to learn the fundamentals of Linux?  Every online resource seems to drop terms like I should know them...

Thanks for now, 
Dean

---

### Post by GreatDanton on 2012-09-15
1. I don't understand what is the problem here. Click on free space, format it and make partitions. Keep in mind that you will have to create Extended partiton. I found some article about this: [http://jcyberinux.com/rjdreyes/gparted-to-create-extended-or-logical-partition.html](http://jcyberinux.com/rjdreyes/gparted-to-create-extended-or-logical-partition.html)

2. You can have one swap. There is no need for more.

3. I am not sure how much Linux uses (somewhere around 4-5 gb I think). But if you want to use it just for testing I would make 10gb partitions, and you will also have enough space for other software (ex. Inkscape).

4. Maybe look for ebooks like this one: [http://www.ubuntugeek.com/getting-started-with-ubuntu-12-04-precise-pangolin-pdf-guide.html#more-13567](http://www.ubuntugeek.com/getting-started-with-ubuntu-12-04-precise-pangolin-pdf-guide.html#more-13567)
I still think you will learn most if you will be reading this forum, and if you will be just playing with Ubuntu (not games).

Hope this helps

---

### Post by Epodx64 on 2012-09-15
[http://www.distrowatch.com](http://www.distrowatch.com)

check out that site for many many distribution choices.
I'd also recommend minimum 10Gb partitions honestly don't overwhelm yourself with 3-4 distro's at once you'll just get frustrated when I first was learning Linux the best way I found was to learn the in's and out's of one distro at a time (for me it was Debian back in '01) If you learn Debian(or Ubuntu) you'd be surprised just how much of it applies to Linux overall but you only have to focus on the nuances of one package manager and apt is probably light years ahead of anything in the Fedora/RedHat RPM camp.
 Once your comfortable working in a terminal and understand the basics of Bash then I'd say branch out it'll be alot easier for you if you can diagnose things for yourself from a terminal that you learned from one installation. I'd suggest starting with Ubuntu then branching off to Debian then go from there. 
/my 2 cents.

---

### Post by josephmills on 2012-09-15
> **GratefulDean said:**
> 

So, the questions:

1) How do I create the partitions?  In 10.10 I remember it being pretty straight forward in Disk Utility.  Now, not so much.  I also picked up GParted but still can't figure it out.

How to use Gparted 

[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)
[http://www.youtube.com/watch?v=5TK5YezY-Xc&feature=related](http://www.youtube.com/watch?v=5TK5YezY-Xc&feature=related)
[http://www.youtube.com/watch?v=TBnVGLiRmdw](http://www.youtube.com/watch?v=TBnVGLiRmdw)


> 
2) At the moment I have a 4GB extended Partition and 4GB swap, do I need to create additional swaps for each partition?  Should I just expand the existing extended and swap partitions?  Or is 4GB OK?

I would say watch this for swap 
[http://www.youtube.com/watch?v=3dhIBcR1cTw](http://www.youtube.com/watch?v=3dhIBcR1cTw)



> 
3) Might I get away with 3 or even 4 partitions?  What's the minimum size partition one could get away with in Linux?

Yeah but if you have the ram and cpu Look into something virtual. 
Like virtual box 
qemu 
vmware 

that way you can just make virtual OS and test there, you will see that there are many many options like taking a snapshot and many other things that Virtual OS's can do. 

Go to Youtube and google 
"Virtual box Ubuntu "

> 
4) What are some excellent resources for a noob such as myself to learn the fundamentals of Linux?  Every online resource seems to drop terms like I should know them...


Ubuntu VTC 
[http://www.youtube.com/watch?v=zXeQdgSHfP0&playnext=1&list=PLE86D2BD487501246&feature=results_main](http://www.youtube.com/watch?v=zXeQdgSHfP0&playnext=1&list=PLE86D2BD487501246&feature=results_main)



There are books in the software center.
wiki.ubuntu.com

Youtube 

Ubuntu User days 
[https://wiki.ubuntu.com/UserDays](https://wiki.ubuntu.com/UserDays)

Ubuntu Classroom 
[https://wiki.ubuntu.com/Classroom](https://wiki.ubuntu.com/Classroom)


ubutnu classes 
[http://www.youtube.com/watch?v=460IxkYmZxQ](http://www.youtube.com/watch?v=460IxkYmZxQ)


debian new maintianers guide 
[http://www.debian.org/doc/manuals/maint-guide/](http://www.debian.org/doc/manuals/maint-guide/)

---

### Post by GratefulDean on 2012-09-15
> **GreatDanton said:**
> 1. I don't understand what is the problem here. Click on free space, format it and make partitions. Keep in mind that you will have to create Extended partiton. I found some article about this: [http://jcyberinux.com/rjdreyes/gparted-to-create-extended-or-logical-partition.html](http://jcyberinux.com/rjdreyes/gparted-to-create-extended-or-logical-partition.html)

2. You can have one swap. There is no need for more.

3. I am not sure how much Linux uses (somewhere around 4-5 gb I think). But if you want to use it just for testing I would make 10gb partitions, and you will also have enough space for other software (ex. Inkscape).

4. Maybe look for ebooks like this one: [http://www.ubuntugeek.com/getting-started-with-ubuntu-12-04-precise-pangolin-pdf-guide.html#more-13567](http://www.ubuntugeek.com/getting-started-with-ubuntu-12-04-precise-pangolin-pdf-guide.html#more-13567)
I still think you will learn most if you will be reading this forum, and if you will be just playing with Ubuntu (not games).

Hope this helps
Thanks for the reply,

I am not that familiar with the process.  I recall under 10.10 you could click the partition you wanted to partition further and it walked you through it.  Or maybe that was in Windows 7.  Anyway, I will review your link and see what I can do.

Thanks again,
Dean

---

### Post by GratefulDean on 2012-09-15
> **Epodx64 said:**
> [http://www.distrowatch.com](http://www.distrowatch.com)

check out that site for many many distribution choices.
I'd also recommend minimum 10Gb partitions honestly don't overwhelm yourself with 3-4 distro's at once you'll just get frustrated when I first was learning Linux the best way I found was to learn the in's and out's of one distro at a time (for me it was Debian back in '01) If you learn Debian(or Ubuntu) you'd be surprised just how much of it applies to Linux overall but you only have to focus on the nuances of one package manager and apt is probably light years ahead of anything in the Fedora/RedHat RPM camp.
 Once your comfortable working in a terminal and understand the basics of Bash then I'd say branch out it'll be alot easier for you if you can diagnose things for yourself from a terminal that you learned from one installation. I'd suggest starting with Ubuntu then branching off to Debian then go from there. 
/my 2 cents.


Yea, I am not digging this flavor of Unity.  I liked how Maverick Meerkat was laid out. I want to check out a bunch of different ones then choose the one to dive in to.  I think.

---

### Post by Epodx64 on 2012-09-15
> **GratefulDean said:**
> Yea, I am not digging this flavor of Unity.  I liked how Maverick Meerkat was laid out. I want to check out a bunch of different ones then choose the one to dive in to.  I think.

Linux Mint 13 Cinnamon is pretty good I wasn't a big fan of Unity either or gnome really I used KDE (Kubuntu 9.04-12.10) for a long time but I recently got tired of KDE as well so I tried out Cinnamon (which you can get for Ubuntu  here's a good tutorial:[http://www.dedoimedo.com/computers/ubuntu-cinnamon.html](http://www.dedoimedo.com/computers/ubuntu-cinnamon.html)) and so far I like it not nearly as resource heavy as KDE\Kwin was and I'm a sucker for new technologies.

---

### Post by GratefulDean on 2012-09-18
> **Epodx64 said:**
> Linux Mint 13 Cinnamon is pretty good I wasn't a big fan of Unity either or gnome really I used KDE (Kubuntu 9.04-12.10) for a long time but I recently got tired of KDE as well so I tried out Cinnamon (which you can get for Ubuntu  here's a good tutorial:[http://www.dedoimedo.com/computers/ubuntu-cinnamon.html](http://www.dedoimedo.com/computers/ubuntu-cinnamon.html)) and so far I like it not nearly as resource heavy as KDE\Kwin was and I'm a sucker for new technologies.

I tried that, I also tried Gnome but, after I log out, then select Gnome or Cinnamon and log back in I still get Unity.

I will hit it again when I have time at the end of the week.

Thanks,
Dean

---

