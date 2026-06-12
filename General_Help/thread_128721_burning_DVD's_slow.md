---
title: "burning DVD's slow"
date: 2006-02-12
forum: General Help
---

### Post by moose6589 on 2006-02-12
I have been trying to burn DVD's with k3b, but it doesn't seem to ever burn at full speed. My burner and k3b both say it supports 16x burning, and on Windows, I could burn at 12x or more consistently. On Ubuntu, however, my DVD burning speed tops out at 4x and often drops to 1-2x, even when I set it to 16x. CD burning is fine, but the transfer rate there is much lower as well compared to DVD. 

I have, of course, enabled DMA, but the problem still persists. Has anyone had any success burning at faster speeds? It currently takes about 18 minutes to burn a full DVD (compared with 5-6 minutes for Windows). Incidentially, Nero on Linux also burns at the same slow speed, so it is not k3b's fault. 

My burner is a NEC 3520A, if that helps.

---

### Post by z_diver on 2006-02-12
[QUOTE=moose6589] Has anyone had any success burning at faster speeds? It currently takes about 18 minutes to burn a full DVD (compared with 5-6 minutes for Windows). [/QUOTE]
I burn DVD's using gnome's built in burner.  Iso images take 5-7 minutes for a 4+ gig disk.  Before I enabled DMA it took about 10 to 15 minutes which I felt was a little slow.  

hdparm -i /dev/hdd shows it's a SONY DVD RW DW-Q30A which is rated at 16x.

---

### Post by moose6589 on 2006-02-13
Well, I really don't think burning with Gnome's built-in program will help; both k3b and Nero are slow. Furthermore, my burner is also rated at 16x, so what could be the problem?

---

### Post by frodon on 2006-02-13
You should check if your DMA is enabled, it's often the problem is this case :  [http://doc.gwos.org/index.php/DMA](http://doc.gwos.org/index.php/DMA)

---

### Post by ssstrx on 2006-02-13
sudo hdparm -d1 /dev/hdc 
replace hdc with whatever the dvd device is eg. hdb, hdc,hdd etc

---

### Post by z_diver on 2006-02-13
The OP mentioned DMA was set already.  Here are the full specs from hdparm -i

Model=SONY DVD RW DW-Q30A, FwRev=YYS1, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2
 AdvancedPM=no
 Drive conforms to: device does not report version:

 * signifies the current active mode

---

### Post by digitalsy on 2006-02-13
I have a NEC 3550A and I'm having the same problems. DMA is enabled, but burning a full DVD (iso) takes approx 8+ minutes. I just tested it in windows and it took 5mins, unbelievable. I love my new rig, just wish linux would burn at FULL SPEED also. What gives?

---

### Post by stfriesen on 2006-02-15
I have a PIONEER DVD RW DVR-109 16x same problem.  Only burns at 4x.  DMA is on.

---

### Post by 8bit on 2006-02-19
[QUOTE=digitalsy]I have a NEC 3550A and I'm having the same problems. DMA is enabled, but burning a full DVD (iso) takes approx 8+ minutes. I just tested it in windows and it took 5mins, unbelievable. I love my new rig, just wish linux would burn at FULL SPEED also. What gives?[/QUOTE]

I just purchased the same drive. I'm getting around 25x on CDR when it should be 40x and around 7x when it should be 16x for dvd-r.

dma is enabled.

---

### Post by Valavien on 2006-02-21
This isn't very helpful.  but I have the same issue with my LG dvd burner and Asus cdrw

---

### Post by Valavien on 2006-02-22
Just read in another post with this topic that people have had luck by installing xcdroast and then installing the dvd ripping stuff.

---

### Post by 8bit on 2006-02-25
Has anyone had any luck fixing this issue?

Thanks,

---

### Post by moose6589 on 2006-02-26
I guess it must just be a natural problem/bug with Ubuntu then if there are truly no solutions. Does anyone know if there is a bug report on this or if Dapper will improve on burning performance?

---

### Post by lotheac on 2006-02-27
I also noticed this problem, my DVDs only burned at around 4x. Then today I burnt a CD with two files on it, the other from a NTFS partition and other other from my home dir (ext3). The file on the NTFS partition burnt at 25x or so speed but the latter half of the burn got 40x which is how fast it should've been. So I did some testing:
> $ hdparm -d /dev/hda

/dev/hda:
 using_dma    =  1 (on)

$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   3488 MB in  2.00 seconds = 1743.39 MB/sec
 Timing buffered disk reads:  164 MB in  3.00 seconds =  54.64 MB/sec

$ sudo hdparm -tT /dev/sda[35] /dev/sda[35] /dev/sda[35]

/dev/sda3:
 Timing cached reads:   3580 MB in  2.00 seconds = 1789.38 MB/sec
 Timing buffered disk reads:  104 MB in  3.06 seconds =  34.03 MB/sec

/dev/sda5:
 Timing cached reads:   3276 MB in  2.00 seconds = 1636.61 MB/sec
 Timing buffered disk reads:  168 MB in  3.01 seconds =  55.80 MB/sec

/dev/sda3:
 Timing cached reads:   3344 MB in  2.00 seconds = 1670.58 MB/sec
 Timing buffered disk reads:  104 MB in  3.05 seconds =  34.05 MB/sec

/dev/sda5:
 Timing cached reads:   3392 MB in  2.00 seconds = 1695.41 MB/sec
 Timing buffered disk reads:  168 MB in  3.01 seconds =  55.80 MB/sec

/dev/sda3:
 Timing cached reads:   3120 MB in  2.07 seconds = 1507.48 MB/sec
 Timing buffered disk reads:  102 MB in  3.00 seconds =  33.97 MB/sec

/dev/sda5:
 Timing cached reads:   3516 MB in  2.00 seconds = 1756.51 MB/sec
 Timing buffered disk reads:  168 MB in  3.01 seconds =  55.79 MB/sec

where /dev/hda is my optical drive, /dev/sda5 an ext3 partition and /dev/sda3 an NTFS partition. Just a thought.

---

### Post by 8bit on 2006-03-06
I was burning fine with my Plextor drive. It was an 8x dvd burner and it burned at 8x. Then it started acting up so I bought a new NEC drive. It works but burns at about 8x for dvd's and 26x for cd's when it should be  burning at 48x.

I wonder if there is a conflict with the apps k3b uses and the new kernel. Things didn't start happening with me until after I updated the kernel.

This sucks..

---

### Post by skaboss on 2006-05-01
This good old issue still remains...    ](*,) 
It seems that we are lots of users having this problem, so please if someone from ubuntu team reads this thread, please solve it !
My NEC x16 DVD burner burns at really slow speed, and i never found the solution...

Hope it will be better with Dapper...

---

### Post by robert114 on 2006-05-03
Well i'm in dapper and burning is still very slow :(

---

### Post by robert114 on 2006-05-03
Well this did the trick for me!
[http://k3b.plainblack.com/message-board/k3b-burns--4x-with-8x-burner--too-slow](http://k3b.plainblack.com/message-board/k3b-burns--4x-with-8x-burner--too-slow)

succes!

---

### Post by skaboss on 2006-06-02
Failure here....
Still > 25 minutes to burn a DVD (with a 16x NEC burner).

---

### Post by robert114 on 2006-06-03
Can you trie to disable any network connectivity while burning....

maybe your DVD burner and network card share the same irq wich is maybe slowing down the burning proces as it did for me!

---

### Post by habrys on 2006-08-06
This worked for me:
sudo hdparm -d1 -c1 /dev/cdrw

It turned out, that DMA (-d1) was already enabled on my system, but 32-bit IO (-c1) wasn't. This caused burning of DVDs wit the approx. speed of 1-1.2x. After enabling it I get 4x speed, which is max for my NEC.

---

### Post by relgar on 2006-08-12
FWIW, I found that having my burner and my single Linux disk together on the same IDE channel (i.e. attached to the same cable) to be the problem.  For both I had DMA enabled, 32-bit enabled, and it was burning at 1x.

I moved all the data in-kind to another hard drive on the other IDE channel, leaving the old hard drive and burner in place (i.e. I didn't open up the box).  Booting off the new location, it now burns at full speed (4x).

Some gueses:

- My new setup is "exclusively" reading data from one IDE channel and writing to another IDE channel.  Perhaps when they shared the same channel, the IDE controller had to use the channel to read some data from the disk, then stop reads so that it could use the channel to write it back out to the burner.  Doesn't make sense, though, as I *thought* that one could instruct the disks to talk to each other directly without a middle-man, but it's been awhile...

- There's some non-obvious side effect or operation to burning that's hitting the primary disk (root or swap) so that multiple operations with different destinations are interleaved on the IDE channel, preventing it from getting a good "run" of high throughput.

Interestingly, with my original, slow configuration, I noticed that occasionaly the burn would peak to 4x for about 5 seconds, then drop back to 1x... and then peak again some while later (a minute or two?).

Hope those details help someone; I'm just happy to be able to  burn at reasonable speeds again.

---

### Post by liberona on 2006-08-27
anyone got a solution yet? i have dma enabled and 32 bit enabled and i get really slow speeds like 3 -4 for dvd and i have a 16x burner... i got 16x in windows xp... whats goin on here? thanks for any info

---

### Post by foxy123 on 2006-09-02
Got the same problem. Following the link for k3b solution gave me some boost but still it takes around 14 min to burn a DVD.

---

### Post by finite9 on 2006-09-21
Just want to add my 2 cents:

I have an Acer Aspire 5021WLMi which houses a 16x dual layer DVD burner.  I run Dapper 6.06 with kernel 2.8.15-25 and i'm burning with Gnomebaker--version in the repos.

I have discs that are rated at 16x and no matter how I burn them, it goes at 2x exclusively.

In Windows XP on same laptop, using same media and same source material, I can burn at 16x using Nero Express 6.

As most burner apps use the same underlying utility (cdrtools?) to burn I would assume its an issue with that rather than the GUI front end.

---

### Post by foxy123 on 2006-09-21
has anyone tried to burn cd/dvd from console using a backend?

---

### Post by finite9 on 2006-09-21
well, I can confirm that Habrys solution works fine!

sudo hdparm -d1 -c1 /dev/hdc

sets DMA and 32-bit IO on the CD/DVD-RW drive

Ubuntu defaults to 16-bit--a very conservative decision, which they seem to take with all performance related things for max compat. on older h/w. :(

sudo gedit /etc/hdparm.conf allows you to edit the samples at the end of the config file...there is one for hda and one for cdrom, and I suggest un-commenting both of these and verifying that you have the correct device name.  In my case it's /dev/hda and /dev/hdc.  I used the commands in the sample and set io32_support = 1 on both of them.  Reboot and run 'sudo hdparm /dev/hdc' to verify that DMA and 32-bit is actually enabled.

After doing this, I could burn CD-RW 12x media at 9.9x average and a 4.7GB TDK DVD+R took 15 minutes at 8x (I don't have and 16x media at the moment).

Obviously, you need a fairly new (last 5 years or so) CD/DVD-RW ATA drive.  If you don't have hardware that supports 32-bit then setting this won't help.

---

### Post by xmastree on 2006-09-23
How would one make that the default? I know how to enable DMA by editing hdparm, but hou do you enable 32 bit?

Oh, and something which made me laugh. I found this thread because I was having the same problem. I couldn't write CDs at more than 4x.

Nothing worked, DMA, 32bit, still stuck at 4x.

Eventually, I decided to se what the drive ought to be capable of, so I looked it up...

[http://www.shopping.com/xPF-LG_CED_8083B_CED_8083B](http://www.shopping.com/xPF-LG_CED_8083B_CED_8083B)

:oops:

---

### Post by finite9 on 2006-09-23
xmastree:  I mentioned in my post how to make default...

sudo gedit /etc/hdparm.conf

scroll down to the samples at the end of the config file...there is one for hda and one for cdrom.

remove the # sign from the sample for /dev/hda and /dev/cdroms/cdrom and rename the /dev/cdroms/cdrom device name to that which you use (probably /dev/hdc).

There is a parameter within the sample called "io32_support = 0".  Change the value to 1 and you're all set.  Reboot and do sudo hdparm /dev/hdc to check that its set to 32-bit.

By the way, you come from Burnley?  Small world--me too :)

---

### Post by xmastree on 2006-09-23
> **finite9 said:**
> xmastree:  I mentioned in my post how to make default...
Ahh yes, so you did. And to be honest, looking at the samples it ought to have been obvious to me anyway... :rolleyes: 

I think I was too busy kicking myself for my other error.

> By the way, you come from Burnley?  Small world--me too :)
Yep. For a while I was based in the Philippines, but now I'm back.

---

### Post by liberona on 2006-09-24
i have enabled dma and io32bit and i still get less then 4x .... my drive is 16x and my discs are also and in windows on this same machine in nero i get 16x burning... whats goin on with the burning speeds in ubuntu?

---

### Post by Giggity on 2006-09-26
It looks like the developers are just too busy lately, but I thought I'd chime in anyway:

My Lite-On DVD burner does okay as long as I'm doing absolutely nothing else with the computer.  It burns at 10-11X as long as everything else is inactive, but drops to about 3-4X when I do simple tasks such as web browsing while burning.  It seems that the FIFO buffer empties a lot when I do stuff like that, which causes the speed to drop since the buffer needs to refill to continue burning.  This is especially annoying given that 10X translates to about 10 minutes for a full DVD, and when I'm doing major backups, I tend to burn about 20-30 DVDs, which would mean I can't use the computer for anything else for upwards of 5 hours!

This *never* happens when I'm in Windows using Nero, Alcohol or whatever.  Burning CDs/DVDs works so well in it that I have to do something retarded like defrag my hard drive while burning to cause this big of a drop in speed.

I really hope that the Ubuntu developers can find a way to fix this seemingly simple, but apparently very complex, problem.  Ubuntu is the only distro I've encountered (I've only used a few) that offers wide-ranging functionality with an easy learning curve, and so I consider it the best hope that Linux has of snatching the significant (20+ percent) portion of the desktop market necessary to compel more companies to offer Linux-compatible software.

It's a shame, but I bet that little things like this are alienating a great deal of users who lack the patience required to wait several months for a fix... sending them back to Microsoft for a couple years before they regain the adventurousness needed to try Linux again.

And yes, DMA and 32-bit IO are enabled on my DVD burner. ](*,)

---

### Post by GuiGuy on 2006-09-27
> **Giggity said:**
> It looks like the developers are just too busy lately, but I thought I'd chime in anyway:

My Lite-On DVD burner does okay as long as I'm doing absolutely nothing else with the computer.  It burns at 10-11X as long as everything else is inactive, but drops to about 3-4X when I do simple tasks such as web browsing while burning.  (*,)


Tell me about it. DVD burning (and I'm suspecting HDD file I/O as well) seems notoriously slow on Linux. In my experience it is not just Ubuntu - I've had the same issue with Mandrake & Suse distros.

The best I can manage on my 16X DVD burner on very smart hardware, tweaked with every tweak I can identify, is **1.68** - occasionally, and as you say when the PC is idling, K3b or whatever will have a rush of blood to the head and freak out somewhere near 3.8X:confused: 

I find it is faster to transfer 4G of files across the network to a SLOWER WinXP machine and burn there. Some things Windows just does better.

<sigh> - I feel a little better now ;) but see no solution.

regards

---

### Post by Giggity on 2006-09-28
Hmmm... that seems waaaay too slow to just write it off as unsolvable.  I'm sure someone in here has a solution that will bring it up to the same speed that I can get at least.

Also, DVD burners have only relatively recently become affordable mass-market items.  I'm confident that someone will find a workable solution to address the buffer underruns when other apps are being used... a volunteer network just needs time.

I have enough free time... perhaps I should cultivate some programming skills myself.

---

### Post by arthur_kalm on 2006-09-30
I have the same problem here. I have an LG GSA-4160B, 16x. Max I get is 4x. The strange thing is that a while ago (maybe 6 month), I was able to burn 8x with 8x DVDs. Now the max it will go is 4x. Very frustrating :(

And yes I have both DMA and the IO thing enabled. ](*,)

---

### Post by Helldesigner on 2006-10-01
Count me in. Ubuntu 6.06 Dapper Drake, LiteOn DVD Writer - SOHW-1633S with BS0Y firmware. Beautiful 16x writes under windoze (using Verbatim 16x DVD+R blanks). Under Ubuntu - 2x is total maximum I can get (with same blanks). No freakin' idea what's going on. I have followed every tutorial there is out there. I've been tweaking hdparm several times - no luck. Here's what it looks like right now:

```
/dev/hda:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    =  8 (on)
 HDIO_GETGEO failed: Invalid argument

```

I used this syntax to get it:

```
hdparm -d1 -c1 -a8 -u1 -Xmdma1 /dev/hda
```

And here's my hdparm -i output:

```
/dev/hda:

 Model=LITE-ON DVDRW SOHW-1633S, FwRev=BS0Y, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 *mdma1 mdma2
 UDMA modes: udma0 udma1 udma2
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-5

 * signifies the current active mode
```

This really sucks :/ I'm not sure there's much I can think of to bring my writer to its full speed - the one I get under win. Anyone - any ideas?

---

### Post by barranco on 2006-10-01
I did not know thi was such a huge deal, I've been trying to resolve this problem since I bought my linux box a DVD-RW.

I'm not as slow though as others my max speed goes up to 6x, but hey this is so annoying when I can burn at 16x under windows, with the same drive and media.


```

 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```

```

 Model=LITE-ON DVDRW SHW-160P6S, FwRev=PS0A, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 sdma? mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode

```

I think for now I'm just gonna assume BURNING AT 16X IT'S NOT POSSIBLE UNDER LINUX, yes I know there's people that can burn at 16x but I mean, this is the kind of things that won't let me completely switch to linux, there is only a number of hours I should and will spent to resolve this type of problems and it's well beyond the hours spent by a regular user and don't even mention watching encrypted DVD's pal!

---

### Post by finite9 on 2006-10-02
I think it's really hard to resolve this kind of issue in a forum--it needs a bug report, and as far as I can tell, no one has submitted one (at least no one has posted the bug number in this thread).

I have followed and added to this thread and one thing has become apparent...It is easy to say "this works in windows, but not in linux" without *actually* testing it in windows!  You might think 'hmm, yeah, i remember doing this 3 months ago' but in actual fact remember wrongly.  I know this from personal experience.

So first things first:

Does your drive support the speed you expect with a given media type?  Have you verified this with the manual?

Does your *media* truly support the same speed *on your drive*?  I ask because I have 16x drive but many 16x media do not burn full speed on my drive due to firmware limitations--true of many drives.  You need to verify this on Windows first before posting that 'it works in windows'!

Do you have DMA and 32-bit enabled on the correct device in Ubuntu?  Won't help if you enabled it on hda when your optical drive is hdc!

Which program are you using to burn in Ubuntu?  Could be other issues with the program you use that aren't related.

I know they may seem like very basic questions, but it's easy to write statements on a forum without thinking.  The posts here are just too random to say with any clarity that xyz doesn't work at all and needs fixing: many people can write high speed, so it may be a question of certain drives not being fully supported.

As enabling 32-bit fixed my problem, it is not possible for me to open a bug report, as it is nothing I can verify.  One of you who still has the issue after trying all these tips should open a report, so it gets looked into, instead of this thread just inevitably dying out.

---

### Post by Helldesigner on 2006-10-02
First, I think it's rude to assume that people trying to solve their problems on this forum do not think. 

Second - I can't speak for others, but I personally have just switched (fully) to Ubuntu after using Win XP on daily basis (and I'm not talking about gaming here) for quite few years (I've been using Win2k, Win98, Win95  before). During that time I have burned hundreds DVDs in several applications, so I think I can tell how fast my writer can be. In windows, burning 16x Verbatim blank took no more than 10 minutes. Right now, in Ubuntu, it takes more than 30 minutes, sometimes even more. And it does not matter which program am I using - K3b, Bonfire (Brasero now I think) or anything else. Average speed does not go above 2-3x. Period. 

However, let me answer your questions one by one:

> Does your drive support the speed you expect with a given media type? Have you verified this with the manual?

Yes it does. I know what I buy. As I said, I've got [SOHW-1633S ]("http://www.liteonit.eu/index.php?option=com_content&task=view&id=36&Itemid=67&limit=1&limitstart=1") with BS0Y firmware, which allows burning DVD+Rs with 16x speed. And so it does - under win. Not in Ubuntu, though.

> Does your *media* truly support the same speed *on your drive*? I ask because I have 16x drive but many 16x media do not burn full speed on my drive due to firmware limitations--true of many drives. You need to verify this on Windows first before posting that 'it works in windows'!

I do not use cheap no-names. Only Verbatims. And they DO work great. In windows.

> Do you have DMA and 32-bit enabled on the correct device in Ubuntu? Won't help if you enabled it on hda when your optical drive is hdc!

I know how my drives are connected, 'cause I built my PC. However to avoid any mistakes, probing /dev/dvd should give true readings, right?

```
/dev/dvd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    =  8 (on)
 HDIO_GETGEO failed: Invalid argument
```

> Which program are you using to burn in Ubuntu? Could be other issues with the program you use that aren't related.

Doesn't matter. All of them burn full DVD (4GB) longer than 30 mins on my machine - Nero, K3B, Brasero.

> many people can write high speed, so it may be a question of certain drives not being fully supported.

If there is someone who can burn DVDs in one of the mentioned apps with 16x speed -- PLEEEASE! Post your writer data and hdparm output! I would really like to see it.

> One of you who still has the issue after trying all these tips should open a report, so it gets looked into, instead of this thread just inevitably dying out.

Ok, so where can I do that? I would gladly open such a bug report. This is really a pain in the ***. I'm using Ubuntu as my primary OS for quite some time now - and not just for fun, but for webdev too - and the DVD writer issue is the only thing that makes me angry about Ubuntu.

**UPDATE**: Ok, nevermind about filing a bug. [Here it is]("https://launchpad.net/distros/ubuntu/+source/k3b/+bug/31709"). And here is a [second one]("https://launchpad.net/distros/ubuntu/+source/dvd+rw-tools/+bug/52666") (actually, these bugs should be merged, as it is not K3b problem for sure - well, at least not K3b alone)- as you can see, there are quite a few people having this problems out there.

---

### Post by adaman on 2006-10-21
Hi 
I have same problems with Benq DW1670. When i switch write speed to 4x in K3b, it burns max 2x. With auto speed i got max 0,9x. dma and 32-bit are enable.  CD's are burning with normal speed.
there are no problems under windows xp.

does anyone solve this problem??

---

### Post by theslut on 2006-10-22
I have been saying for ages that Linux dvd burning is not as good as windows and is inconsistent.

Using any free app like k3b, brasero, or the gnome based burners, i cannot get a disc to write at 16x (which takes 5-8 minutes on Windows). DVD burning takes 15-20 minutes on these Linux apps.

Interestingly, Nero Linux burns DVDs much closer to speeds replicable in Windows. It seems that Nero uses its own API base to control the burn process while the free linux apps all use the same enginge.

I have also found that setting my burner to Master and not Slave or CS has improved the transfer rate but not made it full speed.

At best, I should be able to burn a DVD in 6-7 minutes with the media and burner I have.

---

### Post by GuiGuy on 2006-10-24
> **theslut said:**
> I have been saying for ages that Linux dvd burning is not as good as windows and is inconsistent..

As I sit here and watch K3b on my 16X burner running on a 3000+ Athlon XP with 2G RAM struggle to achieve 1.7X burning speed, I have to agree.

It does seem hopeless :(

---

### Post by foxy123 on 2006-10-24
> **GuiGuy said:**
> As I sit here and watch K3b on my 16X burner running on a 3000+ Athlon XP with 2G RAM struggle to achieve 1.7X burning speed, I have to agree.

It does seem hopeless :(
well, 1.7x is too slow even for Linux. I have around 4x on NEC3500A for 16x media. Funny enough k3b shows 16x in its info window, but actual speed, which is shown in the main window always around 4x.

---

### Post by GuiGuy on 2006-10-24
> **foxy123 said:**
> well, 1.7x is too slow even for Linux. I have around 4x on NEC3500A for 16x media. Funny enough k3b shows 16x in its info window, but actual speed, which is shown in the main window always around 4x.

In my case K3B always identifies the DVD burners correctly (I have tried several makes). However the burning speed, indicated at the bottom left, is generally around 1.68x :( 

I have exhausted every smidgeon of advice and text I have been able to find on this subject. I have spent so much time on this issue that I have to conclude there is a major flaw in the OS when it comes to burning DVDs and CDs. Note that I had the same problem on Mandrake & Suse distros.

ANyway, I gone back to Windows to do most of my multimedia and burning tasks. There are some things it does much better. Shame, really... <sigh>

---

### Post by Magnes on 2006-11-06
The same here. Lite-ON 16x. 12-15 minutes burning with max. 6x.

---

### Post by robert114 on 2006-11-06
Still with edgy?

The performance of burning DVD's has increased to the maximum capable by my hardware since I installed Edgy!

I hope I'm not the only lucky one!

---

### Post by a6jarvi on 2006-11-07
> **relgar said:**
> FWIW, I found that having my burner and my single Linux disk together on the same IDE channel (i.e. attached to the same cable) to be the problem.  For both I had DMA enabled, 32-bit enabled, and it was burning at 1x.

Well, that sounds just like my problem: (according to the HDD led and DVD drive led) the hard disk reads for about 3 secons, then stops and then the DVD burner burns the data to the DVD and so on. And the speed is marvellous 0,60X. :evil:
My burner is also attached to the same cable as my HDD and both have DMA and 32-bit support enabled.

I used Verbatim 16X DVDs and the burner is Samsung SH-S182D/BEBN which is capable of burning DVDs @ 18X.

Oh well, 52 minutes for burning 3,9 Gb of data...  ](*,)

---

### Post by foxy123 on 2006-11-07
> **robert114 said:**
> Still with edgy?

The performance of burning DVD's has increased to the maximum capable by my hardware since I installed Edgy!

I hope I'm not the only lucky one!

I wonder if anyone else experienced any improvement of CD/DVD burning speed after upgrading to Edgy. BTW, what is you hardware spec?

---

### Post by robert114 on 2006-11-08
AMD x2 4600
Nvidia MB nforce5 chipset
1GB memory
(upgraded bios)
Lite-on burner

---

### Post by GuiGuy on 2006-11-09
> **foxy123 said:**
> I wonder if anyone else experienced any improvement of CD/DVD burning speed after upgrading to Edgy. BTW, what is you hardware spec?

YES!!! :D Burning between 12X to 15X (16X Pioneer). 

However, I flunked the Edgy update- total disaster. Kiddies, do not attempt the upgrade unless you have a fall back strategy.

I finished up having to do a new install and then restored my home.

There are a few issues to sort out, but so far so good.

---

### Post by dannyboy79 on 2006-11-09
man, you guys are lucky, i can't even burn dvd's in linux, i have been trying to burn an .iso file ever since I started using linux in march. ubuntu is my first distro ever. i have tried dma, different media, it's on it's own ide channel and set as master. any other suggestions would be great. i have tried nerolinux, k3b, nautilus, gnomebaker.

---

### Post by GuiGuy on 2006-11-10
> **dannyboy79 said:**
> man, you guys are lucky, i can't even burn dvd's in linux, i have been trying to burn an .iso file ever since I started using linux in march. ubuntu is my first distro ever. i have tried dma, different media, it's on it's own ide channel and set as master. any other suggestions would be great. i have tried nerolinux, k3b, nautilus, gnomebaker.

When you say ¨can even burn¨, can you be more specific?  For example, what what happens when you commit the burn?

---

### Post by artisan on 2006-11-10
I tried burning a dvd with K3b and K9copy. It took a fantastic four hours to get an ISO copy onto my hard drive and then I got magnificent burn speed of 0.
](*,) 
I've had a few problems withn Ubuntu, with the updates not so long ago, and I still don't have flash 9.
But I do not intend to go back to windoze. So if someone could suggest a working solution besides funking with DMA 'cause my machine is older than 3 years, it would be appreciated :-?

---

### Post by foxy123 on 2006-11-10
I have installed backported cdrtools but have not tried to burn anything yet. I will let you know if I have any improvement.

---

### Post by robert114 on 2006-11-10
> **artisan said:**
> I 
I've had a few problems withn Ubuntu, with the updates not so long ago, and I still don't have flash 9.


Ubuntu proberbly doesn't distribute the flash player for Dapper and Edgy you can manually download the player here:
[http://labs.adobe.com/downloads/flashplayer9.html]("http://labs.adobe.com/downloads/flashplayer9.html")

Installing is simple (after you've removed the old flashplayer)
just put the libflashplayer.so file in /usr/lib/firefox/plugins/ 
Youre flash should work now!

---

### Post by dannyboy79 on 2006-11-10
> **foxy123 said:**
> I have installed backported cdrtools but have not tried to burn anything yet. I will let you know if I have any improvement.

since I am having problems burning dvd's, I tried installing the latest source of dvd+rw tools and that still doesn't work. I get i/o errors everytime and the one time it did work, the disc was bad. I am trying to burn xbox iso images onto dvd+r disc's.

What version of dvd+rw tools does ubuntu have by default?

Mine is 6.1, you can find out by doing this:
growisofs --version

the something like this will be spit out:
* growisofs by <appro@fy.chalmers.se>, version 6.1,
  front-ending to mkisofs: mkisofs 2.01-unofficial-iconv (i686-pc-linux-gnu)

---

### Post by GuiGuy on 2006-11-10
> **artisan said:**
> 
But I do not intend to go back to windoze. So if someone could suggest a working solution besides funking with DMA 'cause my machine is older than 3 years, it would be appreciated :-?

See my post above- I have had the ´slow burn´ issue for some time now across three Linux distros. But after installing Edgy DVD burning now occurs at something approaching maximum speed. I suggest that if you need performance burning, try and install Edgy.

---

### Post by foxy123 on 2006-11-11
> **dannyboy79 said:**
> since I am having problems burning dvd's, I tried installing the latest source of dvd+rw tools and that still doesn't work. I get i/o errors everytime and the one time it did work, the disc was bad. I am trying to burn xbox iso images onto dvd+r disc's.

What version of dvd+rw tools does ubuntu have by default?

Mine is 6.1, you can find out by doing this:
growisofs --version

the something like this will be spit out:
* growisofs by <appro@fy.chalmers.se>, version 6.1,
  front-ending to mkisofs: mkisofs 2.01-unofficial-iconv (i686-pc-linux-gnu)

In Dapper it is 5.21.4.10.8

---

### Post by pedrofdmp on 2006-11-11
i have the same problem
burning at 1x princo 4x media
all my drives have 32bit and dma enabled

XP2400
1.5gb ram
Plextor 755a

---

### Post by pedrofdmp on 2006-11-11
[http://forums.gentoo.org/viewtopic-t-292252-highlight-.html](http://forums.gentoo.org/viewtopic-t-292252-highlight-.html)

gentoo forums says it's a problem with the generic ide driver

i tried to remove the generic driver
modprobe -r ide_generic

and using the via one
modprobe via82cxxx

but still the same problem

---

### Post by pedrofdmp on 2006-11-11
problem solved using Nero Linux 

:(

---

### Post by foxy123 on 2006-11-12
> **pedrofdmp said:**
> problem solved using Nero Linux 

:(

I wonder what Nero has, which k3b has not.

---

### Post by xmastree on 2006-11-12
> **foxy123 said:**
> I wonder what Nero has, which k3b has not.

A price tag. :rolleyes:

---

### Post by foxy123 on 2006-11-12
> **xmastree said:**
> A price tag. :rolleyes:

well, yes, but I meant something that allows it to burn faster than Linux traditional tools.

---

### Post by pedrofdmp on 2006-11-12
this seems to be some kind of cdrtools growisofs bug

---

### Post by finite9 on 2006-11-13
Yepp, I blame the whole messy business on cdrtools and the DVD equivalent.  ALL the burning utilities for Linux use these two culprits as the back-end modules that actually burn the disc.  And it seems like there is a bit of friction between debian and the author of cdrtools.  Nero probably works fine because it uses it's own proprietary backend to burn the disc.

The sooner someone does a replacement for cdrtools the better.

---

### Post by Magnes on 2006-11-13
[http://perso.orange.fr/bonfire/features.htm](http://perso.orange.fr/bonfire/features.htm) - anyone tried using Brasero with libburn.pykix.org? Maybe that will help (I'll try it some day).

---

### Post by tanari on 2006-11-24
what Ubuntu developers say about this problem? Do they even know about this problem?

I bought new samsung DVD writer and it burns only at 0.8x speed!!!

Samsung SH-S162L
[http://samsung.com/Products/OpticalDiscDrive/DVDWriter/OpticalDiscDrive_DVDWriter_SH_S162L.asp?page=Specifications](http://samsung.com/Products/OpticalDiscDrive/DVDWriter/OpticalDiscDrive_DVDWriter_SH_S162L.asp?page=Specifications)

---

### Post by foxy123 on 2006-11-24
I backported dvd+rw-tools from Edgy and it had no effect on burning speed. I still need more than 15 min to burn a DVD.

---

### Post by Xceptiona1 on 2006-11-27
Is there a recommended DVD burning program for Ubuntu 6.10?

---

### Post by robert114 on 2006-11-27
As a Kubuntu user I can recommend K3b, but I do not know the Gnome equal

And I'm not sure weather you'll suffer from the performance bug were many people complained about! I use K3b without the performance bug... kubuntu 6.10

---

### Post by tanari on 2006-11-27
I can't enable DMA. 
I have added 

/ dev/hdd {
io32_support = 1
dma = on
}

to hdparm.conf

But DMA is off!

When I use sudo hdparm -d1 /dev/hdc DMA is ON, but after first mount/unmount it is set to OFF again ! :(.

---

### Post by xopher on 2006-11-27
> **Xceptiona1 said:**
> Is there a recommended DVD burning program for Ubuntu 6.10?

I can't tell you to use this, but I like it very much, its still not that stable though - Oh yeah, its called brasero.

K3b is probably the most widely used.

Gnomebaker is nice too, quite light-weight imo.

---

### Post by tanari on 2006-11-29
Nero also doesn't help :(. When DMA is off Nero ask to trun it On, but when DMA is On Nero can't start :(.
What can I do? Help please!

---

### Post by foxy123 on 2006-12-07
I have recently tried to burn on Windows and it took me half of time required on Linux. However despite the fact that my burner and the media support 16X, the speed was 8X. Linux gives me 4X, which is not as bad as I was afraid.

---

### Post by twistedneck on 2007-05-01
Same issue here, new samsung 18x dvd drive.. 32x enabled, DMA enabled, max speed 4.1x.

Ubuntu Feisty Fawn.

---

### Post by chalewa on 2007-05-01
> **twistedneck said:**
> Same issue here, new samsung 18x dvd drive.. 32x enabled, DMA enabled, max speed 4.1x.

Ubuntu Feisty Fawn.

are you sure that dma is actually enabled...

lots of people are having the same issue because /dev/hXX is now /dev/sdXX which doesn't work with hdparm

---

### Post by GuiGuy on 2007-05-02
> **chalewa said:**
> are you sure that dma is actually enabled...

lots of people are having the same issue because /dev/hXX is now /dev/sdXX which doesn't work with hdparm

Sorry for butting in, but I had posted elsewhere here that K3B v1 is, in my case, switching DMA off after the first burn. Further investigation has revealed that after the first burn, which happens at about 8X on a 16X device, DMA on ALL IDE devices including HDD is switched off.

Any ideas?

---

### Post by Syco54645 on 2007-05-02
i am glad that this got bumped.  i am tired of burning at 4x on my 16x burner.  i guess i will just get nero

---

### Post by GuiGuy on 2007-05-09
> **GuiGuy said:**
> Sorry for butting in, but I had posted elsewhere here that K3B v1 is, in my case, switching DMA off after the first burn. Further investigation has revealed that after the first burn, which happens at about 8X on a 16X device, DMA on ALL IDE devices including HDD is switched off.

Any ideas?

OK, none seemed to have an idea and I could find no obvious (read non-tedious) way of giving feed back to K3B team. 

I have tried every other free burning software for linux I could find and all were dreadfully slow. There is NO DOUBT that my hardware settings were correct until the situation outlined above occurs.
[B]
Yesterday I obtained the latest Nerolinux. I have now burnt several successive DVDs at the full potential of the burning hardware (16X). A full disc in around 7 minutes. Verification around 8 minutes. [/B]

I hope the slow burn issue, which has been a constant with me ever since I first tried Linux several years ago, is now fixed. For me, at least.


 regards

---

### Post by minoas on 2007-06-02
Same Problem here and its driving me insane.My Hdparam on the recorder is:

/dev/hdb:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

Im using SATA HDD and IDE DVD-RW.Although it says DMA is enabled ok K3b it takes ages to write a DVD.The most Bizzare thing is the internal nautilus tools writes in correct speed while NeroLinux3 works 50% of the times.Sometime it does a 16x Recording DVD  at 10 mins and some times at 20 mins...It gives an sd0 sda1 allert but NO DMA disabled allert.Also I tested it while gksudo and had no effect whatsoever..

The system is brand new Feisty installation will the updates included....

Any input is greatly appreciated.

---

### Post by GuiGuy on 2007-06-05
> **minoas said:**
> Same Problem here and its driving me insane.My Hdparam on the recorder is:

/dev/hdb:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on).

I am now using NeroLinux 3 - It works at full speed using my mix of Pioneer 110D (16x) and LG 8X burners. 

From my perspective, K3b and the other 'common' packages out there just don't work properly. Spend the few dollars and get NeroLinux 3 - or you can get the free trial (15 days) version here: 

[http://www.nero.com/ena/nerolinux-prog.html](http://www.nero.com/ena/nerolinux-prog.html)

It's easy to install too. 

regards

---

### Post by foxy123 on 2007-06-06
> **GuiGuy said:**
> I am now using NeroLinux 3 - It works at full speed using my mix of Pioneer 110D (16x) and LG 8X burners. 

From my perspective, K3b and the other 'common' packages out there just don't work properly. Spend the few dollars and get NeroLinux 3 - or you can get the free trial (15 days) version here: 

[http://www.nero.com/ena/nerolinux-prog.html](http://www.nero.com/ena/nerolinux-prog.html)

It's easy to install too. 

regards

some people do not like proprietary applications and still want to have full speed burning. :(

---

### Post by GuiGuy on 2007-06-06
> **foxy123 said:**
> some people do not like proprietary applications and still want to have full speed burning. :(

 That's the ideal, of course and I would have gladly donated the money to K3b or whatever if only they worked.

I have been trying for four years to get a decent rate of burn speed on CD & DVD drives on Linux. It started to annoy me that wherever I went for help the geeks told me it was a) Check your settings and b) you're to stupid to use Linux.

Paying $20 odd for NeroLinux may confirm I am stupid, but hey, it works. In the end that's what matters.


regards

---

### Post by minoas on 2007-06-07
Negative not even with Nero is the problem fixed.I have messed around with 2 diffirent spare computers and tried all Burning Software from Nautilus burner to Gnome Baker,Brasero and K3B and Nero.The situation is always the same.The first time you burn to a CLEAN Feisty installation you get normal speed 6-7 mins with my 16x recorder.Then its over.All burns from this point onwards take more or less 20 mins....

Im using an Sata Hdd and Ide DVD-RW.

_**UPDATE!!!**_

I have the issue fixed.Apparently it has to do with the way Kernel Handles Mixed Systems (Sata Hdd with Ide Drives)If you have that issue you may download Nerolinux Demo and try to run it.It should promt an error for not getting access to sg0 or sg1 drives.They are SCSI virtual drivers created on startup.To fix your speed do this trick

sudo gedit /etc/rc.local and add BEFORE the end line :P

chown root:cdrom /dev/sg0 (or sg1,2,... whatever your system is)

Save close reboot and enjoy ultra fast burning....

Tested so far on Nerolinux Braser and Gnome Backer.Im not gonna try on K3B...

ATM enjoying burning a DVD at 6mins :)

---

### Post by Pygi on 2007-06-10
Hello,

I'm the developer of the libburnia project, which may be visited at [http://libburnia-project.org](http://libburnia-project.org) and am working towards getting cd-recording just work in Gutsy. Brasero (Gnome cd-recording frontend) will use those libraries by default in gutsy, and everything should just work.

KR,
M.

---

### Post by hcuijpers on 2007-07-19
Hi All,

I first have to mention that i'm not an ubuntu user, but i use Debian Etch. I think the problems mentioned above are exactly equal to mine. SO i am having the same problems burning DVD's. 

I bought a samsung SH-S162L/RSBN That is a 16 speed DVD Writer. 
DVD+R & DVD-R both 16 speed 
DL DVD+R 8 speed and DL DVD-R 6 speed

At that time i was on windows XP and i burned at least 100 DVD's without a problem. I use only Philips DVD+R 16 speed Media. Always did. Always perfectly fine results. Not a single disc went to the trash can. Al discs burnt within 8 minutes...

Then (about 4 months ago) i made the move to Debian Etch (dual boot) and i started to trash one disc after the other. Burn speed is always around 0.8x. Sometimes i get a stunning 1.2-1.3x. Discs are all unusable in a standalone player. 

I tried every burn-program i can find. K3B, Gnomebaker, growisofs, wodim, nautilus CD/DVD creator, brasero.....  you name it i tried it. All with the same result: Disc straight to trashbin.  (I can't find a nero3linux download, so i did not try that one.)
@Pygi: Your suggestion does not compile at Debian Etch without upgrading a lot of lib's i don't want to upgrade. The last version i can get compiled is 4.4...

**Here comes my solution:** 
[I]I create the iso files on Debian (on my ext3 filesystem). When i have a bunch of them i (dual) boot into XP burn the images at 16x speed (around 6-7 minutes each) with nero straight from the ext3 filesystem. When done i reboot back into Debian and delete the iso-images.
[/I]**End of solution**

I would like to NOT boot into XP anymore because this is the only thing i need it for these days.

-- My config: (AMD Athlon 2800+ 3Gig Mem)
I have 2SATA hard-discs (sda & sdb) and 1 PATA (IDE) disk at the first IDE controller (hda) and the samsung burner is primary device on the second IDE (hdc). There is also an old NEC (ND-2500A) burner. That's a slave drive also on the second IDE. (hdd)

As u can see below io is at 32 bit, DMA is on, readahed is on and dma-mode is udma2 for both burners.

hdparm output:

amdtje:/home/henrie# hdparm  /dev/hdc

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
amdtje:/home/henrie# hdparm -i /dev/hdc

/dev/hdc:

 Model=TSSTcorpCD/DVDW SH-S162L, FwRev=TS02, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no

 * signifies the current active mode

amdtje:/home/henrie#

amdtje:/home/henrie# hdparm  /dev/hdd

/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
amdtje:/home/henrie# hdparm -i /dev/hdd

/dev/hdd:

 Model=_NEC DVD_RW ND-2500A, FwRev=1.06, SerialNo=
 Config={ Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no

 * signifies the current active mode

amdtje:/home/henrie#

---

### Post by isecore on 2007-07-27
> **minoas said:**
> Negative not even with Nero is the problem fixed.I have messed around with 2 diffirent spare computers and tried all Burning Software from Nautilus burner to Gnome Baker,Brasero and K3B and Nero.The situation is always the same.The first time you burn to a CLEAN Feisty installation you get normal speed 6-7 mins with my 16x recorder.Then its over.All burns from this point onwards take more or less 20 mins....

Im using an Sata Hdd and Ide DVD-RW.

_**UPDATE!!!**_

I have the issue fixed.Apparently it has to do with the way Kernel Handles Mixed Systems (Sata Hdd with Ide Drives)If you have that issue you may download Nerolinux Demo and try to run it.It should promt an error for not getting access to sg0 or sg1 drives.They are SCSI virtual drivers created on startup.To fix your speed do this trick

sudo gedit /etc/rc.local and add BEFORE the end line :P

chown root:cdrom /dev/sg0 (or sg1,2,... whatever your system is)

Save close reboot and enjoy ultra fast burning....

Tested so far on Nerolinux Braser and Gnome Backer.Im not gonna try on K3B...

ATM enjoying burning a DVD at 6mins :)

I tried this, but the only effect it had was making my CPU-load shoot through the roof as well as lowering my speed from ~4x to a constant less than ~2x. I'd much rather see DVDs burn at ~4x with almost no CPU load rather than the other way around.

I have no clue why this happened either. It seems rather odd that the rights to a virtual driver could have this much impact on performance.

---

### Post by LeX-333 on 2007-09-29
Same problem here, using Debian Lenny AMD64 with a TSSTcorpCD/DVDW SH-W162C DVD burner. I've tried burning with Nero and K3B to burn DVDs and got lots of buffer underruns resulting in an effective writing speed of about 0.4-0.8X. I've tried doing a reading benchmark using qpxtool and also noticed a maximum reading speed of about 2X, which is way to slow for my drive. Of course DMA is on.

**Possible solution**
My previous setup was:
/dev/hda -> DVD burner
/dev/hdb -> DVD reader
/dev/hdc -> (empty)
/dev/hdd -> IOmega ZIP drive
/dev/sda -> SATA hdd (Raid-0)
/dev/sdb -> SATA hdd (Raid-0)
This is not optimal, but basically I only used the burner and the /dev/hdc to sometimes connect a PATA drive.

I changed the PATA setup like this:
/dev/hda -> DVD burner
/dev/hdb -> (empty)
/dev/hdc -> (empty)
/dev/hdd -> DVD reader

With this setup K3B burned a DVD+RW at 4X and Nero burned a DVD+R at 8X without any problems. So it seems that having a second device connected to the same PATA channel as the DVD burner can completely wreck the perfromance of the burner. Maybe a kernel bug? The old setup worked fine under Windows.

I hope this helps someone here :)

---

### Post by cinamax on 2008-03-30
> **minoas said:**
> Negative not even with Nero is the problem fixed.I have messed around with 2 diffirent spare computers and tried all Burning Software from Nautilus burner to Gnome Baker,Brasero and K3B and Nero.The situation is always the same.The first time you burn to a CLEAN Feisty installation you get normal speed 6-7 mins with my 16x recorder.Then its over.All burns from this point onwards take more or less 20 mins....

Im using an Sata Hdd and Ide DVD-RW.

_**UPDATE!!!**_

I have the issue fixed.Apparently it has to do with the way Kernel Handles Mixed Systems (Sata Hdd with Ide Drives)If you have that issue you may download Nerolinux Demo and try to run it.It should promt an error for not getting access to sg0 or sg1 drives.They are SCSI virtual drivers created on startup.To fix your speed do this trick

sudo gedit /etc/rc.local and add BEFORE the end line :P

chown root:cdrom /dev/sg0 (or sg1,2,... whatever your system is)

Save close reboot and enjoy ultra fast burning....

Tested so far on Nerolinux Braser and Gnome Backer.Im not gonna try on K3B...

ATM enjoying burning a DVD at 6mins :)


Hello,

I'm having a simliar problem in Ubuntu GUTSY (7.10). I have a DVD-RW installed but it's using ide_cd drivers as per lsmod. My burn speed is at a pathetic x0.7 under k3b. However, my read speed is ultra fast. 

I checked hdparm -i and see that udma 32 bit, etc. are turned on just like yours. 

will chown root:cdrom /dev/dvdrw do the same trick for me as yours? Should I look into changing my ide dvdrw to use scsi emulation instead ?

thanks in advance please help

---

### Post by hcuijpers on 2008-05-19
I have a breaktrough!

Last month i bought 2 disks (SATA 500G). I took out all my other HD's and replaced them with the 2 new SATA500Gb.

That give's me place for my 2 burners each on a seperate IDE. So

sda: hd SATA 500G
sdb: hd SATA 500G
hda: burner 16speed (Samsung 16speed)
hdc: burner 2speed (Nec)

I now burn all my DVD's under Linux (Debian Lenny) @16 speed without having to trash 1 of them. 

Though it's no hard evidence: the burner alone on his own IDE solved my problem. (I believe it's already been said, but adding my experience might help someone.)

---

### Post by meeotch on 2008-06-16
I'm having a similar problem in Hardy.  When burning, both k3b and Nero cause the cpu load to shoot through the roof - so badly that I can't play music or do other light tasks, and even hitting the "cancel" button takes a while.  Burning speed shows as < 1.0x (4.0x if I run k3b as root) - but it's useless anyway, as the whole system is essentially locked up while it's burning.

"hdparm -i /dev/scd0" shows that udma1 is enabled on the burner and udma2 on the HDD.  Nero lists ata_piix as the adapter.

Unfortunately, I can't try putting the drive on its own IDE channel, as my SFF system only has one.  (The system drive is also on that channel, and the storage drives are on SATA.)

Drive seems to rip CD's fine (and fast) - haven't tried burning them, or ripping DVD's.

Anyone got bright ideas?

---

### Post by medic2000 on 2008-07-02
Bump!
Still slow on Hardy?

---

### Post by isecore on 2008-07-02
> **medic2000 said:**
> Bump!
Still slow on Hardy?

Yup, still get the same phenomenon. Burning a DVD, CPU-load becomes ridiculous to the point of other applications stalling until it's done.

---

### Post by GuiGuy on 2008-07-02
> **medic2000 said:**
> Bump!
Still slow on Hardy?

In my case I am realising about 50% speed on DVDs and CDs, i.e. on a 16x writer I realise ~ 8x. 

I've decided to live with it.

---

### Post by isecore on 2008-07-02
> **GuiGuy said:**
> In my case I am realising about 50% speed on DVDs and CDs, i.e. on a 16x writer I realise ~ 8x. 

I've decided to live with it.

Speed is actually decent for me. I also get ~ 8x speed. Which I'm fine with.

What irks me is that the CPU usage goes through the roof. I mean seriously, no multitasking on a quad-core? Applications stalling while at least three cores are working under full load just to burn a dvd?

It shouldn't be this way.

---

### Post by GuiGuy on 2008-07-03
> **isecore said:**
> 
What irks me is that the CPU usage goes through the roof. I mean seriously, no multitasking on a quad-core? Applications stalling while at least three cores are working under full load just to burn a dvd?

On my everyday desktop (Athlon XP (single core) 2800+) box I don't see excessive CPU load. In fact, yesterday I was banging away at an Openoffice document while K3b burnt a 4G data DVD.Not a hitch. 

But you have my curiosity aroused. My MythBuntu setup is Athlon 4800+ AM2 X2. I've never burnt a disc on it. Will try and post the result. 
 
regards

---

### Post by isecore on 2008-07-03
> **GuiGuy said:**
> On my everyday desktop (Athlon XP (single core) 2800+) box I don't see excessive CPU load. In fact, yesterday I was banging away at an Openoffice document while K3b burnt a 4G data DVD.Not a hitch. 

But you have my curiosity aroused. My MythBuntu setup is Athlon 4800+ AM2 X2. I've never burnt a disc on it. Will try and post the result. 
 
regards
I see it all the time. Wish I didn't. Writing speeds are decent (i.e. about 8x on an 8x disc) but the CPU-load is just ludicrous. It's not the application either (I prefer Brasero actually) but some low-level process or something that's difficult to find. All I see is the CPU-usage going through the roof, and even just surfing the web with Firefox or navigating with Nautilus easily stalls.

EDIT: For what it's worth, my system is an AMD Phenom 9500 with 4 gigs of RAM running Ubuntu x86-64. Harddrives are all SATA in an LVM-chain separate from the burner, which resides on it's own IDE-controller.

---

### Post by lachild on 2008-07-03
I get the same problem too.  I updated from backports and it seems to be slightly better, but my 16x cd burner is still only burning at 5-8x and the whole computer is still pretty much locked up during the burn.

This is also happening regardless of the application that I'm using to make the CD.  All the apps that I have found in the repo's all do the same thing.

Lachild

---

### Post by isecore on 2008-07-03
This is odd. I was checking the hdparm settings for my writer, making sure that DMA was enabled (which it was). I noticed that 32-bit IO support wasn't enabled (it was in 16-bit mode) and enabled that for the writer. DMA was already enabled, and none of the other settings had any effect - just got an error message about invalid argument.

This however didn't change a thing. Until after I rebooted. Noticed it was back to 16-bit, set it to 32-bit. And all of a sudden I can burn dvd's at high speed (~6-8x for an 8x disc) and with no noticeable CPU-load. In fact, the computer runs just fine when burning. No stalling, no laggy responses.

Weird.

---

### Post by lachild on 2008-07-03
You nailed my problem right on the head.  However in my case I don't know how to fix it.  It seems that mine is also reading in 16 bit, but I also noticed that DMA gets disabled at startup.  

Here's my dmesg that shows the problem...  If anyone has an idea how to fix this please let me know.

```
[   13.411777] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, 1.02, max MWDMA2
[   13.411793] ata2.00: simplex DMA is claimed by other device, disabling DMA
[   13.583478] ata2.00: configured for PIO4
[   13.583600] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVE-0 01.0 PQ: 0 ANSI: 5
[   13.588253] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4244N 1.02 PQ: 0 ANSI: 5
[   13.595274] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   13.595282] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   13.608617] Driver 'sd' needs updating - please use bus_type methods
[   13.608705] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   13.608717] sd 0:0:0:0: [sda] Write Protect is off
[   13.608720] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.608736] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.608780] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   13.608788] sd 0:0:0:0: [sda] Write Protect is off
[   13.608790] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.608803] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.608808]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   13.649722]  sda1 sda2 sda3
[   13.680396] sd 0:0:0:0: [sda] Attached SCSI disk
[   13.687456] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   13.687475] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   13.701925] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   13.701931] Uniform CD-ROM driver Revision: 3.20
[   13.701984] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   14.090353] Attempting manual resume
[   14.090357] swsusp: Resume From Partition 8:3
[   14.090359] PM: Checking swsusp image.
[   14.090672] PM: Resume from disk failed.

```

Thanks in advance

---

### Post by lachild on 2008-07-03
Ok I was able to fix it following the instructions in [this post]("http://http://ubuntuforums.org/showthread.php?t=760121").

> So I blacklisted ata_generic and added pata_atiixp to /etc/initramfs-tools/modules
Code:

pata_atiixp
blacklist ata_generic

and recreated the initramfs with
Code:

sudo update-initramfs -u

and, after a reboot, the speed was better: 

Not only did this fix my DMA problems but I noticed an overall performace boost across the board.

Hope this helps someone else.

---

### Post by !nkubus on 2008-07-18
It helped me for about 2 burning sessions now it's back to the old behavior, which my cd's wont auto mount, and hangs when I want to burn.

What on heart Hardy is doing with cdroms.

---

