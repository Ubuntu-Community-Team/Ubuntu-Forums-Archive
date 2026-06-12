---
title: "A few questions about wine"
date: 2011-07-20
forum: General Help
---

### Post by louisgonick on 2011-07-20
I am pretty new to ubuntu. And so far the transition has been pretty smooth, with a few issues on the way but generally good. I've heard alot about this app called wine that you can use to run windows apps on linux. Can somebody explain me how does it work? I plan to use it to run the apps that ubuntu lacks such as some games and microsoft office beacause libre office sucks. Will the performance be good? And also I have another question, When I installed ubuntu I gave it 35GB and for some reason each time I have less space left even though I have almost no files and I only have downloaded about 15 apps from the appstore. I remember when I first installed ubuntu I had used up only 3GB and now I have 9GB of used space. Is there anyway that I can re size the partition?

---

### Post by sectshun8 on 2011-07-20
Libre Office sucks?  I don't think so.  I use it just fine to edit MS Word/Excel/Powerpoint files for work when I travel with zero issues.

But back to wine.  I'm sure you've visited winehq.com?

From using it, it sort of emulates a Windows file sctructure on your unix machine.  It sets up basically a C:/Windows type thing... most programs go to C:/Program Files.  So it just mimics a Windows environment to get your programs working.

So basically to install something, you use the command wine, followed by the path to the setup.exe or whatever you have.

And then to run things, if you have no shortcut set up, you'd have to navigate to the program in the wine directory, which is /.wine, and do the command wine <program.exe> to run it and it works just like normal.

I use it primarily for Photoshop and a few games.

---

### Post by louisgonick on 2011-07-20
> **sectshun8 said:**
> Libre Office sucks?  I don't think so.  I use it just fine to edit MS Word/Excel/Powerpoint files for work when I travel with zero issues.

But back to wine.  I'm sure you've visited winehq.com?

From using it, it sort of emulates a Windows file sctructure on your unix machine.  It sets up basically a C:/Windows type thing... most programs go to C:/Program Files.  So it just mimics a Windows environment to get your programs working.

So basically to install something, you use the command wine, followed by the path to the setup.exe or whatever you have.

And then to run things, if you have no shortcut set up, you'd have to navigate to the program in the wine directory, which is /.wine, and do the command wine <program.exe> to run it and it works just like normal.

I use it primarily for Photoshop and a few games.

What I did not like about these open source office programs is that the interface looks very dated and it doesn't have the features that office 2010 has. Is the command wine thing some sort of command prompt?  And will the programs run as good as they do in windows or even better?

---

### Post by Mr. Shannon on 2011-07-20
Wine can be complicated to set up correctly, a simpler solution is to use Play On Linux (a front end to wine).  It will install "some" programs for you without a lot of effort.  Like for instance in Play On Linux you can click on MS Office and it will ask you to put your disk in and after that it is not more difficult to install MS Office on Linux than it is on Windows (if I remember right).  It will not activate through the internet though, so you will have to call Microsoft to get it activated.  Also, I was not able to get updates to work either.  There are also some games that Play On Linux can install as well.  NOTE: I don't have MS Office installed in Linux anymore.

My biggest problem with Libre Office is that it does not handle MS Word equations correctly.  Now if I could only get the people at college to use LaTeX.

> And will the programs run as good as they do in windows or even better?

No, no, no!  MS Office is buggy in Linux.  It's probably usable, at least some of it is, but buggy.

---

### Post by 3rdalbum on 2011-07-20
> **louisgonick said:**
> will the programs run as good as they do in windows or even better?

No. My estimate is that 20% of Windows programs work okay in Wine. Maybe another 10% will run with serious hacking around. Most don't work.

Use Wine as a last resort, basically.

---

### Post by louisgonick on 2011-07-20
> **Mr. Shannon said:**
> Wine can be complicated to set up correctly, a simpler solution is to use Play On Linux (a front end to wine).  It will install "some" programs for you without a lot of effort.  Like for instance in Play On Linux you can click on MS Office and it will ask you to put your disk in and after that it is not more difficult to install MS Office on Linux than it is on Windows (if I remember right).  It will not activate through the internet though, so you will have to call Microsoft to get it activated.  Also, I was not able to get updates to work either.  There are also some games that Play On Linux can install as well.  NOTE: I don't have MS Office installed in Linux anymore.

My biggest problem with Libre Office is that it does not handle MS Word equations correctly.  Now if I could only get the people at college to use LaTeX.



No, no, no!  MS Office is buggy in Linux.  It's probably usable, at least some of it is, but buggy.

hmmm... it sounds easier to just bare with windows on my laptop than to go through all these apps to just get buggy programs running..... Any idea of what may be going on with my hard drive? each time I have less space

---

### Post by CatKiller on 2011-07-20
> **louisgonick said:**
> I've heard alot about this app called wine that you can use to run windows apps on linux. Can somebody explain me how does it work?

It's an implementation of the Win32 API. It interprets program calls into something that will work on Linux.

> Will the performance be good?

It depends. The bits that have been implemented are the bits that people have got round to implementing. Popular applications get more attention because there's more motivation. Some problems are harder than others. You can see what the level of functionality is like for a particular application, and if there are any tweaks that help, at Wine's [AppDB]("http://appdb.winehq.org/").

A lot of programs run as well as they do in Windows. A few work better. Many run with some glitches. A great many don't run at all.

An equivalent native program will always be the better choice. For the applications where there is no alternative, Wine is worth a try. If Wine can't do it, there's always the virtualisation option. Anything's better than running Windows :)

---

