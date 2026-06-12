---
title: "Eager to make the final switch - help me do it"
date: 2006-06-21
forum: General Help
---

### Post by Michael%S on 2006-06-21
Ubuntu has been my primary OS (dualboot with WinXPPro since February) for about a month and a half now, and although I was pretty much convinced I can do without Big Ball of Mud Microsoft products after a couple of days of it, I was far far too busy with tests to even consider starting to make the final leap and get rid of Windows for good. Now I'm very close to a span of very flexible time and one of my top priorities is to sort out my computing. There are a few dilemmas and questions that stand in my way towards Ubuntu freedom, and I'd like to sort these through with some advice from more experienced users as soon as possible and decide what I'm doing with my machine.
First I should mention what I currently still need WinXP for: games (which I hardly had the time for so far), managing my very large collection of meticulously cataloged digital music [on an NTFS partition], and I suppose possibly for MS Office for compatability (hasn't come up so far but it may well do).
For the games the answer is obviously Cedega which I am glad to pay for and will probably sign up for soon enough.
For the music collection I would assume simply replacing the NTFS partition with the Ubuntu-installed filesystem will do the trick.
What remains is MS Office which leads me to the issue of VMWare - I still haven't understood if it allows me to legally and costlessly do the few remaining tasks I really need MS software for. If it does, how?
The final question is if it's advisable to keep a living WinXP boot even after all my data is moved onto the Linux partition.
Basically what I'm getting at is I want general advice before making the switch, with some focus on the issues I mentioned (which as you may notice are all rather mild and not incredibly problematic.) Is there anything I should know before backing up all my data temporarily and then starting afresh, formatting my HD and installing Dapper anew?

---

### Post by Mirrorball on 2006-06-21
You can run MS Office on wine, but you can just use OpenOffice.org. It opens most Office documents with no problems and exports its documents to MS Office format. You won't have any problems with your music.

---

### Post by th3james on 2006-06-21
Best thing to do is to spilt the hard drive into 2 equal sized partions, depending on avaliable space, Install Ubuntu onto the new partition, and then copy all the your music onto the ubuntu partition. However, if you don't have the space, you can just read the music from the windows partition, although you won't be able to edit it (which is why i recommend copying if possible).

Do you know for a fact that you need office? I find open office meets my needs fine, the only real problem is that its a abit dodgy with spreadsheet macros. If i have any problems converting to .doc, i just use PDF, which (in my eyes) looks nicer. 

I must admit, I don't know that much about VMWare, my understanding is, it allows you to run windows inside of linux. I hung onto my windows partiton, just in case, although i never use it

---

### Post by Michael%S on 2006-06-21
I sometimes have to work with very complicated MSO documents, like ones including huge complex tables, or ones with a whole complicated systems of styles and a long table of contents, and all of this often in Hebrew which isn't handled in OO.o as well as in MSO.

And Mirrorball, can you explain to me a little how to use Wine? I installed it once and never got around to really using it. What should I know about it?
I know Cedega is based on it. When I get it, will it be able to somehow replace Wine, or is it solely game-oriented?

---

### Post by matrooswolf on 2006-06-21
vmware here:
[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

I have a large music collection on a ntfs partition (70GB).  I use Amarok, and it just works fine.
[http://kubuntu.org/announcements/amarok-1.4.php](http://kubuntu.org/announcements/amarok-1.4.php)

I don't use Office anymore, once you get used to it, OpenOffice is just as good, if not better in some points (but I don't know about OpenOffice Base)

I still have dual boot, you never know when something gets broken in Ubuntu, and it is nice to have access through Windows to the internet to find the necessary answers (once I had Grub problems, another time X didn't start ...).  So I still keep it...

Have fun!

---

### Post by thasheep on 2006-06-21
For spreadsheets, I much prefer gnumeric to openoffice. It's faster, smarter and handles other formats (including graphs in xls) better.

---

### Post by Mirrorball on 2006-06-21
[QUOTE=Michael%S]I sometimes have to work with very complicated MSO documents, like ones including huge complex tables, or ones with a whole complicated systems of styles and a long table of contents, and all of this often in Hebrew which isn't handled in OO.o as well as in MSO.

And Mirrorball, can you explain to me a little how to use Wine? I installed it once and never got around to really using it. What should I know about it?
I know Cedega is based on it. When I get it, will it be able to somehow replace Wine, or is it solely game-oriented?[/QUOTE]
About wine: first you open a terminal and run winecfg. Then cd to the directory where your Office CD is mounted (probably /media/cdrom) and run 'wine SETUP.EXE'. Everything you install will be inside the .wine directory in your home directory.

Have a look at [WineTools]("http://www.von-thadden.de/Joachim/WineTools/") too. It makes configuring Wine a lot easier.

---

### Post by Jott on 2006-06-21
Howdy.  

I find open office adequate for about 90% of what I do, but it does fall down for some more complex tasks - especially when it's stuff that has to work and look the same in MS office.  I'd recomend spending the $40 to get crossover office, which is kind of like a special version of wine that's tailored to work well with MS productivity software.  If you use vmware, I think you end up having to run the whole windows ms inside your linux os just to run office, which seems resource intensive.

I originally set up three partitions on my drive - one ntfs for windows, one ext3 for linux, and one vfat that they could share.  I kept my music and other data on the vfat - the idea being that both os's could read and write to it without problems.  It works fine, but I find that I bassically never ever boot into windows anymore, so it's kinda useless.  In retrospect, I would have shrunk the windows partition down to the absolute minimum size I thought I might need, used the rest for ubuntu, and kept all my data on the ubuntu side.  

I like to keep the windows, just in case I need it for something or want to play a game that's only available in windows; and I've got plenty of drive space.  Also, it lets me rationalize installing all the restricted codecs (w32, mp3, etc) in ubuntu - I got a liscense for all of them with windows, so it should be legal, right?

Anyway, that's my $0.02.

---

### Post by DirtyJay on 2006-06-21
Micheal%S,
If your at all technically inclined, this is what I would do.
Purchase a new hard drive.  Pull your existing hard drive, bag it, tag it and pick it up!  Install new hard drive and install Ubuntu as the only operating system.  Then if you every have any real problems, and need Windoze in a pinch, you reinstall your old hard drive and your back in action.  I have experienced some problems with dual boot systems and unless you are prepared work through them, I would suggest not installing 2 systems on same machine.  I started a thread on how I run my computer with Windoze and Ubuntu without using a traditional dual boot.  Check it out.  If your interest is peaked let me know and I'll help you set it up.

[http://www.ubuntuforums.org/showthread.php?t=195532]("http://www.ubuntuforums.org/showthread.php?t=195532")

---

### Post by eth on 2006-06-21
[QUOTE=Michael%S]I sometimes have to work with very complicated MSO documents, like ones including huge complex tables, or ones with a whole complicated systems of styles and a long table of contents, and all of this often in Hebrew which isn't handled in OO.o as well as in MSO.[/QUOTE]

**LaTeX** and **Kile** will just make MSO looking terribly silly, annoying, and poorly professional.

---

### Post by Fred Doolie on 2006-06-21
[QUOTE=Michael%S]I still haven't understood if it allows me to legally and costlessly do the few remaining tasks I really need MS software for. If it does, how?[/QUOTE]

VMWare creates virtual isolated computers inside seperate windows.  You can do whatever you want with them as if they were actual computers in your house. Make one, install Windows on it and there you go. A Windows system that you can run Windows software. Make another and install Slackware. Make another and install PuppyOS. They are all seperate "computers"* You can even network them together into a home network.

How "legally"? It's just an empty simulated computer. The legality of it lies in what OS you install. You have a legal copy of Windows and legal copies of your software, don't you? It's legally your system then. 

Uh, wait. I see your point. If you want to remain 100% legit you'll either have to pay Microsoft $100 for the privilige of installing another copy of Windows in your house or wipe out your existing installation**. You are only allowed to have one installation at a time or the MS lawers will kidnap your children and sell them as slaves***.

How "costlessly"? I don't know. Right now VMWare Server is free. Maybe after people get hooked on it the free version will time out and you have to pay $80,000 for your "VMWare fix" <grin>
-----------------------

* But they run rather slowly. You can only have like two running at the same time and still get something done. Also the graphic card and sound card are garbage. Forget games and DX9 stuff. For business software it should be fine though. 

** Right after the monkeys fly out of your bum, right?

***  They would give you 24 hours to pay the $100. Also you would get anything over the $100+kidnapping fees+legal fees+sales tax+local tax+state tax+carpet tack+tic tacs if the kids brought that much. Otherwise you would owe the balance.

---

