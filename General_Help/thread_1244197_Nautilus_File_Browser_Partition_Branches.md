---
title: "Nautilus File Browser Partition Branches"
date: 2009-08-19
forum: General Help
---

### Post by Sean Moran on 2009-08-19
Hello fellow freedom people.  This is my first post on the forum so please excuse me for my ignorance having only briefly read the rules of conduct.

Most of all I wish to thank the developers of Ubuntu for making my 1998 dreams come true after over ten years of waiting and hoping for an intelligent Linux desktop that sorts out the ADSL automatically (I am not all that intelligent so I need this Jackalope like a sunrise needs an horizon).  One small step for online ease but it truly IS the most wonderful giant IT leap I remember since I discovered the Commodore Amiga w/20mb hdd in 1989.  April Fool's Day 2009 when the .iso download made it onto the CD and I finally made my escape from the clutches of commercial software on my desktop.

Thank you for taking the wisdom of the Bantu language to another level.

Everything has been running along very nicely since then, and I know that this is probably one of the most pedantic stumbling blocks you might imagine, but I am rather fastidious to the point of OCD regarding my pride and joy; my Calista the 2.53Ghz P4, and I'm baffled as to how the different disk partitions on my two HDDs are ordered in **tree** and **places** left-hand  columns when I open the Nautilus file browser.  

If you can picture my desktop history moving from Wxxx 98 directly to Ubuntu and remember the old W98 Explorer file browser, with the usual C:-D:-E: etc.  order down the list, then I hope you can understand how absolutely silly this tiny problem is with regards a totally fantastic dreamworld of an O/S (although 256Mb RAM might be a little on the minimalist side now that the old commercial o/s has been chucked in the  'RECYCLE_BIN' <ed> for good.  (That's a user/hardware problem so don't worry.)

Now, about this silly problem that I cannot seem to mount my partitions in any sort of alphabetical directory structure that makes any sense to me.

I am running twin HDDS: **sda1-15** and **sdb1-11**. On the **sda** HDD, they follow a structure based around the PC-DOS style C:-D:-E: alphabetical order that I have adopted from the old Win98 days, ie. C=CODE D=DATA E=EXCH (FAT32/ext3 exchange formatted FAT32) F=FILE G=GRAP(Graphics)  H=HOME I=INCO (Incoming digital photos and MP3 music) J=JIVE K=KERN (Kernel) etc.

On the **sdb** drive, they are named for size, and used for backups until I fill up my 80Gb sda: Arch16, Arch32, Arch64 etc.

Everything is working beautifully!  There is no doubt in my mind that Ubuntu has been the catalyst for Linux to conquer the desktop market.  However there is this one little glitch.  My Nautilus tree list of partitions/media/devices looks like this: 

< .png image snipped because I just worked out the answer and now it looks like that + THIS! 9-) >

[img]http://antarctica.netau.net/img/ubuntu/npl_home.gif[/img]


I hope that the image is not too cumbersome.  I have looked at the online documentation a little and taken a quick browse over the postings here since joining a little earlier today, but I honestly think that I might be asking such a silly question that either nobody is bothered about this 'order' stuff or else I must be overlooking something obvious.

Can any of you experts with far more understanding of the Linux desktop and ergo Nautilus file browser please help me to work out how the listing of devices in the left-hand column of the file browser are ordered?

Either way, I am more grateful than words can say for this great advance in technology that has been so long awaited.

Thank you for curing my beloved computer of chronic Redmonditis. 

):P


---o00---

Sorry to forget to mention: the objective is to try to order the various partitions in roughly the same order as they are listed numerically, ie. : 

sda1 
sda2
sda5
sda6
sda nnn

sdb1
sdb2
sdb5
sdb6
etc.

That might help others to make sense of my silly qualm.  Quite honestly, there is nothing else I can remember having reason to complain about, so this is my best shot at a whinge.

---

### Post by lian1238 on 2009-08-19
I was curious about your question, so I did a little experiment of unmounting and mounting some paritions. I found that the latest one goes to the bottom of the list. (The order is chronological.)

I find it strange that you want to see the actual partitions. I personally like to see only the logical structure, e.g. There's home, then there's Music, Pictures, etc.

What I try to do is HIDE the actual mounted partitions (I mount everything in /mnt)

I guess it's personal taste, or just what we're familiar with (Windows: My Computer).

---

### Post by Sean Moran on 2009-08-19
Lian, thank you for the answer. It certainly IS an intelligent operating system, and it was confusing me the way that these partitions in a fairly carefully designed structure (I use physical <logical> partitions matched to logical data file structure so I always know where everything is on the <physical> disk) seem to keep rearranging in what I imagined was some sort of random order that continues to throw my mind off-target like an angled mahjongg board.  I can't think straight with these minor sorts of distractions.

I will try to realign the listings in the /etc/fstab file and see if I can get something to suit my needs tomorrow morning and report back as to how it helped, but time to let the computer cool off for the night now.  Here in Perth is an hour ahead of Bkk.  It's also a great surprise and an honour to get the answer from the capital of my favourite civilisation on the globe.  

Norn laab faan dee, kap.  (Sleep and dream good, with respect. <language Thai>)


---o0o---

Just after 11AM BKK TIME: I missed the obvious, although it was more a matter of just getting used to working entirely within my own account's home directory because it's right up there at the top of the Nautilus window, and there are no other users.  As you mentioned, Lian, it's about the *LOGICAL* so what was I worried about just because the list of media is ordered by the chronology of mounting?

I tried changing around the fstab order just to see if that made any difference after login to the file order, and that was probably the wrong way to try to fix it anyway, but needless to say 'mai pen lai' (the problem is of no importance).

There truly is no place like home.

---

