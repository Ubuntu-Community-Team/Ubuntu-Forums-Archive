---
title: "[Server, 9.10] Memory leak"
date: 2009-11-19
forum: General Help
---

### Post by dirty.hippy on 2009-11-19
I have recently build an Atom box as a home server (Atom 330, 2 gigs RAM) and put Ubuntu Server 9.10 on it.  Over time, used memory as reported by top goes up and up, but there seem to be no processes that are taking up much memory.  Before I last rebooted, to reported 1997532k used, but said that rtorrent was using the most memory with 1.2%.  I checked the number of running processes using ps -e and there weren't too many, so it wasn't like there were a bajillion small processes taking up the memory.  Any ideas?

---

### Post by juancarlospaco on 2009-11-19
Watch for ForkBombs if you are not the only user.
*/etc/security/limits.conf may look interesting to you...*

---

### Post by dirty.hippy on 2009-11-19
I am the only user on the machine, excepting 'virtual' users such as www-data for php.

---

### Post by Giblet5 on 2009-11-19
That's disk buffering in action.

You can still run commands that allocate huge amounts of RAM and they'll run just as fast as if the memory weren't in use.

This is a major complaint on Linux, Vista, and Win7. All three complaints are based on unrealistic perception that a "good" OS won't use all of the memory available, except for programs.

It's a mistaken perception.

The real test of memory in use is swap usage: when swap starts getting used, the pool of free RAM is becoming exhausted.

What's the swap usage there?

I run 9.10 desktop on an old Pentium III with 256MB of RAM. It provides web service (Apache2+MySQL+PHP), DNS, NFS access to a 1TB RAID array, IMAP, POP3, Samba, Mediatomb, and an SMTP relay. No swap is in use, and that is one busy little clunker.

---

### Post by dirty.hippy on 2009-11-19
I just rebooted the server and accicentally copied over the top report that I was looking at, but physical memory there was ~50 megs free, ~70 buffered, and the rest was under 'used'.  Are cached items listed under 'used' or 'buffers'? Unfortunately, I don't recall the swap statistics offhand.

---

### Post by Giblet5 on 2009-11-19
The 'top' command just runs continuously (and uses some resources...). It updates about every 3 seconds and understands some keyboard commands. For details, enter ```
man top
```

Try using the 'm' command (memory and swap). Interesting and useful stuff there, especially for a server.

You can install some better tools via ```
sudo apt-get install sysstat
```

Now read the man page for iostat ```
man iostat
```. You'll like that one.

Cheers!

---

### Post by dirty.hippy on 2009-11-19
Thanks for the quick reply.  I was using the m command from top, that is how I got the usage numbers in my previous post.  In looking at iostat, while it seems useful I don't see the relation between what it does (disk IO monitoring) and RAM usage.  Any other ideas are welcome.

---

### Post by Giblet5 on 2009-11-19
You can play with system accounting (package acct, same man page) but that's more useful for detecting CPU hogs...

You'll find that Ubuntu doesn't have a good (comprehensive) server management gui. Not like Redhat and others. The command line is adequate though.
--

Back to your issue:

My top (6GB RAM) shows I have 160MB free memory and the vast majority (over 5GB) of the rest is in buffers and cache.

Depite that, I can do a 'locate \* | sort -r' (something that uses a wee bit of memory to do) and the free memory stayed right around 70MB. Cache dropped noticeably, but is climbing again already.

It isn't a problem - it's a feature - on any post 2.4 Linux as well as Vista or Win7 (and newer Redhat, CentOS, Solaris, Suse, etc).

---

### Post by dirty.hippy on 2009-11-19
I see now that you are correct.  I would have thought that buffered/cached memory would show completely under 'buffers' in top, not split between 'buffers' and 'used'.  If you'd like to see exactly what the split is, you can use free -m .  I use the command line exclusively, so lack of a GUI program is not an issue.  Thanks for your assistance!

---

### Post by cariboo on 2009-11-19
A better way to check memory usage is to use the free command:

```
free -m
```

the result should look something like this:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2009       1435        573          0         41        686
-/+ buffers/cache:        708       1300
Swap:         3812          6       3805
```

in the buffers/cache line you will see that I'm using **708**Mb with **1300**Mb free. Swap seems to be using 6Mb.

---

### Post by jharris1993 on 2010-02-22
I have a simular problem - except that it's not a "memory leak" *per-se*, but a "swap" leak.
 
My System: A crufty old Dell Optiplex GX-110 with 512 megs of memory (I believe it's max'd out) and a 700 Mhz P3 or thereabouts.
 
I originally had Fedora 10 installed on it.
 
This machine is running a 4 x 1T RAID-10 array (total 2T space) on a 4-port eSATA card, and a second 2t external HDD on a second, identical 4-port card.
 
I use the RAID array as my main file store and it contains about 30 or so years of absolutely irreplacable data.
 
I regularly run a "cp -a. . . ." between it and the 2T HDD to have a second image "just in case"
 
It also has Samba, Apache, SWAT, NMB, and Winbind installed so that I can run this as a stand-alone file-store on my domain.
 
The file store has about 1.8 T of data stored.
 
The system drive is a 70-or-so gig drive, partitioned as 1 gig of swap and the rest as "/" where the O/S is installed.
 
When I had Fedora 10 installed - I could do a complete dump from the RAID array to the other external HDD - even with the GUI running - and experience ZERO problems. It ran, was reasonably fast and didn't thrash swap.
 
I went to upgrade to Fedora 12 and it was a nightmare. No way I could get it to recognize the Silicon Image eSATA card I had.
 
Since Ubuntu 9.10 WOULD recognize it, I made the jump - especially since I like Ubuntu better than Fedora anyway. . . . .
 
At the time - I didn't have two 4-port cards, I had one 4-port (Silicon Image) and a no-name-brand VIA chipset 2 port SATA plus USB plus PATA, plus. . . and every time I ran the external hdd on it, it would throw kernel errors (ATA. . .) faster than the Government throws away money! So I swapped it out and replaced it with a 2nd 4-port Silicon Image card, identical to the first.
 
Not trusting the copy on the external HDD because of all the ATA errors I was getting, I decided to wipe it clean and, (while I was there anyway), reformatted as ext4.
 
Now - using Ubuntu desktop - doing a total soup-to-nuts copy, it would proceed about 2/3 of the way and then puke; throwing memory errors and GUI errors. (I would end up with a system that was running, but not doing anything, with nothing but the background showing. At least it would gracefully shut-down when I hit the power button!)
 
As an experiment, I increased the amount of swap to 3 gigs, (by reducing the size of the main partition), wiped the external drive again, and restarted the copy.
 
Viz: (as root) cp -a -v /mnt/RAID/Public/* /mnt/Backup
 
I then created a script that runs (again as root) "free -m" every five seconds, and writes the results to a text file. ( > mytextfile 2>&1 )
 
I fired off the "instrumentation" script, and then fired off the main copy process in a second terminal session.
 
I started at zero swap used. At last check (tail mytextfile) the machine is using more than 1.6 gigs of swap - and still climbing. (The rest of the numbers are not particularly impressive)
 
"ps aux" shows a fairly good laundry list of processes, but the big memory hog is good 'ole "CP", with about - you guessed it! - 1.6 gigs of memory in use!
 
The process has been running for about 24 hours now, and has passed the original crash point - obviously now caused by exhausting swap - along with everything else!
 
This brings me to my question:
 
WHY should simply copying 1.8T of randomly sized data objects, (some in the 2-3 K size, some DVD-5 sized, and a fairly catholic distribution between those points), cause me to consume almost two gigs of swap? (so far. . . .)
 
Fedora had absolutely no problems with a single gig of swap making this kind of copy. And I know - I ran this copy **_several times_**, testing out a backup script I was writing! I don't remember what the figures for swap used were, but I don't remember being shocked outta my socks by it.
 
Every article I've read on allocating swap usually has something that sounds like this: "1 *GIG* of *SWAP*? Are you **CRAZY**?!!!"
 
These guys apear to be claiming that on a system that runs the entire US Government - along with the governments of Russia, Finland, England and a few 3rd world countries - they, _maybe_ on a bad day, peak at 64 megs of swap used. Of course the implication is that **anyone** that would allocate **an entire mortal gig of swap** is **_OUTTA THEIR MINDS_**!!!.
 
In my case, I have *three* gigs of swap, and it's evaporating faster than spit on a hot New Mexico sidewalk!
 
Is this REALLY normal? Is there a memory leak somewhere that oughta be reported as a bug? Needless to say - I'm a bit confused and I'd really like to know what to do here.
 
Thanks!
 
Jim

---

