---
title: "Tips to preserve RAM?"
date: 2012-09-30
forum: General Help
---

### Post by Stonecold1995 on 2012-09-30
I have a computer with 16 GB of RAM, but I often run many memory-intensive programs on at once.  Chromium itself often takes up nearly half, and on top of that I often have Windows 7 and another instance of Kubuntu in VirtualBox, along with other programs like KTorrent and Folding@home.  I also have /tmp mounted as tmpfs.  Because of this, it's not uncommon for my computer to run out of RAM, and slow down tremendously (forcing me to wait over 10 minutes sometimes for it to respond long enough for me to go to terminal and kill some programs, [usually chromium-browse]("http://www.pictureshack.us/images/7949_screenshot2.png")).  I also don't have any swap enabled.

What I currently do is, as soon as I notice my computer mouse stuttering and music skipping, I quickly press Control+Alt+F1 get to console and run "killall -9 some_large_process".  But the problem is that it's usually too late to switch to a new session like that by the time the mouse stutters. So sometimes I have to wait more than 10 minutes for the login prompt to appear (and worse, when I enter my name, if the password prompt takes more than a minute to appear, it gives me a login timeout error).  If it takes too long, I'll just use SysRq and forcibly reboot the computer, but then I may loose important data, so it's not an ideal solution.

I keep hearing that zRAM is good on computers with little RAM.  My concern is, does zRAM always compress all of the RAM, causing a performance degradation if I'm only using 1/3 of my total RAM, or does it *only* compress RAM that would otherwise go over the physical limit?  Would zRAM be good for my computer?  Do I just install it and leave it be and if I start using too much RAM it'll automatically compress the extra or what?

If zRAM isn't a good idea, are there any alternatives short of re-partitioning my disk to use swap?  Otherwise would it be a good idea to create a script that kills chromium-browse if the RAM usage goes too high (killing chromium-browse wouldn't close Chromium, it would just kill the individual pages making them all "he's dead jim" errors)?  If I can, I'd like to avoid potentially loosing my work just to prevent a *potential* lockup.

Basically I'm just looking for any tips to preserve RAM (I'm thinking of expanding to 32 GB instead of 16 but my computer's a laptop with only two slots, so if it already has two 8 GB cards it'll be more expensive to throw them out and get two 16 GB cards than simply adding another 16 GB card).

---

### Post by Epodx64 on 2012-09-30
If I remember correctly zRam is just swap space that acts like additional Ram it doesn't suffer from the I/O slow down which I don't know how healthy that'd be for your computer I probably personally wouldn't use it. I think your best bet would just being adding a large amount of swap space which pretty much runs concurrently with your ram when it detects high usage at least thats been my experience if it I've only got 4GiBs of Ram and 4GiB's of Swap but I've never had any problems with it (I used Kubuntu and KDE for about 4 years before switching to Cinnamon) another thing you might wanna test is your ram itself with Memtest86+ even with running memory intensive programs 16GiB's of Ram should be able to handle it without issue it find it concerning that Chromium uses half that amount I frequently use Chrome Dev and Chromium Stable and it never seems to use more then 1.5 GiBs of ram even with 15-20 tabs opened and some extensions installed so my advice is to first run Memtest86+ and make sure your rams not the probably then add a large amount of swap space I'd skip zRam personally a quick way to add swap is like this
```
 sudo dd if=/dev/zero of=/swapfile1 bs=1024 count=524288
``` (would create 512mb of swap obviously create more then this)  
breaks down like this ```
 1) if=/dev/zero : Read from /dev/zero file. /dev/zero is a special file in that provides as many null characters to build storage file called /swapfile1.

2) of=/swapfile1 : Read from /dev/zero write storage file to /swapfile1.

3) bs=1024 : Read and write 1024 BYTES bytes at a time.

4) count=524288 : Copy only 523288 BLOCKS input blocks. 
```

next
```
sudo mkswap /swapfile1 
```

Then setup of correct file permissions for security reasons
```
sudo chown root:root /swapfile1
sudo chmod 0600 /swapfile1 
```

A world-readable swap file is a huge local vulnerability. The above command make sure only root user can read/write to the file. Finally, activate /swapfile1 swap space immediately, enter
```
sudo swapon /swapfile1 
```

To active /swapfile1 after reboot use nano or your text editor of choice and
```
sudo nano /etc/fstab

and then append the following

/swapfile1 swap swap defaults 0 0 
```

reboot then run
```
$free -m 
```

to verify it is activated.

---

### Post by jrog on 2012-09-30
> **Stonecold1995 said:**
> I often run many memory-intensive programs on at once.  Chromium itself often takes up nearly half, and on top of that I often have Windows 7 and another instance of Kubuntu in VirtualBox, along with other programs like KTorrent and Folding@home.
I see a way to preserve RAM somewhere in there... ;)

---

### Post by LewisTM on 2012-09-30
It's easy to try zRAM, just install package **zram-config**. No need to reboot, it starts to work immediately. 

The command
```
swapon -s 
```
should list a number of /dev/zram# device files corresponding to your number of CPU cores.

See if it helps, if not go with other solutions. If found that it stabilizes a system that would otherwise go critical from lack of RAM and crazy swapping to disk, allowing you to take the necessary measures like closing a few programs. Have a RAM monitor always visible so you see this coming.

Cheers!

---

### Post by Stonecold1995 on 2012-09-30
> **Epodx64 said:**
> I frequently use Chrome Dev and Chromium Stable and it never seems to use more then 1.5 GiBs of ram even with 15-20 tabs opened and some extensions installed

I think it's normal for Chromium to be taking up half my RAM considering I usually have a LOT of tabs open.  As in, last night I had 200-300 tabs open (yeah ridiculous I know).  It's just that my VPN is ridiculously slow (if I try to load Google, it only responds 50% of the time and takes about 30 seconds to load), so I just don't close tabs unless I am 100% sure I'll never need to go to the page again, so it results in a lot of open tabs.  Plus I need to preserve bandwidth so I can't be frequently closing and opening tabs.  I'm at Chromium's limit because it can only have so many running processes, so each process ends up managing multiple tabs and that leads to instability even if my RAM isn't completely full, so things like VirtualBox just throw it over the edge.  I know the answer "don't use that many tabs" would work, but I kind of need to have them open.

> **LewisTM said:**
> It's easy to try zRAM, just install package **zram-config**. No need to reboot, it starts to work immediately. 

The command
```
swapon -s 
```
should list a number of /dev/zram# device files corresponding to your number of CPU cores.

See if it helps, if not go with other solutions. If found that it stabilizes a system that would otherwise go critical from lack of RAM and crazy swapping to disk, allowing you to take the necessary measures like closing a few programs. Have a RAM monitor always visible so you see this coming.

Cheers!

Alright, I'm trying it, let's see how it goes.  How efficient is the compression?  Like, does it just use DEFLATE or something slower but more powerful?

---

### Post by LewisTM on 2012-10-01
From this [blog]("https://www.extremeshok.com/blog/ubuntu/debian-ubuntu-raspbian-zram-compression-compressed-swap-residing-in-ram-over-allocating-memory/"):
> A successor to compcache, zram is fully integrated in the Linux kernel and uses lzo compression. Compress memory on the fly to reduce swapping. Uses a small amount of cpu, however the reduced i/o usage more than makes up for this.
LZO is very fast and comparable to deflate. Speed and low CPU utilization are critical here.

---

### Post by Stonecold1995 on 2012-10-01
I was using a lot of RAM, and used 2.4 GB of swap, but when I closed the memory intensive application the used swap remained.  I know the way to put the swap back to RAM is this:
```
sudo swapoff -a
sudo swapon -a
```
The first command took a long time to complete, and the swap was slowly put back into the RAM, but then when I did the next command, the swap didn't turn back on.  My computer says "no swap space available".  Will the swap turn back on only when I need it or should it always be on (just not being used) like most swap?

---

### Post by LewisTM on 2012-10-01
The command [FONT="Courier New"]sudo swapon -a[/FONT] won't work because it only uses swap spaces specified in fstab
You must manually specify the zram special files, with high priority
```
sudo swapon -p 5 /dev/zram0 /dev/zram1
```
That being said, I doubt you need to manually control swapping. Linux does not erase data in swap when more RAM becomes available. The same amount of space is reserved for zram as before (as should be reported by swapon -s), only this time Linux reports that some data was written into it, which will be overwritten as needed. Using swapoff only removes zram and return it to normal ram, thus you lose the benefit of compressing the data.

In other words, the % swap is an indication of maximum load, not current load.

I often see worries that zram "steals away" useful RAM. It's not the case! Data functionally always remains in RAM, only sometimes in a compressed (hence more efficent) state.

---

