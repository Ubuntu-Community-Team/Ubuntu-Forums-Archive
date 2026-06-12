---
title: "Insufficient space to download"
date: 2011-10-24
forum: General Help
---

### Post by Celticscorer on 2011-10-24
I have installed Ubuntu via Wubi and selected 15GiB to start off for my Ubuntu partition. I got all that goodness installed and I can get on Ubuntu and it works great. But now I want more of my hard disk memory dedicated to that partition. When i start up my computer I get to choose between Ubuntu and Windows. This whole partitioning idea is new to me so forgive me if I fail to use correct jargon.

I am executing an installer.exe with Wine Windows Program Downloader.  In this case it is WoW. When I get to the install screen it tells me that I have insufficient room to install the program.
[IMG]http://i53.tinypic.com/2cgzall.png[/IMG]

The thing is that I have around 250GiB of free memory on my hard disk. I have a section of 50GiB of unallocated space. After reading several forums, I felt I was on the right track, but now I can't seem to figure out how to use this unallocated memory; as far as I am concerned it is just sitting there now.

[IMG]http://i51.tinypic.com/maj8mq.png[/IMG]

What can I do now to make it so I can use that 50GiB on my Ubuntu partition? If you need any other details, just post and I'll get them on here as soon as I can.

Thanks

---

### Post by searchfgold6789 on 2011-10-24
That big partition in the middle is for Windows, which you have a Wubi installation on. That unallocated space is currently being unused. However, if you expand that fat middle partition to take up the remaining space, all it will do is increase the amount of hard disk space available to your Windows installation, not to Ubuntu.
I recommend using a dedicated partition, or just doing a full  installation. This makes partition management a *ton* easier :P
You can follow the guide [here]("http://ubuntuforums.org/showthread.php?t=1625371") to resize Wubi.
 - search

---

### Post by WorMzy on 2011-10-24
Let me get this right: you installed Ubuntu inside Windows, and now you want to install a game for Windows inside Ubuntu, which is inside Windows?

Well, good luck with that.

What I would say is: use Windows games on Windows. And if you're going to use Ubuntu, do it properly and install it to it's own partition. Wubi isn't designed to be used any anything more than a temporary solution to allow you to get acquainted with Ubuntu.

---

### Post by searchfgold6789 on 2011-10-24
> **WorMzy said:**
> 
What I would say is: use Windows games on Windows. And if you're going to use Ubuntu, do it properly and install it to it's own partition. Wubi isn't designed to be used any anything more than a temporary solution to allow you to get acquainted with Ubuntu.
Well, maybe he's just testing to see if the game will work, but +1 anyway.

---

### Post by Celticscorer on 2011-10-24
> **searchfgold6789 said:**
> 
I recommend using a dedicated partition, or just doing a full  installation. This makes partition management a *ton* easier :P
You can follow the guide [here]("http://ubuntuforums.org/showthread.php?t=1625371") to resize Wubi.
 - search

So instead of resizing Wubi, I should just make a separate partition just for Ubuntu. Everyone screams "Wubi" for people who are new to Ubuntu, so I figured it was the best method. In order to do this (full installation), is it logical to just 'delete' all my Ubuntu data and start from scratch?

---

### Post by Celticscorer on 2011-10-24
> **searchfgold6789 said:**
> Well, maybe he's just testing to see if the game will work, but +1 anyway.

Unfortunately no. I'm just a rat in a maze trying to find my cheese, the only sense of direction being what I want to do with Ubuntu, and no idea how to do it :p

---

### Post by WorMzy on 2011-10-24
> **Celticscorer said:**
> So instead of resizing Wubi, I should just make a separate partition just for Ubuntu. Everyone screams "Wubi" for people who are new to Ubuntu, so I figured it was the best method. In order to do this (full installation), is it logical to just 'delete' all my Ubuntu data and start from scratch?

You can do that, although I would back up any important documents you have in your home folder first; but you *can* move from a Wubi install to a partition install: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by Celticscorer on 2011-10-24
Thanks WorMzy, I'll give this a try tomorrow and let you know how it goes.

---

### Post by Celticscorer on 2011-10-25
I have no clue what I just did to my computer. All I know is that I now have a separate partition for Ubuntu, and plenty of space to install whatever my little heart desires. Kudos to you guys for having the patience to put up with the novice users like myself. :D

---

