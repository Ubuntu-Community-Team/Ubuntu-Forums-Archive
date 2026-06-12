---
title: "Contemplating a new system... many ?s"
date: 2006-03-23
forum: General Help
---

### Post by robenroute on 2006-03-23
Hi there, all of you.

I'm currently running Breezy on my ASUS (L3800C) laptop. I haven't touched XP for quite a few months now, and I'm perfectly happy. Of course, I wouldn't mind getting my video-out working, but having it not working isn't a showstopper for me. Sound works, network (DSL) zooms, external firewire drive hums merrily, no accelerated graphics (but I'm not a gamer, so I really don't mind). Happy as a lark, I'd say. However, my laptop is aging; the battery is dead (or should I say, incontinent?), the CD-RW is just that (no DVD-RW), USB is a-w-f-u-l-l-y  s-l-o-w, it's all starting to creak and squeak, so to speak.

So, time for a new system, a desktop-ish system. Looking at the possibilities of building my own system, I ran into a slight problem: a million and a half motherboards to choose from (of course, none indicated by the manufacturer as Linux compatible, but that goes without saying....) What on earth should I choose? Of course, I've checked the Ubuntu hardware compatibility docs, but there are a mere 10 motherboards mentioned. I've also looked on the Internet in different forums and on several hardware sites, but I cannot seem to find what I'm looking for (a lot of the recent motherboard attention goes to SLI and PCI-e, which I don't really need). Well, I was hoping some of you might throw me a hint or two. So, here are my requirements:

- on-board LAN (but not Marvel, because of problems with Ubuntu's skge, as I've heard/read)
- on-board, decent audio (no need for fancy, 8-speaker setups, though)
- on-board graphics with dedicated graphics memory (no shared stuff, please)
- no need for SLI or PCI-e (I'm no gamer)
- no need for SATA (but would be nice)
- on-board 1394a (or b)
- plenty of USB2.0 ports
- socket 478, 775, 939? dunno, but I know I want to run an i686 kernel of Ubuntu, because it seems there are lots of problems getting several codecs and flash to work on the 64-bit version of Ubuntu.
- budget around $120/100 euro (give or take a bit).

I really can't see the forest for the trees. I'm hoping some of you have recently built a nice, not too fancy system and have good experiences. I'll be very grateful, I promise ;) 

Or should I perhaps be looking at one of them Shuttle SFF boxes instead? Anyway, thanks a lot for any feedback.

Rob

---

### Post by bluevoodoo1 on 2006-03-23
Might not want to get a 478 socket. That's getting to be quite old (I have a 478...) and in the future upgrading your processor might not be easy, if it's even possible at all. Might want to look at the 939 socket. Like I said I have an Intel with the 478, but I think next system I'm going to go for an AMD. AMD's have some good "bang for the buck," and from what I've read around here, you can get a 64 bit processor and run the 32 bit (i686 kernel) version of Ubuntu on it without [many] problems [I think]. 

Anything you do, be sure to read up as much as you can about what you intend to purchase, especially in terms of compatibility with Linux.

---

### Post by robenroute on 2006-03-23
> and from what I've read around here, you can get a 64 bit processor and run the 32 bit (i686 kernel) version of Ubuntu on it without [many] problems [I think].

Can anyone confirm this? Is it completely transparent, running an i686 kernel on an AMD-64 processor? Are there no (potential) hiccups, hurdles or incompatibilities?

I see your point regarding the processor upgrade, but my own experience tells me that I never do this anyway. When it's time for an upgrade, I usually buy a new system. But, perhaps that's a little silly. Maybe I should think of a longer term investment... The idea of a 64-bit platform sounds very appealing, but at the moment, software support is not optimal. Hence my question about the compatibility of the AMD-64 processors running 32-bit software.

Thanks again.

---

### Post by damu on 2006-03-23
I have an AMD X2 3800+
motherboard : asus AV8 deluxe

I use 2 linuxx dstros: Ubuntu for everything and Studio-to-go for sound production.

Both Distros run on 32 bits without any problem.

I have on big issue though with Ubuntu (which is probably specific to my hardware configuration). To use the 2 cores of my proc, I need to update the kernel to an smp kernel. When I try to boot from this kernel, it hangs (Win XP also crashes 5-6 times in a row before I can use it, which hardly ever happens now ... :) )

I don't have this problem with Studio-to-go, and I really hope Ubuntu Dapper will solve this problem.

Like you I don't want to use a 64 bit version because of the lack of compatibility of softwares.

---

### Post by NetMatrix on 2006-03-23
I would say to look into an Asus board with an AMD processor.

I use and FIC board with a Ath 1800+ and it works pretty good.  Asus has been around for a while and is very well known and widely used.

---

### Post by jbennett on 2006-03-23
I can't speak from personal experience (I haven't built my computer yet), but from the research I've done, it seems as though the ASUS boards are pretty solid, even with Linux.  I'm planning to build a box this summer (as soon as I have the money) and [this]("http://www.newegg.com/Product/Product.asp?Item=N82E16813131570") is the one I'm looking at.  It has PCI which I know you said you had no need for, but it also has onboard video, sound, firewire, USB and gigabit ethernet.  It's socket 939, which is compatible with the majority of newer processors (at least for AMD, I plan to purchase the AMD Athlon X2 3800+ processor).  Plus, the price is excellent.  $80 is great for this many features.

Hope this helps you.

---

### Post by robenroute on 2006-03-23
[QUOTE=jbennett].... and [this]("http://www.newegg.com/Product/Product.asp?Item=N82E16813131570") is the one I'm looking at....[/QUOTE]

First of all, thanks a lot for responding. Secondly, I would rethink this board if you're looking for ACPI support/compatibility. I also came across this board, but was quickly put off because of the following issue (which still haven't been resolved by ASUS):

- [http://www.nvnews.net/vbulletin/showthread.php?t=66102]("http://www.nvnews.net/vbulletin/showthread.php?t=66102")

Otherwise, it seems a very reasonable offering.

However, ASUS is not known for their personal support, nor their prompt fixing of things. Based on my own experience (and plenty thereof, I might add) and on that of others, one might conclude that smaller companies (MSI? Gigabyte?) often offer better support and quicker fixes to problems. Just my thoughts, really.

I'll keep an eye on the development of the aforementioned ASUS board and BIOS problem....

Thanks again.

Rob

P.S. I just noticed that the A8N-VM CSM features a Marvell network chip, and that seems to be causing a few problems here and there (currently unsupported by Ubuntu?).

---

### Post by jbennett on 2006-03-23
Thanks for the info robenroute.  I'll definitely take that into consideration when I make the final choices for my box.

---

### Post by ekarni on 2006-03-23
I suggest a top-down approach.  First, figure out what processor you want (after deciding AMD or Intel, cost tends to make this decision for you pretty quick!).  This will immediately narrow the field down to those mobo's with the correct socket.  Then go to a site like [Newegg]("http://www.newegg.com") with a good filter tool, and use that with your list of requirements.  You should narrow the field down pretty quick.  Then google them all, read any reviews you can find, look for gripes, maybe pull the PDF manuals off the company websites and see if they're any good.

I'm running AMD3000+ Socket 939 Venice core on an MSI K8T Neo2 motherboard with i386 kernel - everything works fine.  (although when I bought it all I had to flash the BIOS to get it to work with the then-new Venice core).   Truthfully, it's plenty fast for everything I've thrown at it, including some pretty hairy scientific stuff for school, so trying an i686 kernel hasn't made it very far on my "things to try" list.  32 bit Breezy and programs work just fine on it.

---

### Post by robenroute on 2006-03-24
Thanks for your suggestion ekarni, but my reasoning is as follows (perhaps I'm on the wrong path...):

I don't care too much what processor I'll be buying; I'd rather have a computer sporting a simple Celeron but which is fully compatible and operational than a fully flexed Athlon Dual-Core machine that's limping along because the motherboard has a few issues (with Linux). So, I thought I'd start with the motherboard and than take it from there.

I also don't care whether I have a maximum of 2GB or 4GB RAM (and whether that's just DDR or DDR2, I honestly don't care), whether I can only use an AGP card or a PCI-e card (I might not even go further than the on-board graphics, if available). In my experience, the most important component of a computer system is its motherboard. However, like I said, I might be a litle wrong here. So please, anyone, feel free to set me straight....

Thanks a lot in advance.


*(edited because of typo)*

---

### Post by astoltz on 2006-03-24
Don't forget about the chipset.  In my (fairly limited) experience the nvidia stuff is hard to beat as far as linux support.  This is especially true if you want to stick with the on-board video.  Have a look at the MSI K8NGM-V.

---

### Post by ekarni on 2006-03-24
Yeah, I agree that you obviously want a fully-functioning system.  My rationale is that there are hundreds of motherboards currently in production, and only one is going to end up in your system.  Picking a processor tells you what socket you need to shop for, and narrows the field substantially.  Beyond, that, don't filter on things you don't care about.  You said you want 1394 and non-shared memory graphics, so those would be good things to require.  Price is probably a factor too.  Don't worry about the things you don't care about!  Then once you've got the field down to five or six mobos, search away and see if anyone has reported success or failure with any of them (or ones using components on them, especially north/south bridges and sound chips).  As with most problems, there's more than one right way to solve it.  This is just my approach.

---

