---
title: "Problem with running Ubuntu on PC"
date: 2011-08-27
forum: General Help
---

### Post by chris722 on 2011-08-27
Hello everyone, I'm new here and I have a problem with using Ubuntu. I have 5 years old PC and decided to install Ubuntu 11.04 on it. At the beginning I couldn't run the installation program because after choosing language it switched me to Live CD operating system, although I had chosen "Install Ubuntu" without trying it.

As my native language is not English and at first I tried installing Ubuntu in my mother tongue, I decided to run it once again in English and additionally I created partitions for Ubuntu using Partition Magic in WinXP.
Luckilly the installation program has started and I followed  the installation steps finally finishing it succesfully.

And here's where the problems started

When the computer is starting, there are white horizontal stripes blinking on the screen, but the system is able to start.(The same thing was with WinXp but not as intense as with Ubuntu)
While running firefox I faced several times browser crash (on fresh Ubuntu 11.04).

It happend to me a couple of times, that when I was browsing the internet or doing whatever, suddenly the screen switched to:
    a) black with errors
    b) many colourfull horizontal stripes and there was nothing possible to do but restart         the PC

Here comes my question:
What can be the cause of mentioned errors? Is it that I have incompatible hardware or something?
My PC is :
AMD Athlon 2400+
Saphire Radeon X1600
512MB RAM
SWAP = 2xRAM

I heard many good things about Ubuntu and I would really like to use it on my PC but for now it seems to be impossible. I'm thinking of trying other distros like Mint or even Debian but at first I'd like to get some information from experts on how to deal with the problem.

And the last thing, sorry for my English because as I said it's not my native language ;)

---

### Post by raja.genupula on 2011-08-27
. two options 

1. upgrade your RAM minimum 1gb for better performance 
2.install lubuntu or xubuntu

---

### Post by Mark Phelps on 2011-08-27
If you had completely incompatible hardware (I.e., video card), then you would not even see a desktop.  The fact that you see one indicates that Ubuntu recognized it and installed drivers for it.

The X1600 is an OLD ATI card -- so old that AMD no longer provides Linux drivers for it.  That means the drivers already installed are the only ones available.  Don't be tempted to download and install any others.  They won't work, will trash your display, and you'll have to boot into a command line to remove them -- and replace them with the same drivers you already have in place.

The video artifacts you're experiencing, especially since you see the same ones in XP, are indicative of a failing card or monitor.  There's nothing you can do in Ubuntu to fix either.

The system memory is very small.  I'm surprised that Ubuntu 11.04 even works for you.  If you can't expand the memory to at least 1GB, as others have suggested, then consider switching to one of the other distros mentioned.

---

### Post by chris722 on 2011-08-27
Thanks for the replies.
Seems that I have to choose another distro for my PC. Could anyone recommend most suitable for my PC? The PC is going to be used mostly to browse the internet, doing basic things like writing in office-like applications, prining, watching movies etc.
I'm considering linux Mint,open SUSE, lubuntu or Debian, but the last one is less likely for me to install because many people say it's better for server rather than for desktop.

Any advice is apreciated

---

### Post by raja.genupula on 2011-08-27
for your system i choose lubuntu , it is simple & good performance for low ram systems 


[http://en.wikipedia.org/wiki/Lubuntu](http://en.wikipedia.org/wiki/Lubuntu)

look at that link .,

---

### Post by claracc on 2011-08-28
I recommend lubuntu 11.04 too. Very light distro.

I have installed it in an old pentium III laptop 1GHz, 512 Mb RAM fom wich 64 MB go for the sis 630 videocard, 20 GB HD and it works very well.

I use this old laptop to surf the web ( I recommend epiphany browser better than default one: Chromium) and only slows down when I try to see flash embedded videos, which I see in slow motion, but I think I can blame adobe flash for it.

I have installed VLC as video and audioplayer and can play youtube videos without exhausting the CPU of this old laptop.

---

### Post by 3rdalbum on 2011-08-28
It sounds like the problem is your video card. That is an old card and ATI doesn't support it anymore.

Before changing to a different distribution, I'd suggest installing Unity 2D and using that instead. Your problem sounds like something similar I was having. Install the 'unity-2d' package from Synaptic Package Manager or Software Center, log out, click on your name and then at the bottom menu choose "Unity 2D". Type your password and press Enter.

If Unity 2D works without problems, then you don't need to change distro.

If you still have problems, then it's probably a driver issue. Switching to Debian, Linux Mint or Lubuntu will not help because these all have a common base. Switching to something like Fedora or OpenSUSE, which both have a different underlying base, might solve your problem.

It could also be an actual hardware problem, possibly one that's not exposed by Windows XP's primitive 2D desktop.

Another possibility, although less likely in this case, is bad RAM. Windows often doesn't expose problems with your RAM because frankly it reserves a big chunk of memory that it usually never uses; possibly the bad spot is a part that Windows keeps blocked off for its own purposes but never uses. Linux keeps all your RAM in play and usually uses as much as possible for making things faster, meaning that it's more often a victim of faulty RAM modules.

---

### Post by chris722 on 2011-08-28
Thank you for so detailed info:)
The thing is, I don't use Unity. I chnged it to Classic Ubuntu in the login screen.
I have almost completed downloading Lubuntu and hopefully the system is going to work fine.
If not I'll get the distros with different base that you mentioned.

Thanks for the replies:)

---

### Post by chris722 on 2011-09-01
OK, I'm back:)
I dwonloaded Lubuntu and burned a live cd. When I was trying to boot my PC using that CD, an error occured:
"Your board has no valid PCI subsystem ID and thus can't be autodetected. Please pass card=<n> insmod option to workaround that. Redirect complaints to the vendor of the TV card. Best regards.

Here's the list of valid choices for the card=<n> insmod option:
card=0 -> UNKNOWN/GENERIC
....
card=72 -> TBS 8920 DVB-S/S2"

From what is said above I figured out that the problem can be with my TV card as well (My TV card is PixelView which is on the list of 72 items). When I try to type card=3 (which is PixelView) nothing happens.

So there are two problems (TV and Video Card) and I have no idea how to overcome them.
Is there any chance to install Linux OS on my PC?

---

