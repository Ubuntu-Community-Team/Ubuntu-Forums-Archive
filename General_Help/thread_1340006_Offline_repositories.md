---
title: "Offline repositories"
date: 2009-11-28
forum: General Help
---

### Post by knit.manish on 2009-11-28
:):):)hiiii frnds is there some working method by which we can make offline repositories for ubuntu 9.10 so that we can install applications even if we r not connected to internet
i have tried a few methods but none of them was useful to me e.g 

dpkg-scanpackages debs /dev/null | gzip > /home/phu/debs/dists/karmic/local/binary-i386/Packages.gz 

and also through sudo apt-get mirror

please help me as i dont have permanent net connection so each time for updation or after fresh install of ubuntu i have to go to cyber cafe.


and more question is there  that the repository of ubuntu feisty can work in ubuntu karmic or not??? if yes then why do we have two seperate repository

thanx and regards:):):)

---

### Post by Aearenda on 2009-11-28
See [this thread]("http://ubuntuforums.org/showthread.php?t=1338029") - aptoncd might work for you.

---

### Post by 3rdalbum on 2009-11-28
> **knit.manish said:**
> and more question is there  that the repository of ubuntu feisty can work in ubuntu karmic or not??? if yes then why do we have two seperate repository

Probably not. You'd end off with system breakage, because Karmic's packages are 30 months newer than Feisty's, and the whole Ubuntu system has dramatically changed since 2007.

Why, do you need a package that was available in Feisty's repositories? You could try just finding a .deb package for it, or compile it from source.

---

### Post by mac9416 on 2009-11-28
knit.manish, you should look at [Keryx]("http://keryxproject.org"). Keryx looks and acts a lot like Synaptic, but it is portable and cross-platform. You make a Keryx "project" (essentially a snapshot of APT) on your offline computer, then take it on a flash drive to an online machine to download packages.

You'll want to take a look at the tutorial and see what it's all about.
[http://crashsystems.net/2009/01/keryx-tutorial/](http://crashsystems.net/2009/01/keryx-tutorial/)

Good luck, and let me know how it goes!

---

### Post by knit.manish on 2009-11-29
> **3rdalbum said:**
> Probably not. You'd end off with system breakage, because Karmic's packages are 30 months newer than Feisty's, and the whole Ubuntu system has dramatically changed since 2007.

Why, do you need a package that was available in Feisty's repositories? You could try just finding a .deb package for it, or compile it from source.


actually i dont need a feisty package , one of my friend has given me offline repository for feisty which i tried in jaunty and it worked but it doesn't works in karmic that's why i was asking for it
and i dont know the method for downloading the repository and my friend is also not available at the moment

---

### Post by knit.manish on 2009-11-30
thanx for all the suggestions i used aptoncd for making offline repository and it worked but there are other method also which i had tried but they didn't worked two of them i have mentioned earlier. Can anyone tell me about them plz

---

### Post by carolineictwiki on 2010-02-01
I am struggling to find a elegant way to share programs between off-line Ubuntu computers.

I teach Ubuntu classes for community members who have computers (but no Internet) in their homes. I'd like to be able to hand out cds for them to install choice programs on their home computers. 

I've tried APTonCD in many different ways over many months, and have had great difficulty building any metapackage that has all the dependancies their offline computers need, so I'd like to try something else.

I've been trying debshare also but have again been struggling to easily build metapackages for whole programs i.e.: tuxtype, tuxpaint, mp3 support, marble, etc. 

Does anybody have a suggestion to help me?

Thanks!

-Caroline
Peace Corps Volunteer 
Ghana, West Africa
ictwiki.org

---

### Post by mac9416 on 2010-02-01
Hey,

Installing packages at all on offline Ubuntu machines is still difficult, but it is especially hard to make offline installation one-click easy for less experienced users. Here are some options:
[SIZE=3]
1) Use APTOnCD[/SIZE]
[SIZE=2]Upsides:[/SIZE]

[LIST]
[*]APTOnCD creates a metapackage to install all software on the CD [SIZE=2]Downsides:[/SIZE]
[/LIST]
[SIZE=2]Downsides:[/SIZE]

[LIST]
[*]Installing single packages will require the command line or an  installation tool such as Synaptic - no double-click install
[/LIST]

[SIZE=3]2) Use a SuperDeb[/SIZE]
[SIZE=2] Upsides:[/SIZE]

[LIST]
[*]A package and all its dependencies can be installed with a simple double-click
[/LIST]
 [SIZE=2]Downsides:[/SIZE]

[LIST]
[*]Since each package bundles many dependencies, each SuperDeb will be very large
[*]I know of no actively-developed SuperDeb projects
[/LIST]
 [SIZE=2]Notes:[/SIZE]

[LIST]
[*][http://code.google.com/p/superdeb/](http://code.google.com/p/superdeb/)
[*][http://hacktolive.org/wiki/Super_Deb_FAQ](http://hacktolive.org/wiki/Super_Deb_FAQ)
[/LIST]
 
[SIZE=3] 3) Buy the repos on DVD[/SIZE]
[SIZE=2]Upsides:[/SIZE]

[LIST]
[*]You will have offline access to *all* software available from the repos
[*]Since the software on the DVDs is all FOSS, you *may* be able to copy and distribute the DVDs - please check on that for yourself though
[/LIST]
 [SIZE=2]Downsides:[/SIZE]

[LIST]
[*]Seven DVDs is a lot to hand someone to take home
[*]Everyone you give them to will need a DVD drive to install
[*]They are expensive
[/LIST]
 [SIZE=2]Notes:[/SIZE]

[LIST]
[*][http://www.osdisc.com/cgi-bin/view.cgi/products/dvd/ubuntu/repo.html](http://www.osdisc.com/cgi-bin/view.cgi/products/dvd/ubuntu/repo.html)
[/LIST]

I hope that helps. If I may make a shameless plug, the [Keryx Project]("http://keryxproject.org") is working hard to make installation on offline machines easier. Drop by our website often and check on our progress.  :)

Let me know if I can clarify anything. Thank you for all you do!
-mac

---

### Post by carolineictwiki on 2010-02-04
I've been using APTonCD, but this only pulls from your current package cache directory - I can't find a way to make it go out and get any dependencies that are not cached - so the CDs it makes are unreliable. I've spent the most time with this and have struggled to get it to build even a basic MP3 dependencies CD. Do I just need to re-install every program before I create the CD to make sure it's in my cache?

I'm off to try superdeb - thanks for the idea!

Repo DVDs look intriguing...not going to help me with the many dvd-drive less computers, but will save my own from long downloads! I'll get the 10.04 set when it comes out, I do believe. 

Keyrx looks great. I'm downloading it now! 

Thanks!
p.s. I wanted to compliment you on your exemplary clear written communication skills :) Both your forum response and your keryx tutorial were very easy to digest and understand! Owa dieh!

---

### Post by mac9416 on 2010-02-05
> Do I just need to re-install every program before I create the CD to make sure it's in my cache?

I'm afraid that would only re-download the top-level packages and not get the dependencies. 
The problem is that Ubuntu clears the package cache monthly. I would suggest putting a fresh Ubuntu installation on a second partition and installing packages there. Whenever you install a package, copy all the packages out of /var/cache/apt/archives/ to a flash drive. That will ensure none of the packages you need for the APTOnCD will be lost.

> p.s. I wanted to compliment you on your exemplary clear written communication skills Both your forum response and your keryx tutorial were very easy to digest and understand! Owa dieh!

Thanks for the compliment! The thanks for the tutorial, though, would go to [crashsystems]("http://crashsystems.net/"), who did a great job writing that up for us.

---

### Post by Bit Hacker on 2010-02-11
I followed the tutorial of keyrx but still the dependecy problem exits. Whats the point if it won't download the dependencies itself? In the end all it was, You have broken blablabla.... :(

---

### Post by mac9416 on 2010-02-11
Hello, Bit Hacker,

I am very sorry you are having trouble with Keryx. Could you quote the part of the tutorial you are having trouble with?

---

### Post by Bit Hacker on 2010-02-12
> **mac9416 said:**
> Hello, Bit Hacker,

I am very sorry you are having trouble with Keryx. Could you quote the part of the tutorial you are having trouble with?

Its not the tutorial, everything worked fine as far as the Gettting the packages was concerned. For example vlc was one of the things that I wanted to install on my friends machine, which ofcourse doesn't have the internet. I searched for vlc in keyrx and downloaded every highlighted result. Went to linux, ran the dpkg command but after sometime it returned the error of Not finding this, not finding that. Same was the problem with almost every package.

---

### Post by mac9416 on 2010-02-12
The installation method in the tutorial is admittedly janky. There is a fairly good chance something will go wrong and cause trouble. However, Keryx 0.92.4 (which will be released very soon) will have a GUI method for installing packages which will make things much easier.

Another problem is that dependency calculation in Keryx 0.92.x is somewhat lacking. For packages which have a lot of dependencies (such as VLC), there is a fairly good chance something will be missed and you will have to go back to the online machine to get it. This will not be a problem when 1.0 comes out (not in the near future).

If you are able to provide some details about your current situation, I will do what I can to help you get it sorted out. Otherwise, I hope you will stay tuned for the 0.92.4 release!

---

### Post by Bit Hacker on 2010-02-13
Thanks for the reply, I actually used the packages from aptoncd and used the dpkg command to installed all the packages and almost everything had one or more dependency problem. I'm lookin' forward to the next release, hope it would do some good.

---

