---
title: "Virtual Machine V Dual Boot"
date: 2011-04-28
forum: General Help
---

### Post by HostPost on 2011-04-28
This is blinking' ridiculous! I am titivating around and hesitating on what to do. I am setting about rebuilding a windows PC that was running XP Pro. As said in previous threads it was rendered useless by a virus.

I have already decided that Ubuntu will figure in this build in some form but I am having a headache working out if it should be a Virtual Machine with XP or set up a Dual Boot.

The new build will have a few identities on it for personal family and business use. I think (and would prefer) I can do without any Win stuff for the business and go 100% Linux, but the family will use some windows apps and a couple of games.

HELP!!
What do you recommend? What do you have? What do you use it for? Pros and Cons?

Any thoughts welcome.

Regards

---

### Post by thunderbirdje on 2011-04-28
It's a hard choice ;-)

You should consider the pro's and contra's: in a nutshell:

Virtual Machine:
+ You can switch fast between OS
+ You can easy run multiple Virtual Machines (if you need to)
- You have to share (set how much memory/processor/etc) will be used for each OS, so performances could be lower
- Sometimes people experience problems if you want to access a common share/network between your running OS and Virtual Machine (it all depends on your hardware, Virtual Machine software, etc) but keep in mind you can't share at all in Dual Boot due you have to reboot (although you can of course safe stuff to a share).

Dual Boot:
+ OS can use the full potential of your computer (no shared resources)
+ If you don't have to switch often (otherwise you will get irritated by waiting, waiting to switch).
- Not so easy to switch by a click


Hope you will have some more information now.

Good luck!

PS: I had Ubuntu and Windows for a long time on dual boot :-) Due for my work I have to use Windows specific software to teach. My laptop only has Ubuntu anymore (much faster) and is able to access the network shares with a glance :-)

---

### Post by colin.p on 2011-04-28
I was dual-booting lucid and 7, but very rarely ever booted into 7. Figured it was just plain silly to have the space for an entire OS to run 1 or 2 win programs on a very infrequent occasion. I then tried XP in VB and was pleasantly surprised at the speed of it. If I ever need win, I have it in VB or run a win program in wine, if so inclined.
If you have a reasonably recent machine, try a virtual environment for win.
Then, just maybe, you will find a native linux replacement for that 1 or 2 win programs and then ditch MS's cash-cow once and for all.

---

### Post by techunit on 2011-04-28
The windows apps will likely run in wine fine you should try that first. Good Luck. Dualbooting with XP is pretty easy to do actually just make sure to install XP first then Ubuntu later.

Guides are readily available from simple google search.

---

### Post by wizard10000 on 2011-04-28
I haven't had the need to dual boot in years.  If your hardware's beefy enough virtualization is the way to go IMO.

I do run Office 2007 under Crossover Office as I'm currently putting my resume out there and have had one unreadable resume created by LibreOffice - once I don't need to insure I'm 100% MS Office compatible I'll ditch Crossover Office  :)

---

### Post by thunderbirdje on 2011-04-28
Totally agree :-) 

I just boot into windows for Microsoft Office 2007 (because I need sometimes screenshot or I have to create a specific M$ Office exercise file for my students).

Ubuntu is fun, feels better, runs faster, the first days I discovered so nice features you just mis in M$ - for which you have to pay, install a 3th party program which doens't integrate that well and even slows down your computer more -... I just love it! :D

So Win7 is just when I want to work slow, haha :D LOL

Good luck!

---

### Post by Paddy Landau on 2011-04-28
I used to have that situation -- Linux for me and the family, and one computer with Windows for the occasional Windows program for the kids.

As kids can get viruses on Windows faster than you can say, "Damn, Windows crashed again!" I did the following.


[LIST]
[*]I set up Windows (dual boot) to perfection.
[*]I backed up the Windows partition using [CloneZilla]("http://www.clonezilla.org/").
[*]Thereafter, whenever the children got a virus, I restored the partition (it takes only a few minutes of my time), ran the Windows updates (boy, are they slow!), and let the kids on again.
[/LIST]

The kids were responsible for their own Windows backups. Nice and simple!

---

### Post by wilee-nilee on 2011-04-28
> **Paddy Landau said:**
> I used to have that situation -- Linux for me and the family, and one computer with Windows for the occasional Windows program for the kids.

As kids can get viruses on Windows faster than you can say, "Damn, Windows crashed again!" I did the following.


[LIST]
[*]I set up Windows (dual boot) to perfection.
[*]I backed up the Windows partition using [CloneZilla]("http://www.clonezilla.org/").
[*]Thereafter, whenever the children got a virus, I restored the partition (it takes only a few minutes of my time), ran the Windows updates (boy, are they slow!), and let the kids on again.
[/LIST]

The kids were responsible for their own Windows backups. Nice and simple!

Same here dual boot it and clone all partitions individually.

The Ubuntu will run chunky in a virtual, even if given a lot of memory, at least that has been my experience.

---

### Post by HostPost on 2011-04-28
Thanks everyone for the helpful responses. I have a dell dual core running 4GB RAM with a 500GB H/D and another 350GB hard drive available. I think that will be beefy enough.

I had looked into having the two drives running the two separate O/S's (as said on another thread) but this is a non starter.

Think I will go with the virtual box and see how that performs. If there is any significant performance issues I will ditch it.

regards

---

### Post by Hedgehog1 on 2011-04-28
Virtual Box has another advantage:  You can load lots of OSs for playing and testing, without partitioning you hard drive for each one:

[IMG]http://img219.imageshack.us/img219/455/vbox01.png[/IMG]


And you can jump between OSs really easy:

[IMG]http://img88.imageshack.us/img88/9595/vbox02.png[/IMG]


I find it hard to have only one OS on my work PC!

***The Hedge***

:KS

---

### Post by HostPost on 2011-04-29
Wow, thanks Hedge.

I've seen that OS flipping round effect before on my Macbook.

I take it you don't see any performance issues running VB.


Does anyone know if this is possible with running a VB: I will have two drive on my PC. Is it possible to have Ubuntu on one drive and allocate the space on the other drive to run a Virtual OS?

---

