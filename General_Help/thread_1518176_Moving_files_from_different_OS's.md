---
title: "Moving files from different OS's"
date: 2010-06-26
forum: General Help
---

### Post by DGPoulton on 2010-06-26
ok i finally made up my mind, im switching. Vista is......yeah nothing needs to be said. Anyways i only have a few things preventing me from switching, biggest is Ubuntu is currently partinioned on 10gigs of my hard drive, the rest is mostly crap. All i want off vista is music, pictures, and a few videos. how do i get them onto the ubuntu side, or allocate more space to use a friends external harddrive. I know Wine is used for WoW(problem solved) but how about ventillo and the rarely played EvE online? also if possible i need to bring those over as well. other than than Ubuntu kicks the **** out of any windows or mac OS ive ever used. but thats not sayin a whole lot. thanks for reading and any help you guys can give me :D

---

### Post by warfacegod on 2010-06-26
If you have an external available to you then I suggest using it. Get all of the data that you want onto. ***Be absolutely certain you get it all.*** And make sure you have a working LiveCD of Ubuntu.

Once you've done that. Repartition the Windows space as ext4. Use Gparted for that.

```
sudo apt-get install gparted
```

You will probably need to reinstall GRUB2 at this point. Section #13 here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

This guide will help you use the newly created ext4 partition as your Home folder: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Once you've done this, you can put all of your data into your home partition and continue enjoying Ubuntu.

---

### Post by DGPoulton on 2010-06-26
for the music anf other stuff that seems fine to just throw it on the harddrive, but if i transfer the Games, WoW and EvE, wont they have a problem playing or even knowing how to play since they were installed on windows? and i understand that after i get everything i am basically going to format that part of my harddrive, really its nothing but crap from the last 4 years thats just slowing my computer down

Update: ok well he says he sold it a few days back so im boned there, been looking for online storage sites

---

### Post by warfacegod on 2010-06-26
Okay, how about a different approach? Clean up Windows so that you can still use it for games. Wine can be a poor substitute for running an app in it's native environment.

Defraggler, Ccleaner, and Glary Utilities are excellent tools for Windows. I would also go through the whole Spyware/Virus scanning thing.

When your done cleaning up, use an Ubuntu LiveCD to have Gparted shrink your XP partition smaller. Lot's smaller. You can then use the remaining space for a small partition for Ubuntu say 10 GB and the rest for your /home.

---

### Post by DGPoulton on 2010-06-26
hmm, i coud leave WoW, EvE, and ventrillo all on windows, and just transfer everything else. i really want to make ubuntu my main OS, if the only OS on my laptop

---

### Post by warfacegod on 2010-06-26
Here's the WineHQ apps list. See if your games are in the list and how well they are supported. [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by DGPoulton on 2010-06-26
yea, since what i do in WoW is to intesive for Wine to run, i guess im just gonna play it on Vista. im gonna go clean up vista then try and transfer the files i need

---

### Post by warfacegod on 2010-06-26
That's what I figured would happen with the games. Post back if you need help otherwise you can mark this thread as Solved under Thread Tools. Although it might be best to hold off until you've got everything running properly.

---

### Post by DGPoulton on 2010-06-28
Ok, I actually spent yesterday using teamviewer to transfer my more important files to my desktop. But this morning I was able to access my Vista files while on Ubuntu, now it was just a shortcut but there must be a way to do a direct transfer. For example my 12gig music files instead of being moved around to a other computer then back, just moved on my harddrive. Also I tried using gparted to partition more harddrive space with little knowledge of how to do it. Are there any guide? Btw thanks so much for your help

---

### Post by warfacegod on 2010-06-28
Could you post a screenshot of Gparted with it's window maximized?

---

### Post by nothingspecial on 2010-06-28
You should backup all your stuff to external media any way. Believe me, I learnt the hard (and expensive way).

Especially if you are going to start messing about with gparted.

---

### Post by WorMzy on 2010-06-28
Just mount your Vista partition while inside Ubuntu. You can easily mount other partitions while using nautilus (file browser). For example, here is a nautilus window from my Arch setup:
[[img]http://www.ubuntu-pics.de/thumb/91444/wormzy_____file_browser_002_K2ajRH.png[/img]](http://www.ubuntu-pics.de/bild/91444/wormzy_____file_browser_002_K2ajRH.png)
As you can see down the left-hand side there's a sidebar with a list of other partitions available on my hard disks. Windows partitions are usually listed like the one my cursor is hovering over in the screenshot (*43 GB Filesystem*). Simply click it, then enter your password, and it'll be mounted. From there it's a simple matter of dragging and dropping any files you want to transfer over.

---

### Post by warfacegod on 2010-06-28
> **WorMzy said:**
> Windows partitions are usually listed like the one my cursor is hovering over in the screenshot (*43 GB Filesystem*). Simply click it, then enter your password, and it'll be mounted. From there it's a simple matter of dragging and dropping any files you want to transfer over.

Assuming of course there is room in Ubuntu to do that. He said he's been using Gparted without knowing much about what he's doing. That's why I asked for a screenshot.

---

### Post by DGPoulton on 2010-06-28
i haven't finalized anything with Gparted for fear of servilely damaging my computer, here the screen shot, and yea if i could just drag the files over to ubuntu, and leave vista empty of what i need that'd be awesome. And most of what im copying isnt hard to replicate, just strenuous to re-aquire

---

### Post by nothingspecial on 2010-06-28
I`m going to bed now.

But I will not help you any further until you back your stuff up to some sort of external media.

And then remove it from your computer.

Anyone posting here (no matter how knowledgeable) can make a typo, which you may copy and paste.

If you really care about this stuff, make a backup first.

I speak, not to be harsh, but from experience.

Cheers.

---

### Post by warfacegod on 2010-06-28
I think your best option for moving your files is to put them on that external you said you had available to you. It just doesn't seem like you have enough room left on your HDD to move everything in one shot. You'd have to do several resize operations and that can be dangerous and it's allot more work.

Once you've got all of the data that you want from your Windows partition moved off of your Windows partition, you should run CHDSK from Windows and defragment Windows.

Now, the safest way to resize Vista is to let Vista' Disk Manager do it. Gparted can also do the resize operation *but* it is more likely to make Vista really cranky. As in broken.

When I did this a few weeks ago, Vista would only allow me to resize it to 75 GB. Not nearly small enough so I had no choice but to use Gparted. But I must stress that I got lucky Vista didn't break. If you use Gparted, I won't be held responsible for what happens. Unless, of course, it works. Then you can give me all the credit you like.:p

Anyway, you are going to have to decide what size Vista's partition is going to be. I should think 20 GB would be more than enough but then I don't game so I could be way off.

Post back when you've gotten that far and then we can start the Ubuntu process.

---

### Post by warfacegod on 2010-06-28
nothingspecial is right. We both speak from experience. If you use the External then that is your backup.

---

