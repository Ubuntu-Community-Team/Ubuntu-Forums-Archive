---
title: "Slow,"
date: 2006-02-03
forum: General Help
---

### Post by geearf on 2006-02-03
Hello,

I don't know what I have messed with, but Ubuntu is now really really slow on my desktop, but still good on my laptop.
My desktop is running kde 3.5 (well now 3.5.1 ..).
With : AXP @1700MHz, 512 Mb RAM, HD UDM5 (but mode 4 in Ubuntu, don't know why).
It was faster before but now (from when did it start ?) it feels heck slower.
If anyone has a clue to what to check ..
Thanks

---

### Post by chele on 2006-02-03
What was changed on the system recently?

I usually check if the system is swapping a lot in these situations. Go to Applications > System Tools > System Monitor. Click the Resources tab.

What CPU % does it show? What about Used swap (MB) & User memory (%)?

---

### Post by chele on 2006-02-03
[quote=geearf]My desktop is running kde 3.5 (well now 3.5.1 ..).[/quote]Oops, the previous suggestion was via a Gnome desktop, I am not familiar with the KDE system monitor, but I assume it provides similiar information?

---

### Post by geearf on 2006-02-04
Hello,

I am not really sure of what was changed, I think it has been slow for a while but yesterday I wanted to play planeshift, and it was too slow to play ..

Most of the time I have no swap used, but sometime it is.
Cpu(s): 54.7% us, 10.2% sy, 13.7% ni, 11.2% id,  9.1% wa,  0.4% hi,  0.7% si
Swap:   265032k total,        0k used,   265032k free,   212528k cached
Mem:    515720k total,   447580k used,    68140k free,    12788k buffers

I have folding@home running, so that must be why the CPU is really used now, (is it slowing my comp down ? it should not, it never did under Windows at least).

Thanks,

---

### Post by ace2005 on 2006-02-04
Just feels slow?

Try ksysguard, anything sucking up all the juice?

Oh and set KDE to start with an empty session  each time and then use this:
[http://www.kde-apps.org/content/show.php?content=32554](http://www.kde-apps.org/content/show.php?content=32554)

to manage the startup items you want to run on KDE startup

---

### Post by geearf on 2006-02-04
Hello,
well it feels slow, but it is also :)

I am running Ksysguard now, I'll take a screen after a while.
And I'll look at your link too thanks.

---

### Post by geearf on 2006-02-04
Here are some pics,
as for autostart I cannot install it because libqt has changed names with breezy, so I should tweak that a little.

Also maybe something else, when I'm building a file from a torrent, the beginning can really slow down the whole comp, and it should not :( (well before it did not at least).

Thanks.

---

### Post by geearf on 2006-02-04
Seems amarok, firefox and kicker are the ones taking most of the juice.

---

### Post by geearf on 2006-02-04
now I am moving some files from my laptop to my desktop, and it's almost unusable. Lots of freeze and so on ...

I thought it was a bit better after a few upgrade and installations I did but no.

And before you ask :
/dev/hde:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 156301488, start = 0

---

### Post by GeneralZod on 2006-02-04
Why are you running F@H as root? Have you altered its "nice" setting at all? Have you tried stopping it and seeing if your system speeds up? I'd highly recommend doing that and then checking out the CPU usage again.

I used it quite a lot a year or so ago and it never slowed my system down, but maybe more recent versions are buggy, or something.

---

### Post by geearf on 2006-02-04
Hello,

I start FAH as a service, therefore as root.
No really big need for it, it's just easier..

Thanks for any comment,

---

### Post by ace2005 on 2006-02-04
Can't you type the command you'd use to run the program in the Alt + F2 box and then in options make it run with a different priority and set it to low?

Have you tried Juk and Opera? both are better (well i think so anyway)

Opera is a lot faster and feels very responsive when compared to firefox due to better memory management and juk is juk, never hurts to try, use Ctrl + D to add a folders at a time, they will appear on the left column as playlists (if you reinstall make sure to save ~/.kde/share/apps/juk)

---

### Post by geearf on 2006-02-04
Well FAH has a nice of 19, so it should be okay I guess.
About opera yes, and I would probably use it it had the opera voice thing.
I'm really thinking of ditching Firefox to Konqueror actually (well I've been thinking about that for months...). I could do it with opera, which is also installed.

I think Amarok is really slowed down by the collection thing ...

Thanks,

---

### Post by claydoh on 2006-02-04
I also tried out kde 3.5.1 the other day and found it much much slower than 3.5.0, I imagine due to it being a testing thing (this was on Dapper, have not done 3.5.1 on Breezy yet)

---

### Post by geearf on 2006-02-04
hmm, I serioulsy think it was slow before, maybe I just got tired of it right now, or maybe it got worse thanks to .1.

Really I cannot say as I did no benchs at all ...

Thanks,

---

### Post by geearf on 2006-02-05
I've done a little test (not wanted actually).
I've started with the recovery mode, and log as root, and it was really fast.
Now I need to log in the normal mode as root to see if it's better or not, and if it is, then I am loading something wrong ..

---

### Post by geearf on 2006-02-05
I've tried login in as root in a normal session, it seemed a bit better (less things started) but the game was exactly as slow with lots of freeze, maybe that is only from the game and the whole system was better, hard to tell without some benchs. 

I will look that further.

---

### Post by geearf on 2006-02-05
I've looked at something else : 

 Timing cached reads:   656 MB in  2.01 seconds = 326.74 MB/sec
 Timing buffered disk reads:  122 MB in  3.00 seconds =  40.61 MB/sec

My desktop hardrive is a 80Gb, 7200 RPM, 8 Mb cache while my laptop drive is a 40 Gb, 4800 RPM, 2 Mb cache and guess what ?

the laptop gets about the double for cached reads (but also half for buffered disk reads).

I've tried with another kernel => same
With a live gentoo cd => same
Then I've tried to unplug the drive from its promise controller (attached to the mainboard, but not the standard controller) and plug it in to the standard controller => same

I really don't understand what is happening.
I guess I should bench it under Windows, maybe the drive is dying ?

Thanks,

---

### Post by geearf on 2006-02-08
Well, it seems the bad hd speed is due to a bad controller on my mother board ....

I have stoped most of the things that seem to slow me down (FAH, Amarok) and now I am transferring 2 files from my laptop to my desktop (170 Mb each), and again my comp is sometime freezing.

I'm lost
If you have any idea, please jump in :)

---

