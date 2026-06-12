---
title: "Any sign of a fix for burning dvds in 10.04?"
date: 2010-07-06
forum: General Help
---

### Post by johnston_evo3 on 2010-07-06
As the title says any sign of a fix for the burning problems.  I notice I'm not the only one having hassles and I have tried every solution I can find with no luck.

Since upgrading any discs that I manage to burn don't work in all machines.

Brasero gets to estimated time which just keeps increasing without doing anything.

Gnomebaker Gets down to 1 minute to go then just hangs.  So far we have managed to get the discs that have burnt to play in one DVD player and 1 PS2 although it stopped half way through the film so not sure if it was a DEVEDE problem making the image or a burn problem .

K3b spits the discs out having burnt a little and says it possibly a buffer underrun problem.

Everything was okay before the upgrade, all discs burnt played on every DVD player and the PS3.

So any one know if the bug is going to be fixed anytime soon or is there a way to revert to 9.10 or 9.04.  1 problem is with it not burning properly I can't backup all my files on to disc plus I'm not convinced a disc image will burn to do a fresh install either. so is there a way to do it through synaptic?

Many thanks Iain

---

### Post by jimmers on 2010-07-06
I use Lucid and have never had any problems burning DVD's in K3b, Brasero I have had a few problems with, but as I tend to use K3B mainly, this not a worry.
I did a clean install (As I always do) instead of upgrading, as I have had experience and heard reports of Upgrades from Hell.

This post may not be of any use to you, but thought it important to state that not everyone has problems burning DVD's in Lucid.

Luck

Jimmers

Linux User         516269
Ubuntu User      31738

---

### Post by johnston_evo3 on 2010-07-06
I noticed not everyone has been having problems but there has been a few.

I've went the upgrade route before without any hassles so didn't hesitate this time.  Well I did a bit I left it a few weeks for any wrinkles to be ironed out.

It's just a shame, it's one thing you would think would work out of the box.  Especially since there were no problems before.

---

### Post by johnston_evo3 on 2010-07-08
A wee bump to see if anyone has come up with anything before I dump half my hard drive to go back to 9.04

---

### Post by scouser73 on 2010-07-08
Why don't you completely remove Brasero.

**> sudo apt-get purge brasero**

**> sudo apt-get autoremove brasero**

Now reinstall it and see if the problem persists

**> sudo apt-get install brasero**

It may not work but it's worth giving it a go before you go back to 9.04

---

### Post by johnston_evo3 on 2010-07-08
tried that and done the same for gnomebaker and k3b

---

### Post by StuartN on 2010-07-08
> **johnston_evo3 said:**
> Brasero gets to estimated time which just keeps increasing without doing anything.

Gnomebaker Gets down to 1 minute to go then just hangs.  So far we have managed to get the discs that have burnt to play in one DVD player and 1 PS2 although it stopped half way through the film so not sure if it was a DEVEDE problem making the image or a burn problem .

K3b spits the discs out having burnt a little and says it possibly a buffer underrun problem.

Interesting.

What messages do you get if you start these applications from a terminal?
What information is written to the logs?
Are there any relevant bugs at Launchpad?

---

### Post by ellgor on 2010-07-08
Hi,

Here's something I came across whilst looking to burn multi-session dvd/cd's, the original post was having the same problem and found that an older version of K3b worked when the new one didn't, here is the link to the files : 

[http://packages.ubuntu.com/jaunty/libk3b3](http://packages.ubuntu.com/jaunty/libk3b3)
[http://packages.ubuntu.com/jaunty/k3b-data](http://packages.ubuntu.com/jaunty/k3b-data)
[http://packages.ubuntu.com/jaunty/k3b](http://packages.ubuntu.com/jaunty/k3b)

install the k3b file last as there are dependencies to be got for the others.

To stop apt from trying to update to a newer version, add this :

sudo gedit /etc/apt/preferences


Code:
Package: k3b
Pin: version 1.0.5*
Pin-Priority: 1001

Package: k3b-data
Pin: version 1.0.5*
Pin-Priority: 1001

save and update, hope this helps.

Regards, Ellgor

---

### Post by mikewhatever on 2010-07-08
You didn't link to any bug reports (are there bug reports?). johnston_evo3, you can't honestly expect a fix for the bug that no one reported.

---

### Post by pbrane on 2010-07-08
I had a similar issue with brasero not working. I got it to work by running a simulation burn, can't remember what it was called, but after that said it completed successfully, the real burn worked! I now use growisofs, I only tried brasero that one time.

---

### Post by johnston_evo3 on 2010-07-08
> **mikewhatever said:**
> You didn't link to any bug reports (are there bug reports?). johnston_evo3, you can't honestly expect a fix for the bug that no one reported.

I noticed on my searches other people have complained of the same problems.

 I've never had any major bother that couldn't be fixed through searching the forum before so don't know how to do the bug report bit.

> **ellgor said:**
> Hi,

Here's something I came across whilst looking to burn multi-session dvd/cd's, the original post was having the same problem and found that an older version of K3b worked when the new one didn't, here is the link to the files : 

[http://packages.ubuntu.com/jaunty/libk3b3](http://packages.ubuntu.com/jaunty/libk3b3)
[http://packages.ubuntu.com/jaunty/k3b-data](http://packages.ubuntu.com/jaunty/k3b-data)
[http://packages.ubuntu.com/jaunty/k3b](http://packages.ubuntu.com/jaunty/k3b)

install the k3b file last as there are dependencies to be got for the others.

To stop apt from trying to update to a newer version, add this :

sudo gedit /etc/apt/preferences


Code:
Package: k3b
Pin: version 1.0.5*
Pin-Priority: 1001

Package: k3b-data
Pin: version 1.0.5*
Pin-Priority: 1001

save and update, hope this helps.

Regards, Ellgor

Doing that managed to get a disc burnt in K3b the PS3 hasn't recognised it going to need to get someone to try it on another dvd player to see how it goes.

Oddly since doing it Brasero is only recognising 4.7GB discs as 4.0GB

---

### Post by mikewhatever on 2010-07-08
Well, johnston_evo3, complaining is ok, it helps people cope with frustration, but it does nothing as far as fixing bugs goes. If you have a bug you want fixed, the least you can do, is to file a bug report. Afterwards, complain as much as you like.

---

### Post by johnston_evo3 on 2010-07-08
Okay I only asked if anyone knew anything about a fix because a search threw up a number of older threads with similar problems.

It would be pretty stupid to put in a bug report for an issue that can be fixed.  When I have had other issues I have found the solution thanks to the search facility or people I have mentioned it to have supplied fixes.

ellgor was nice enough to give a possible solution to my problems and it may have partially worked and may be enough of a solution, at the very least it seems it will let me make a hard copy of things and burn a new install iso and do a fresh install not an upgrade.

That was a lot more helpful than taking the high and mighty approach.  Also if there was no fix someone else could send me along to a previously listed bug report, as stated I am not the only one so there is a good chance someone has already started a report to which I could put my name rather than starting another report on the same item.

---

### Post by StuartN on 2010-07-08
> **johnston_evo3 said:**
> Oddly since doing it Brasero is only recognising 4.7GB discs as 4.0GB

If you start the various burning applications from a terminal, then some additional error messages may be displayed, which you can copy and paste here.

If you look also at your log files, there may be messages while the burners run.

---

### Post by SoFl W on 2010-07-08
I just tried to burn a data disc (pictures) with Brasero that was just barely over 4 gigs onto a dvd that holds 4.7, couldn't do it.  I have had no problems ripping DVDs with Brasero, but I did notice a few threads with burning problems.  

Disappointing, for what it is worth here is the error log.

```
Jul  8 18:45:10 desktop kernel: [129725.935531] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul  8 18:45:10 desktop kernel: [129725.935534] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jul  8 18:45:10 desktop kernel: [129725.935538] sr 3:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Jul  8 18:45:10 desktop kernel: [129725.935543] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
```
I use gnome so I am not sure I want to install the KDE burner. (K3B)

Edit:
I ended up using the drag and drop burner* inside *nautilus.  Works.

---

### Post by StuartN on 2010-07-09
> **SoFl W said:**
> Disappointing, for what it is worth here is the error log.

```
Jul  8 18:45:10 desktop kernel: [129725.935534] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jul  8 18:45:10 desktop kernel: [129725.935538] sr 3:0:0:0: [sr0] Add. Sense: Illegal mode for this track
```

That is useful, the error messages lead to Launchpad bug #435237 [https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/435237](https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/435237) (which is closed) and bug #405544 [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544), both of which have links to additional / duplicate bug reports.

In Bug #405544, comment 39 says this is a kernel error [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544/comments/39](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544/comments/39) and comment 58 says that installing kernel 2.6.32 from the mainline archive will fix it [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544/comments/58](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544/comments/58)

There are instructions on installing a mainline kernel at [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds)

---

### Post by johnston_evo3 on 2010-07-09
Okay the disc I burnt yesterday worked so I burnt another copy no problems.

I then went to do a different iso which I did through DEVEDE, it all looked good until it was finalizing and it spat out an error this was in the de-bugging output.

> 
System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.32-23-generic
Devices
-----------------------
ATAPI DVD A  DH16A1P RG11 (/dev/sr0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD-R Sequential

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: "Current Write Speed" is 16.4x1352KBps.
   12484608/1528651776 ( 0.8%) @2.5x, remaining 12:08 RBU 100.0% UBU   9.7%
   44007424/1528651776 ( 2.9%) @6.8x, remaining 5:03 RBU 100.0% UBU  99.6%
   75988992/1528651776 ( 5.0%) @6.9x, remaining 3:49 RBU 100.0% UBU  99.8%
  108462080/1528651776 ( 7.1%) @7.0x, remaining 3:29 RBU 100.0% UBU  99.8%
  141426688/1528651776 ( 9.3%) @7.1x, remaining 3:06 RBU 100.0% UBU  99.8%
  174850048/1528651776 (11.4%) @7.2x, remaining 2:50 RBU 100.0% UBU  99.8%
  208797696/1528651776 (13.7%) @7.3x, remaining 2:44 RBU 100.0% UBU  99.6%
  243204096/1528651776 (15.9%) @7.4x, remaining 2:33 RBU 100.1% UBU  99.6%
  278134784/1528651776 (18.2%) @7.6x, remaining 2:23 RBU 100.0% UBU  99.6%
  313491456/1528651776 (20.5%) @7.7x, remaining 2:19 RBU 100.0% UBU  99.8%
  349372416/1528651776 (22.9%) @7.8x, remaining 2:11 RBU 100.0% UBU  99.8%
  385744896/1528651776 (25.2%) @7.9x, remaining 2:04 RBU 100.0% UBU  99.8%
  422608896/1528651776 (27.6%) @8.0x, remaining 2:00 RBU 100.0% UBU  98.8%
  459964416/1528651776 (30.1%) @8.1x, remaining 1:53 RBU 100.0% UBU  99.6%
  497778688/1528651776 (32.6%) @8.2x, remaining 1:47 RBU 100.0% UBU  99.8%
  536117248/1528651776 (35.1%) @8.3x, remaining 1:43 RBU 100.0% UBU  99.2%
  574914560/1528651776 (37.6%) @8.4x, remaining 1:37 RBU 100.0% UBU  99.6%
  614203392/1528651776 (40.2%) @8.5x, remaining 1:32 RBU 100.0% UBU  99.6%
  653983744/1528651776 (42.8%) @8.6x, remaining 1:28 RBU 100.0% UBU  99.6%
  694255616/1528651776 (45.4%) @8.7x, remaining 1:22 RBU 100.0% UBU  99.6%
  735019008/1528651776 (48.1%) @8.8x, remaining 1:17 RBU 100.0% UBU  99.4%
  776273920/1528651776 (50.8%) @8.9x, remaining 1:13 RBU 100.0% UBU  99.2%
  818020352/1528651776 (53.5%) @9.0x, remaining 1:08 RBU 100.0% UBU  99.6%
  860225536/1528651776 (56.3%) @9.1x, remaining 1:03 RBU 100.0% UBU  99.6%
  902922240/1528651776 (59.1%) @9.2x, remaining 0:59 RBU 100.0% UBU  99.4%
  946110464/1528651776 (61.9%) @9.4x, remaining 0:54 RBU 100.0% UBU  99.6%
  989790208/1528651776 (64.7%) @9.5x, remaining 0:50 RBU 100.0% UBU  99.0%
 1033994240/1528651776 (67.6%) @9.6x, remaining 0:45 RBU 100.0% UBU  99.6%
 1078624256/1528651776 (70.6%) @9.7x, remaining 0:41 RBU 100.0% UBU  99.6%
 1123778560/1528651776 (73.5%) @9.8x, remaining 0:36 RBU 100.0% UBU  99.6%
 1169424384/1528651776 (76.5%) @9.9x, remaining 0:32 RBU 100.0% UBU  99.4%
 1215528960/1528651776 (79.5%) @10.0x, remaining 0:28 RBU 100.0% UBU  99.4%
 1262157824/1528651776 (82.6%) @10.1x, remaining 0:23 RBU 100.0% UBU  99.6%
 1309245440/1528651776 (85.6%) @10.2x, remaining 0:19 RBU 100.0% UBU  98.4%
 1356824576/1528651776 (88.8%) @10.3x, remaining 0:15 RBU 100.0% UBU  99.4%
 1404895232/1528651776 (91.9%) @10.4x, remaining 0:10 RBU 100.0% UBU  98.6%
 1453457408/1528651776 (95.1%) @10.5x, remaining 0:06 RBU 100.0% UBU  99.6%
 1502511104/1528651776 (98.3%) @10.6x, remaining 0:02 RBU  77.9% UBU  99.6%
/dev/sr0: flushing cache
/dev/sr0: updating RMA
/dev/sr0: closing disc
:-[ CLOSE DISC failed with SK=5h/SESSION FIXATION ERROR - INCOMPLETE TRACK IN SESSION]: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:746412 -dvd-compat -speed=16 -use-the-force-luke=bufsize:32m 


---

### Post by mikewhatever on 2010-07-09
> **johnston_evo3 said:**
> Okay I only asked if anyone knew anything about a fix because a search threw up a number of older threads with similar problems.

It would be pretty stupid to put in a bug report for an issue that can be fixed.  When I have had other issues I have found the solution thanks to the search facility or people I have mentioned it to have supplied fixes.

ellgor was nice enough to give a possible solution to my problems and it may have partially worked and may be enough of a solution, at the very least it seems it will let me make a hard copy of things and burn a new install iso and do a fresh install not an upgrade.

That was a lot more helpful than taking the high and mighty approach.  Also if there was no fix someone else could send me along to a previously listed bug report, as stated I am not the only one so there is a good chance someone has already started a report to which I could put my name rather than starting another report on the same item.

Well, I am glad you found a solution.
I guess the thread title was the part that confused me. The way I read it seemed to imply that you expected a fix to a know bug, which, as you've explained, wasn't the case.
I hope others will benefit from this thread as well.

---

