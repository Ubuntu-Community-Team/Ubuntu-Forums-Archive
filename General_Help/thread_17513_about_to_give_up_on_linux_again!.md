---
title: "about to give up on linux again!"
date: 2005-03-01
forum: General Help
---

### Post by red58 on 2005-03-01
spent all evening trying to install the 2 apps I find most useful - opera7 and arachnophilia5 - downloaded them, installed arach [I think] - can't figure out how to get it to run, opera install runs into one problem after another - had to get the libqt3c102-mt.deb and it doesn't wanna install the way everyone here seems to say it should - some error like needs options - I don't even know what the heck the thing is or why I need it, let alone how to make it part of a system that's pretty obtuse to start with!!

the problem w/ linux for me is I'm **not** here to learn computer programing and  management, but to use a computer as a tool to do a variety of other things, and I can accomplish those things quickly and easily w/ windows - install packages give me a progress report, ask me where to set themselves up and where to put their 'activating' link - within minutes of downloadng them, I can be using them - why does it have to be such a struggle in linux?

oh well ........... rant's over, I guess I'll go back to windows and get something done    like figure out how to recover my boot sector that I foolishly allowed grub to occupy - not as simple as telling windoze to reclaim it  :(  

I'll check back in here from opera for win!!

Bill

---

### Post by KLineD on 2005-03-01
It's really a shame but that's no reason to rant about or to give up. I'm sure that when you first learned about installing software on windows you had your struggles or someone told you how to do it and what all the options where. 

Installing apps in your ubuntu distro is really easy using the Synaptic Package Manager. I know Opera is not listed there (dont know about the other one) but there are other options, like firefox or mozilla, and if you really need opera I'm sure that if you posted an error log or something more useful you could get some help around here.

Linux is not that hard really and I can get all of my work done in here, I'm doing my thesis here in ubuntu, apart from that I browse the web, listen to music, rip and watch dvds, burn cd's and dvd's, play games designed for windows and have set up a FreeNX server so I can use my desktop from University. Ubuntu and Linux in general is great in my opinion.

And to help a little, to restore the NT boot manager, boot with the windows CD and go to the recovery console. From there type fixmbr and that's it.

---

### Post by Daniel G. Taylor on 2005-03-01
Point 1: Java is not free software
Point 2: Opera is not free software

What I am seeing is basically, "My inability to install and run two proprietary applications under GNU/Linux is frustrating. I just want to get work done! I have invested years in Microsoft Windows and know how everything works. It works much better for me because of this."

If people are not willing to change their behavior and learn new things they aren't going to enjoy trying a new, different system. My brother ran Opera 8 (beta) just a few days ago without any problems on Ubuntu. I've never heard of the other application you mentioned, so I can't comment about that. The point is that what you are trying to do is indeed possible.

Blame Sun for the Java issues.
Blame Opera for its proprietary software issues. (or maybe it has been packaged incorrectly for Ubuntu, I'm not sure).
In fact, I suggest you contact both companies and let them know exactly what brought you back to Windows, and that you would like to move to Linux but can't because of issues like these. All it takes is for the right person to hear things like this a few times.

Please, don't blame GNU/Linux.

---

### Post by jsgotangco on 2005-03-01
Have you tried installing Opera using the **static deb** file? I believe Opera is very dependent on QT that's why they have various packages available for every major ditro out in the market. For ubuntu, you can always use the static deb file. It should work without doing dependency checks.

Personally Opera looks way better in Windows than in Linux. That's why I only use Firefox  :-P

---

### Post by landotter on 2005-03-01
[QUOTE=Daniel G. Taylor]
Point 2: Opera is not free software
[/QUOTE]

No, but it's proprietary software done very nicely. ;)

I'm using the 8.0 beta for linux and it's stable beyond belief and very very purty. :P Try the "oxid" theme.

I used the "tar.gz" package from here: [http://www.opera.com/download/index.dml?platform=linux&ver=8.00b1](http://www.opera.com/download/index.dml?platform=linux&ver=8.00b1)

right click on it and unpack it, then open a terminal to install...

did you d/l it to the desktop?
then move to the desktop:

cd Desktop

then of course:

cd Operaxx

then 

ls

There should be a file called "install.sh" listed (or similar, I forget)

just run it as root to install Opera:

sudo ./install.sh

the "./" runs the program in the current folder.

The newest opera kicks butt btw, it's much more stable and the UI is much better than the 7.xx version. 

:)

---

### Post by red58 on 2005-03-01
jsgota - which is the **static**? was advised to use the 'unstable', and the other 3 choices are Sarge, Woody and Potato - I tried firefox on win for a couple weeks and couldn't stay w/ it cuz to me it's a warmed over MSIE compared to the functionality of Opera - I do use Thunderbird

Danial - java is indeed [free software](http://java.com:80/en/download/help/5000010500.xml#download) nowadays, and it's included w/ many apps - arachnophilia is a great free HTML editor that has been written in java to be cross platform, and I find it immensely better than the usual windows HTML apps

additionally I have spent a lot of time trying to setup a linux install, having tried a couple distros in the past 3 years, including 'proprietary' ones, now hoping ubuntu may be the one that works for the 'ordinary' desktop user - I've installed it twice now, and in the process learned there's something amiss in the 'updates' I let it get and install the 1st time, as it didn't function that time - have also used it from the live cd to check it out, and I **do** like it, but linux is the problem here, not the apps written to run on it - I was attracted because it includes OpenOffice [which I also use on XP], Firefox and T-bird, and Opera and Arch are ported to it - my problem is the runaround to try to find anything and install things - it **is** still a collection of stuff written by 'individualists', gathered and packaged by a committee!

what's the way to get the Syn Pkg Mgr to find and install things? I don't find using a console w/ a number of different cmnds at all intuitive when I have no idea where the files I want are, or what cmnd is needed to do something to them - sure I'm comfortable w/ XP - click on an executable file and it executes! if that means start the 'installshield wizard' that's what it does!

I haven't given up on ubuntu, just thinkin I might have to - back in XP-Opera now, and **have** reclaimed the MBR [ followed too many suggestions from here before maybe] and while I was in ubuntu I figured out how to find the grub menu.lst [once I figgured out that was "l"st not "1"st - old eyes don't help w/ cmnd line stuff] and figured out how to change it to boot XP default instead of ubuntu, and I found w/ firefox files to make a boot disk to dispense w/ grub, but had to actually make it in XP, as I **couldn't** make ubuntu write the floppy

so when I have the patience to try again, and a few hours to spare, I'll go thru trying to make the apps install again, tho' there may be a mess in there already from the first try - I had planned on re-installing once I got everything sorted out, as I've done w/XP

sorry for the rant and the long post here, just very frustrated, but appreciate the help!

Bill

---

### Post by jsgotangco on 2005-03-01
When you go to the download page, you're give a list of distros - but Ubuntu is not there, so you can choose "Other/Static DEB". This is similar to a windows app that does not need to be "installed" to run - but the DEB still needs to be installed btw, but it won't have depency errors. What you encoutered in your first install is a dependency check - you lack the files that Opera needs (which is QT I guess). A Static DEB contains what you need to run it. It may not look as flashy as a native QT app but that's the sacrifice. I installed *opera-static_8.0-20050104.1-qt_en_i386.deb* after your first post to test it out. You might want to try it again.

---

