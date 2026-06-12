---
title: "Hundreds of transaction replays before boot up into Ubuntu??"
date: 2011-02-07
forum: General Help
---

### Post by carlos123 on 2011-02-07
Hi there, 

Using Ubuntu 10.10 (I think it's called Maverick).  

Every few boot up times hundreds of transaction replays occur before the Ubuntu login screen appears.  This last time it was 828 replays!  Aside from it causing bootup to take much longer I am wondering if this is something I should be concerned about?

Here is a small sampling of what gets thrown into my boot.log 

--------------------------------------------------------------
Replaying journal: |=================================       \ 83.6%  823 trans
Trans replayed: mountid 50, transid 35912, desc 120, len 1, commit 122, next trans offset 105
Trans replayed: mountid 50, transid 35913, desc 123, len 2, commit 126, next trans offset 109
Trans replayed: mountid 50, transid 35914, desc 127, len 7, commit 135, next trans offset 118
--------------------------------------------------------------

Then toward the end it says...

--------------------------------------------------------------
Reiserfs journal '/dev/sda7' in blocks [18..8211]: 828 transactions replayed
--------------------------------------------------------------

/dev/sda7 corresponds to my home partition mounted on...well.../home.  

I've been using Ubuntu for years and have never seen this occur on my home partition before.  

I am not running any weird problems that might corrupt anything so I am wondering why this seemingly excessive replay?  

Any help to understand this would be appreciated.  

Thanks. 

Carlos

---

### Post by brolyx on 2011-09-27
Hi carlos123,

Have you solved your problem? I'm having the same issue on my machine, although only */var* is formatted with reiserfs while */home* and **/ are ext4 partitions.
Running Arch Linux with kernel 3.04

Cheers

---

### Post by carlos123 on 2011-09-27
Hi brolyx, 

No...I haven't solved the issue that causes all these transactions to be replayed.  

My home, root, and I think one other partition are formatted with reiserfs but only one partition ever replays all these hundreds of transactions.  My home partition (it's a separate partition).  

No clue as to why. 

It doesn't happen on every boot up either. Maybe once ever 3 or 4 bootups but not every time. 

I've just let it and have ignored the problem.  The only consequence seems to be that my boot takes forever that once every four boot ups.  

I can live with that...for now :).  

Carlos

---

### Post by blueridgedog on 2011-09-27
Is it possible that the system is shutting down prior to an unmount?  You may want to test it by manually unmounting it before shutting down.

---

### Post by carlos123 on 2011-09-27
Hi blueridgedog, 

Well...I normally shut down by going to the menu, selecting Shut Down, and then confirming the Shut Down within the confirmation dialog that shows up. 

If by manually you mean going to the command line and executing a shutdown command...I can try that for a week and see if that makes any difference. 

If it does...there is some kind of bug in the Ubuntu shutdown procedure executed from the menu system. 

I'll report back here if I remember to do so. 

Thanks. 

Carlos

---

### Post by blueridgedog on 2011-09-28
By manually I meant to open a terminal and unmount the partition, then shut down (gnome or terminal command).  This would determine if it was an unmounting issue.

---

### Post by carlos123 on 2011-09-28
Hmm...I'll have to try that. 

I wonder...what comes to mind with such a manual shut down is that I often have lots of applications open when I shut down from the menu. 

Occassionally I shut down all applications before shutting down. 

I wonder if that would explain this. 

Hmmm...because if I unmount I will obviously lose stuff I have open (I think).  

Interesting. 

Carlos

---

### Post by blueridgedog on 2011-09-28
> **carlos123 said:**
> I often have lots of applications open when I shut down from the menu. 

Occassionally I shut down all applications before shutting down. 

I wonder if that would explain this.

The best explanation yet.  You can also test it by opening a open office document, typing a line, saving it, typing another line then shutting down.  Upon a reboot, examine the file.

---

### Post by carlos123 on 2011-09-28
Well...I've never had anything get lost but I think that may be just because I always save everything before shutting down than otherwise. 

I guess I always assumed that Ubuntu would close everything for me gracefully. 

What's odd is that there are usually something like 800 transactions that get replayed during a reboot after I have shut down like I do. 

Hard to believe there are 800 transactions waiting to be saved or otherwise processed but then again...I do run Apache, MySQL, PHP, and a host of others and I suppose all this stuff might have a lot going on underneath. 

Regardless I am now going to change my habit and shut down everything manually before...well...really shutting down.  

Thanks for your input you all!  

Carlos

---

### Post by blueridgedog on 2011-09-28
> **carlos123 said:**
> 
Hard to believe there are 800 transactions waiting to be saved or otherwise processed but then again...I do run Apache, MySQL, PHP, and a host of others and I suppose all this stuff might have a lot going on underneath.


Apache and MySQL may take longer to shut down than the system is giving, but you would think that it would wait for a completed signal.

---

