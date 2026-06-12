---
title: "how to learn linux"
date: 2006-04-02
forum: General Help
---

### Post by acorrigan on 2006-04-02
How do I found out how ubuntu linux works in general?  Unless something just works in synaptic  the only other chance I have of getting it to work is a howto.  I'd like to know: is there a book I can get so that I'm not so clueless in general regarding doing nontrivial things?  I found on amazon* Beginning Ubuntu Linux: From Novice to Professional*  but I'm not sure if it will teach me more advanced things like installing drivers or how to create packages when one isn't available.  Does anyone have any book recommendations?   If not, how have other people taught themselves such things?   

Thanks

....

edited for conciseness, i was ranting.

---

### Post by zapcojake on 2006-04-02
here's a hint on question 2.  there is a text file which can be modified to show only the kernels you want to boot.   I have been playing with kernels and have a similar situation.  Also, this is a great place to start learning sometimes you pick stuff up by accident while looking for something else.   Use the search bar in the forums and use the wiki.  They will help.  i have been tinkering with Linux for 4 years now and this is far and away the best place to learn and get help.

---

### Post by acorrigan on 2006-04-02
thanks!

---

### Post by Andrew-buntu on 2006-04-02
How Linux Works by Brian Ward is a great book.  I check that one for a lot of basic stuff - it's not quite "for Dummies" but it's not overly complex, either.
Linux in a Nutshell is a huge book that basically contains the man pages for the most important programs you'd use in Linux - everything from mount to vi.

---

### Post by nanotube on 2006-04-02
[QUOTE=acorrigan]How do I found out how ubuntu linux works in general? the following are a bunch of random things that have confused me.  I'm *not* asking for specific answers to any of these.  Rather I'd like to know if there a book I can get so that I'm not so clueless in general.   I found on amazon* Beginning Ubuntu Linux: From Novice to Professional*  but I'm not sure if it will teach me how to figure out problems similar to the following.   There were other, unreleased books which sounded like they might be helpful , but I'm not sure and they're not released anyway
[/QUOte]
Well, dont know whether this is what you would be looking for, but this link [http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz) is a great free ebook about the linux os, in general. might want to check it out.

> Anyway the things that I've been confused about:

the first set is related to modules, firmware, and how these things relate to updating my kernel in synaptic.
1. Synaptic tells me to update my kernel, but I'm scared to because I don't want to have to reinstall my ivtv or nvidia drivers.  Will it break them this time?  How do I know when it will or won't?  I know it has in the past and I think that I had to go through the nvidia driver howto tutorial again.
dont know much about modules and kernel upgrades, so will leave it for someone else to tackle.

> 2. I have like a screen full of different kernels to load from grub.  How do I get rid of all but the one I use.  Not just from the menu,  but I don't want kernels installed that I don't use.  also I remember one time it got rid of my entry for windows,  why did it do that?

To edit the grub menu, edit the file /boot/grub/menu.lst
that lists all your boot options. the reason you have so many kernels is that when you upgrade to a new kernel, the old one stays in the list (just so you can boot to it if the new upgraded kernel screws something up). to be on the safe side, you might want to leave at least the next oldest kernel in the menu, but it is safe to delete all the others. you can get more info about grub through some well-chosen google querying (eg, "grub howto" or "grub tutorial" will net you some good ones).

> 3. When I install drivers I hear about firmware and I kind of understand what it is, but have no clue how it works in linux and what effect it might have on my hardware in particular cases .  recently I asked on the forum whether or not a printer firmware will affect the printer in windows, i was told it won't, but how can i find this out myself?

dont know the specifics, but google is your friend. that is a "general rule". :)

> 4. I've installed ivtv according to dhyam's very helpful guide I have no clue how to maintain my ivtv drivers, either upgrading or removing them properly since it wasn't done through synaptic

dont know anything about ivtv, so leave this for others.

> about packages:
1. how do I know when packages will be updated?  Ubuntu overall seems to contain very out of date packages  (like firefox, 1.0.7?  I've had 1.5 in windows for a long time)  and I have no clue when it's decided to finally update them.   I remember in gentoo, which I used to use two years ago, everything was constantly updated. Lyx was also updated recently.  They have 32-bit packages on their website for ubuntu.  why aren't they in the repos?  how do i know when an amd64 package will be available.  then again the repos still only have 1.3.6, and 1.3.7 is now not even current, I guess 1.4.0 won't be available for even longer?

ubuntu generally sticks with whatever packages were out at the time of a release, and only does upgrades for security issues. if you want newer stuff, just install from outside the repositories. using program "checkinstall" instead of the usual "make install", it will create a .deb file for you, and essentially be uninstallable and visible through synaptic. very nice. :)

> 2. how do I create basic packages myself?  that would've came in handy when the official vlc was really ugly and i had an old version installed (synaptic wouldn't shut up about it) or now when lyx is very out of date or since AMD ACML is not available at all or glew is very out of date or glewpy isnt available at all and numpy and scipy are very out of date.
  I tried looking at [http://www.debian.org/doc/manuals/maint-guide/index.en.html](http://www.debian.org/doc/manuals/maint-guide/index.en.html)
But it says: "program should result in binary executable form, libraries are harder to handle." which means it doesn't apply to most of these cases.   also that long-winded guide seems way more complicated than necessary to update libraries which I don't care if they've got all their dependencies right - if it doesn't work I'll just remove them. is it really necessary to set up a separate build environment since I don't plan on distributing the packages and therefore as long as they work for me that's good enough or make sure I don't break something since they are not dependencies of anything.

as a nice "side effect", checkinstall, which i mentioned above, actually creates a .deb package, which you can then use/reuse later if you care to. so that is one easy way to create ubuntu debs from sources. if there are rpms available, you can use package called "alien" to convert the rpm to an ubuntu deb.

> 3. since I don't know how to create packages I have stuff in /usr/local/lib like AMD acml and glew   I constantly have to export LD_LIBRARY_PATH=/usr/local/lib to run code which use those libraries.  How do I make a system wide change so that ubuntu knows to look there too?  Also why isn't /usr/lib on there  yet it can find libraries /usr/lib?

to set the path for your user, add the path setting and path exporting command to your ~/.bashrc file. to do in on a systemwide level, put the same thing into /etc/bash.bashrc file. this is one of the things that are "general linux things", that you will learn if you read the rute linux ebook that i linked you to before.

> I guess in general it's really annoying that to do anything I need to browse a forum to find a step-by-step guide to tell me what to do instead of just figuring it out on my own.  or waste other people's time by asking questions

well, after looking around the forums a few times, you will find that you dont have to anymore. for any operating system (including windows), there is a learning curve you have to go through. :)

---

### Post by Velvet Elvis on 2006-04-02
Ubuntu is probably not the best distribution to use if you really want to learn how things work under the hood.  In order to make things as smooth and user friendly as possible on the desktop a lot of complexity has been added that doesn't need to be there if you are willing to manually administer your system.  If you really want to learn how stuff works you'd be best off duel booting with something like slackware that does not hold your hand.

The problem with ubuntu is also its greatest strength.  It's based on debian.  Debian has its own very powerful and very capable tools for doing just about anything you'll ever need to do, but they are different from how you'd do them on other systems.  If you make a lot of your own packages and stuff like that you can break these tools so they become useless.  IMHO, if you're using a debian based system it's best to only use packages from official mirrors if at all possible.  They may not be the most up to date but they should "just work."  While sometimes arcane, the documentation in /usr/share/doc is all you need to get packages working most of the time.  The README.debian files should tell you most of what you need.

If you want to learn the guts of ubuntu, the best place to start is with the debian documentation which can be pretty cryptic in places.  Check [www.debian.org](www.debian.org).  I'd say 95% of what is there is aplicable to ubuntu as well.

I think apress has a ubuntu book coming out that is in the beginner to pro series, the same as the one you are talking about.  That should cover a lot of the debian specific stuff as well.

If you don't mind putting in some time and reading, the best way to go, IMHO, is to start out with slackware and the O'Reilly book *Running Linux*.  The nice thing about slackware is that it's very plain.  There are not a lot of distribution specific tools.  Whatever you learn in slackware you can carry with you to pretty much any other UNIX flavor out there.  With redhat and debain based distros it's real easy to just learn how to use redhat or just learn how to use debain without really getting into the guts of it.

The fact that slackware uses unmodified kernal source from kernal.org makes it easier to manually configure and compile your own kernel specifically for your hardware.  Once you've figured out what the stuff in the kernel does, most other stuff sorta falls into place.  You don't have to ever look at any code or understand how it does what it does to do this, you just have to know what it does.  Configuration is done with a series of graphical menues, albeit a fairly long ones.  Contextual documentation is there to use as you go.  If you want to figure out how to tweak your system for speed and have just the drivers you need and none of the ones you don't, this is the way to do it.   Because of all the bells and whistles that make Ubuntu so nice and slick, it's easy to break if you do a lot of mucking around without totally understanding what you're doing.  With slackware it's real hard to screw it up so bad you can't fix it. 

Anyway, I started out duel booting slackware and windows.  Duel booting Ubuntu and Slackware would be the same idea.  For the first couple months I was in totally over my head.  It tooks weeks just to get X up with full ATI support. After a year I was able to comfortably find my way around any linux or unix system out there, on a server or on a desktop.

I'm using kubuntu now because I'm lazy and it makes it so damn easy to get stuff done.  On the rare occaisions when somthing does break I always know how to fix it or can figure it out withou too much hassle though.

---

### Post by acorrigan on 2006-04-02
that's all great advice regarding. thanks so much!

also, checkinstall is amazing!  thank you!

---

### Post by Zeroangel on 2006-04-02
These forums are also an excellent resource for learning linux. For example, if you have a question, chances are someone already asked it and somone has answered. Sometimes I even read a question and think to myself 'what would I do in this case?' then later on compare my answer to one which has solve the question to learn more about my thought processes.

I also learn additional stuff by using intuition to answer questions, since if I am wrong then someone with a better answer will usually correct me. They say that if someone wants to truly learn something, a good way to do it is to teach it.

---

