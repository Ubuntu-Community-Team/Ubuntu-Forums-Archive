---
title: "I'd like to understand why is ubuntu made so that it needs a lot of knowledge to use?"
date: 2009-11-28
forum: General Help
---

### Post by Guitar-maniac on 2009-11-28
I have used ubuntu now about 4 months, have ran into a problem after solving some other problem. We tried this on our gf computer cause her windows broke down, but couldn't get the wireless connections working, no matter what we tried.
My sound is messed, i have tried countless of online guides, installed the system again couple times. had many problems with video playback. and after installing the codes on many guides, still have the blue pixel problem when downloading clips from youtube for example.
I work as a guitar instructor besides my studies, and i transcribe songs, but its a mess. i have to shutdown songbird to hear tuxguitar and vice versa.
Ipod wont work after trying the guides, trying it with banshee and gtkpod.

So could anyone tell me why ubuntu is made to be this way?  is there some reason that it can't be made easy to use? Three of my friends are tired with the problems on their windows and wuold like to try ubuntu, but i cant really recommend this tho i would love to.

It's just getting frustrating since u have to study commands and get to really know computer terms and stuff just to add songs to your player. or have to turn off other softwares to hear sounds from the other. and then put it back up again after turning of the other.

---

### Post by tgalati4 on 2009-11-28
All of your concerns are valid.  Ubuntu is easier than GNU/Linux used to be.  It still has problems, but it is getting better.  Normally most people buy a computer with an operating system on it that just works.  When trying to install Ubuntu on a computer that had Windows on it, you will encounter some problems.

To fix those problems, one is required to have some (or alot) of computer knowledge, and the ability to search and read the forums.
Most of these problems are fixable, but they require some patience and some time.

The fact that you were able to install Ubuntu and write about your concerns in this forum is evidence that you can do it.  Keep at it and you will eventually find a workable solution for all of these problems.

Regarding the sound issues, Ubuntu has several sound frameworks:  OSS (Open Sound System--older but still used), ALSA (Advanced Linux Sound Architecture), pulseaudio (a sound server that mixes at a system level--so you can control your system sounds vs music player sound levels).

Tuxplayer is probably using one sound framework and Songbird is using another.  Try to research what framework each is using and then write a script to work around it.

For instance, if tuxplayer uses OSS, then you might need to use a helper application to fake ALSA (aoss).

apt-cache search aoss

Something like:

A file called mytuxplayer.sh:

#/bin/sh
# Cheesy script to allow tuxplayer and SongBird to play together

aoss tuxplayer


------------------------

It helps to study some of the history as to how Ubuntu came to be.  It is based on Debian GNU/Linux which has a long history.  This history includes development of graphic and sound frameworks--with each application using whatever framework was popular at the time of programming--can cause difficulty for the new user.  After 4 years of using Ubuntu, you will be more comfortable.

How many years have you used Windows?  How many using Ubuntu?

---

### Post by GregBrannon on 2009-11-28
My experience has been that Ubuntu is made to be as useful as it can be to the largest number of people using the greatest number of hardware configurations possible that can be tested within a reasonable time.  (More testers on more platforms submitting more bug reports presumably will make it even better.)  It's certainly not purposely constructed to be difficult or only for the techno-elite.  When there are problems, my experience with this forum is that complete strangers will bust their butts to help people who provide good info and ask pointed questions.

Since your interests seem to focus on music and video, have you looked at the Ubuntu Studio distro?  Perhaps the focus that package has on those specific areas will provide a distro that better meets your needs.  I learned of it only recently and haven't tried it so can't say.  But I have installed 8.04, Jaunty, and Karmic on 3 different x86 hardware configurations and have had success each time.  Yes, there have been adjustments, and I've learned something each time and continue to learn long afterwards, but the results of my efforts is that computing is fun again.  The freedom Linux offers stimulates innovation and learning.

Don't give up.  Search for and network with others doing and trying to do what you want to do.  I think the results of your search will provide you with the freedom to use tools that will allow you to discover and explore new territories.

Now start a new thread - or several - with titles that describe specific problems you're having.  Then, in the body of the message, provide as much info as you can, describing the problems, error messages, which distro, Gnome/KDM/Other, hardware used, etc.  Good luck.

---

### Post by QLee on 2009-11-28
[QUOTE=Guitar-maniac]
So could anyone tell me why ubuntu is made to be this way?  is there some reason that it can't be made easy to use? Three of my friends are tired with the problems on their windows and wuold like to try ubuntu, but i cant really recommend this tho i would love to.

It's just getting frustrating since u have to study commands and get to really know computer terms and stuff just to add songs to your player. or have to turn off other softwares to hear sounds from the other. and then put it back up again after turning of the other.[/QUOTE]

The simple answer to this is that most people buy computers that Windows already installed and the professionals who determined how it should be configured did so before you received the unit and only put it on a system with known, working hardware.

With Ubuntu, you (a non-professional) installed the system and you didn't yet understand anything about how to configure things for the hardware you have. If a professional, knowledgeable person set up and gave you a working system, you'd be fine.

Often, people start with a working Windows system and through lack of knowledge allow it to get to a point where it doesn't work and then they are in the same situation as you describe for you and Ubuntu. Try to install Windows with a CD on a Dell without the dell drivers for the hardware, you'd probably have trouble with that too, most people do.

I agree and understand it is frustrating when you start learning about a new operating system, but think what you have already learned, it keeps getting easier as your understanding grows. And people here are willing to help you succeed.

Remember, you see problems here, most of the people who installed with no problems, are doing something else, not posting here for help. Be happy that some of them are here trying to help you.

---

### Post by blueridgedog on 2009-11-28
> **Guitar-maniac said:**
> 
It's just getting frustrating since u have to study commands and get to really know computer terms and stuff just to add songs to your player. or have to turn off other softwares to hear sounds from the other. and then put it back up again after turning of the other.

There are many hands at work making Linux and no single point of authority.  One large group of people have developed the core kernel, many, many others have developed drivers (with or without help from the hardware manufactures), others still have worked on the graphical interface and other individuals have written the applications you are using.  Almost all of them are volunteers in the sense that they do it for the love of it.

"Distributions" of Linux like Ubuntu (there are many more) attempt to work out the conflicts in the independent products and present a more unified or monolithic product.  It works in most cases, but it is still just a collection of parts.  

In the end, there is no way to guarantee it will work for every user under every circumstance or that any program you download will install and run without errors or conflicts.  The same freedom that allows you to install and run what you want, to be free of DRM issues in your OS, to have no limits to your use, also requires that you are the chief trouble shooter and the chief support person.  There are resources and people (this list is a great one, as are individual lists for the applications you mention) and there are local Linux users groups that can give you one on one help, but ultimately you have to bring a spirit of wanting to be a problem solver to the table.  The act of installing Ubuntu and then coming here for help is proof that you can make it work.

Start by dealing with one problem at a time.  Post a thread looking for help and work through that one problem.  Be patient.  You may need to post it in different forum, or ask it a different way.  As your knowledge grows, you will be able to ask questions in a better more informative way and you will get help more targeted to your issues.  After a year or two of that you will find that you have learned a great deal and you love Linux because what you have learned has allowed you to use your computer for your purposes and in a way that suits your needs.  

You may also find yourself helping others who come to the OS after you and are struck with that initial sense of overwhelming complexity. 

Don't give up!

---

### Post by sgosnell on 2009-11-28
Ubuntu doesn't really require any more knowledge than Windows, maybe less, but most people already have years of Windows use, so they know how to do things because they've done them for a long time already.  Ubuntu is not Windows, and does some things differently, requiring users to relearn how to do those things.  If you let users who have never seen a computer to start using them, one group with Windows and one group with Ubuntu, I predict that the Ubuntu group will learn more quickly than the Windows group, at least for making system changes.  I'm not sure how you could do that experiment, though.

---

