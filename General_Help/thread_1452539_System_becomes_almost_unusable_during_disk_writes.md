---
title: "System becomes almost unusable during disk writes"
date: 2010-04-12
forum: General Help
---

### Post by spearofsolomon on 2010-04-12
I'm using 9.10 Desktop 64bit on a Dell Latitude D830.  I have 4 gigs of RAM and a 7200 rpm sata hard drive.  Everything works pretty well, video, sound, and network.  Flash isn't as smooth as in Windows but I assume that's a Flash/64bit thing and not necessarily an Ubuntu thing.

However, one area of performance still lags far behind my Windows XP experience, and that's disk writes.  For instance, when I'm copying a large amount of information from a USB drive or from my Windows partition to my native partition, I can barely switch windows until the task is complete, nevermind trying to surf the Web.  I thought that that might be related to the slow performance of the ntfs driver, but recently I have been doing a lot of work with VMWare, and I get the same result when trying to pause virtual machines - it writes a largish amount of information to disk in a short amount of time and I can't do much until it finishes.

Here are some things I looked at based on other threads to try to debug my issue:

~$ sudo hdparm /dev/sda

/dev/sda:
 multcount     =  8 (on)
 IO_support    =  1 (32-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 38913/255/63, sectors = 625142448, start = 0

~$ sudo hdparm /dev/sda

/dev/sda:
 multcount     =  8 (on)
 IO_support    =  1 (32-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 38913/255/63, sectors = 625142448, start = 0
~$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=WDC, FwRev=11.01A11, SerialNo=WD-WXMY08LA1266
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=8
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=625142448
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   6372 MB in  1.99 seconds = 3194.20 MB/sec
 Timing buffered disk reads:  224 MB in  3.02 seconds =  74.26 MB/sec

That disk read speed is a little faster than average - several more tests showed it hovering around the 66 MB/sec range.  Of the other info, I see that UDMA is on which I understand is good, but if there is something else there that I should fix I don't see it.

I know that my computer can handle these tasks (at least the vmware stuff) without such a significant interface slowdown because in XP I did it with less RAM than I have now.  Is this just the way that the linux kernel scheduler fails to account for UI needs?

Thanks for any advice.

---

### Post by dcstar on 2010-04-13
> **spearofsolomon said:**
> 
.........
I know that my computer can handle these tasks (at least the vmware stuff) without such a significant interface slowdown because in XP I did it with less RAM than I have now.  Is this just the way that the linux kernel scheduler fails to account for UI needs?

Thanks for any advice.

There are many posts already on this issue and it seems to relate to particular hardware configurations because a lot of people are ok.

Try a 10.04 beta Live CD and see if the kernel with that works differently.

---

### Post by spearofsolomon on 2010-04-13
Thanks David.  I did comb through as many of those posts as I could before posting, without finding anything that solved my issue.  Sorry if this is redundant.

Will the 9 series of Ubuntu not be upgrading to the kernel that the 10.04 beta cd is using?

---

### Post by imbjr on 2010-04-13
I've seen this happen with increasing frequency as the new releases come out, fortunately I do not need to heft large files around too often.

I can just about tolerate a non-responsive desktop when it happens but it gets annoying when audio playback gets interrupted too.

---

### Post by spearofsolomon on 2010-04-13
@imbjr re audio:  Seriously.  That's another one of my pet peeves - I spent several hours adjusting properties of pulseaudio, but audio from my virtual machines is still stuttery.  Again, no issues in Windows.  I figured that was a different issue than the disk writing issue, but maybe it's all kernel related.

Maybe I just need to get an SSD so I don't have to fight this stuff.

---

### Post by imbjr on 2010-04-14
> **spearofsolomon said:**
> @imbjr re audio:  Seriously.  That's another one of my pet peeves - I spent several hours adjusting properties of pulseaudio, but audio from my virtual machines is still stuttery.  Again, no issues in Windows.  I figured that was a different issue than the disk writing issue, but maybe it's all kernel related.

Maybe I just need to get an SSD so I don't have to fight this stuff.

Aren't you making a bit of a rod for your own back with using VMs for audio? They are never going to give you the perform of bare metal.

Reminds me. I must figure out NFS so I can port my music over to the server. The thought of accessing it via SFTP is fills me with shame.

---

