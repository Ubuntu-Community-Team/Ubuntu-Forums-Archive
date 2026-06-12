---
title: "Large Files - BitTorrent Crash"
date: 2009-07-18
forum: General Help
---

### Post by stepdown on 2009-07-18
Hi, I've been trying to download some pretty large files and I have so far used two BitTorrent clients, Transmission and rTorrent.

The files in question are about 7-8GB in size, and when I load them into Transmission it freezes with no error output given. If I try to kill the process it goes 'zombie' on me which I think means I have to kill the parent process to get rid of it. It also continues to use up a LOT of CPU and I usually restart the system to stop it.

In rTorrent it gives me the error "File chunk write error: No such file or directory." and then freezes. Again, it uses up a lot of CPU and I have to restart the system to get everything back to normal.

Does anybody have any ideas what could be causing this? The file system is ext3 and it's got the encryption that Jaunty offered me when I installed it. I also have 40GB of free space on a 95GB partition.

Cheers,
Step

EDIT - I just tried loading the files into the torrent clients with a 1.5TB drive, and this worked. The problem might be the encryption on /home?

---

### Post by frischi on 2009-07-26
I have the same problem with luks and large files

if your looking for a workaound in rtorrent add
```
split_file_size = 8G
```
to your ~/.rtorrent.rc
8G worked for me anyway if you say you have problem with 7-8G i'd try 4G

this will split your files into parts afterwards you can use 
```
cat part1 part2 > entire_file
```
to join them

---

### Post by moster on 2009-07-26
I would install Ktorrent and turn on "file preallocation" in settings. Ktorrent is much better program and do not fragment disk because of this feature.

---

### Post by Charles Kerr on 2009-08-15
> **moster said:**
> I would install Ktorrent and turn on "file preallocation" in settings. Ktorrent is much better program and do not fragment disk because of this feature.

Transmission preallocates files by default as well.

In fact, if he's preallocating an 8 GiB file in ext3, that's probably what's causing the apparent freeze... that's not a fast operation like it is in ext4.

---

### Post by anonSam on 2009-11-24
I am having the same problem. This happens to me using Bittorrent 6.3 via Wine 1.1.31, uTorrent 1.8.4 via Wine, kTorrent 3.2.4 and Deluge 1.1.9. Small files and even 1.5GB files are fine, but 4.3GB and 6 or 8GB file sizes make this problem happen. Also, these larger files have many more peers then the smaller ones (just for your information). In Bittorrent and uTorrent (they behave exactly the same), I can start the torrent and it acts normal for about 5 minutes, and then my connection slows to about 10kb down and usually completely stops uploading. If other smaller sized torrents are running, they all slow down too but then work fine again if the large torrents are removed. When I stop the large torrent and close BT or uT, the windows closes normally except it is still running and there's no way I can kill the process (wine and wine server are still running too). In the case of kTorrent, the program screen just goes blank and I can force quit, but its process also stays open and I cannot kill it. I can't remember if Deluge still says on too, sorry, but it still only downloads at about 10kb max. When I reboot, everything is normal but when i open BT or uT again, it acts as if it was shut down without closing correctly (preforms file checks). Also, when I start the download of the large torrent again (second time after reboot), my BT log goes crazy and says IO error with a number next to it (I don't really want to create the situation again to get the exact message unless I really have to). It makes about 100 of these error lines real fast at the start and then the whole process repeats over again exactly the same.

Now:
The problem acts almost exactly the same on 4 different clients.
I do not have an ISP that censors or throttles any traffic.
I have tried disabling disk cache in the clients (write disk and disk reads).
I have tried disabling pre-allocating files in all clients.
I have tried using trackers only and then only DHT and peer exchange.
I have tried the torrent with all the files selected for download and
I have tried the torrent with only some of the files selected to download.
This problem began when I installed Ubuntu 9.10 (karmic).
I do not have an virus scanner running that would be scanning these files as they download (as I read in the uTorrent forums that this was the suggested problem).

However I did have a theory (based on absolutely nothing), that somehow the new encryption feature of the home directory in Ubuntu was causing some sort of conflict. I was saving my files to my HDD with the Ubuntu OS on it (to my home directory). I decided to try saving the downloading files directly to one of my external storage drives, reluctantly using it as a normal hard drive. Turns out it completely solved the problem! But I really don't like doing things this way and using what is supposed to be storage as an active HD, as well as being restricted in where I can save my files.

The external drive I used that solved the problem:
Seagate FreeAgent XTreme 1.5TB connected via Firewire 400 cable
The file system format is either NTFS or FAT. I cannot find this information now!
But I know it's one of these two. Under the Basic tab in Properties it only says:
Volume: 1500 GB Filesystem
It used to say the format there before...
Under System Monitor>File Systems>Type> it says "fuseblk" 
I also looked at everything using the Hard Info program, but it's just not listed anywhere anymore!

I really don't know why this solution worked for me, I'm only assuming it's something to do with the file system format. Anyway this is my first post, I hope the info helps us figure it out.

Edit: Doh! I just noticed your edit now. We had the same exact solution! I'll read slower next time.

---

### Post by anonSam on 2009-12-12
So for the first time since I posted here, I am downloading a file 4.46GB in size onto my encrypted hard drive and it's actually working correctly. My upload and download speeds are normal and I was even able to close BitTorrent and Wine successfully and all connections and processes stopped like they should have. I rebooted and started again and didn't get any errors. Hopefully it fixed itself, but we'll see. I was getting really tired of manually changing the save path for large files every time. I have no idea why it's working now.

EDIT:
NEVERMIND it still doesn't work. This was just a one time thing. Any ideas to fix this would be appreciated.

---

### Post by suniyo on 2009-12-31
I've a strange problem related to bittorrent client and disk usage analyzer, can anyone help it out here? have a look at it: [http://ubuntuforums.org/showthread.php?t=1368711](http://ubuntuforums.org/showthread.php?t=1368711)

---

### Post by MihaiCapot&#259; on 2010-01-13
I'm experiencing the same problem in Ubuntu 9.04 x86-32 on an ecryptfs encrypted ext4 home partition. I submitted a bug report:
[http://launchpad.net/bugs/507036](http://launchpad.net/bugs/507036)

---

### Post by stepdown on 2010-04-09
> **MihaiCapot&#259 said:**
> I updated to Karmic today and the problem seems to have gone away. I only tried one file (6.6 GB) in transmission and, while the program freezes for a couple of minutes while the file space is being allocated, it recovers and functions normally. Will report back after more experiments.
From [http://launchpad.net/bugs/507036](http://launchpad.net/bugs/507036)

---

### Post by anonSam on 2010-05-19
I upgraded to Lucid too (and BitTorrent 6.4c/wine 1.1.42) and this was one of the first things I tested. The test failed and it's acting the same way previously described. I find that 2.8GB is my size limit. Anything below that works fine. If I (1)load the large torrent, (2)start it, (3)stop it, and (4)reboot, I get the message at the bottom of BitTorrent saying "Allocating Files," and it appears to just hang like that. I suppose it's just processing super slow for me too, but I'm not really interested in recreating the condition and waiting for it.

---

### Post by razaz03 on 2011-06-26
I'm having the same problem with Natty and Deluge (Client Version: 1.3.2
Libtorrent Version: 0.15.6.0, same with Transmission).

I'm downloading the file to my windows partition on the same disk and it seems, prima facie, to be working as normal. File is 6.3GBs, same happens with a 14GB file. All the symptoms as above- stops downloading immediately, try to close crashed Deluge, xkill the window yet the process remains as zombie taking 100% of my puny netbook CPU. Only restart fixes.

I would request anyone's help as this isn't on- I had to restart my netbook a dozen times trying all the above suggestions to no avail.... I mean *restart my netbook like a windows machine for goodness sake!*

Help please!

---

