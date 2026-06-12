---
title: "windows is to WINE as mac is to???"
date: 2011-12-22
forum: General Help
---

### Post by flyingfisch on 2011-12-22
Is there a mac compatibility layer for linux? Is it even possible? Just wondering.

---

### Post by asifnaz on 2011-12-22
> **flyingfisch said:**
> Is there a mac compatibility layer for linux? Is it even possible? Just wondering.

AFAIK there is no such layer for Linux

---

### Post by cybergalvez on 2011-12-22
of course its possible, but its not been done, and frankly I'm sure even if someone tried it Apple would crush it

---

### Post by N00b-un-2 on 2011-12-22
There is no Wine equivalent to Mac.  Your only options there are A) Virtualization, or B) installing OSX.  Unless you have actual Mac hardware, this violates Apple's EULA and you will not receive any help here on the subject, as Ubuntu does not condone intentional violation of software license and doing so will not be discussed here.
however, you may want to look at insanelymac and osx86 project.  What you do with that information is your decision, just don't discuss it here.;)

---

### Post by flyingfisch on 2011-12-22
I was just wondering, not really seriously thinking about it. So the EULA actually does not allow making a program like WINE for it? wow.

---

### Post by N00b-un-2 on 2011-12-27
It is a direct violation of Apple EULA to install or use any apple software on any non Apple branded hardware.  That being said, I suppose that if you were to install Linux on a Macbook, developing an OSX WINE analog would technically be within the scope of the EULA.  However, Apple's EULA specifically dictates the actual installation and virtualization of Apple software.  I could easily see Apple's lawyers picking apart any project's claim of legitimacy on the grounds of lack of definition.  See, WINE literally stands for "WINE Is Not an Emulator", meaning that there is no virtualization taking place whatsoever.  WINE is actually an open source, clean room reimplementation of the closed source Windows API which has been compiled to work on multiple non Windows platforms including Linux, BSD and OSX.  Apple products like the iLife software collection are the flagships of the Apple armada and constitute the core of what makes a Mac different from a PC.  I can guarantee that any effort to port their highly specialized software to any platform aside from the guilded gates of the OSX world would be summarily crushed by the litigious might of the Apple corporation.
Hackintosh is where it's at if you're looking to run Apple software on anything but a real Mac.

---

### Post by Unguidedone on 2011-12-28
> **cybergalvez said:**
> of course its possible, but its not been done, and frankly I'm sure even if someone tried it Apple would crush it

/apple juice

---

### Post by guestolo on 2011-12-28
[http://sourceforge.net/projects/mac-on-linux/](http://sourceforge.net/projects/mac-on-linux/)

[http://www.davidbaumgold.com/tutorials/wine-mac/](http://www.davidbaumgold.com/tutorials/wine-mac/)

---

### Post by N00b-un-2 on 2011-12-30
> 	
Re: windows is to WINE as mac is to???
[http://sourceforge.net/projects/mac-on-linux/](http://sourceforge.net/projects/mac-on-linux/)

[http://www.davidbaumgold.com/tutorials/wine-mac/](http://www.davidbaumgold.com/tutorials/wine-mac/)

1) Mac On Linux is for PPC architecture only, and Old pre-Intel Macs are pretty much the only PPC based computers, so what's the point if you can run OSX natively?  obviously I know there are other ARM based platforms like cell phones and tablets, but in terms of desktop/laptop computers, Apple was pretty much the only game in town and they no longer make PPC based macs, nor are they supported anymore.

2) Mac On Linux is virtualization software like VirtualBox, QEMU, or VMWare intended to allow you to run PPC OSX (Leopard and before) on PPC hardware, hence it will not allow you to run modern OSX software like iLife.  It is NOT a way to natively run Mac apps on Linux like you can with WINE.  Not only that, but it's not being actively developed and is long since defunct.  It hasn't been updated since 2007.  And I must reiterate -- IT'S ONLY FOR PPC!  It can not and will not run on Intel x86 based computers regardless of how many arguments you try to pass to it at compile time for the same reasons why it's impossible to run Windows natively on a PPC based Mac.

3) Your second suggestion is a deprecated guide for installing WINE on Intel Macs.  completely irrelevant and off topic.

---

### Post by crazy bird on 2011-12-30
> **windows is to WINE.....** Not really. WINE is a compatibility-layer which enables Linux users to run Windows programs on a Linux system without installing a full Windows versions. WINE is only a full reimplementation of the Windows API layer which makes Windows itself unnecessary. So, basically: No, Windows is not to WINE.

---

### Post by N00b-un-2 on 2011-12-30
> **crazy bird said:**
> Not really. WINE is a compatibility-layer which enables Linux users to run Windows programs on a Linux system without installing a full Windows versions. WINE is only a full reimplementation of the Windows API layer which makes Windows itself unnecessary. So, basically: No, Windows is not to WINE.

That is not at all what the op was saying.  The OP's question was what is the OSX equivalent of WINE.  There is none.

---

### Post by teh603 on 2011-12-30
Let's not forget BasiliskII and SheepShaver, if someone needs to run old hoary Classic-era stuff. Dunno how well they run on Linux, unfortunately. I never could get SheepShaver to locate the boot image.

---

### Post by PhilGil on 2011-12-30
I've often wondered why there aren't more Mac applications ported to Linux. It seems like it would be easier than porting Windows software (as Mac is UNIX-like). And at least one major component of Linux is Apple-developed.

I don't know anything about the internals of Mac software, though. Maybe it's not possible.

---

### Post by gardnan on 2011-12-30
Well, just to point out something, OSX is actually POSIX compliant due to Apple incorporating user space applications and libraries from FreeBSD, so it is actually relatively easy to port C programs that do not make heavy use of Apple specific libraries or drivers.

Also, there is the GNUStep libraries for Linux that provide much of objective-C based NeXTSTEP components of the Cocoa API. 

Overall this means that any application can be ported with relative ease (compared to Windows) back and forth between the two systems. As a result, I don't think there is any open-source software on Mac that has not already been ported to Linux, or can easily be ported to Linux. I know this probably isn't what you were thinking of, just something to keep in mind.

---

### Post by PhilGil on 2011-12-30
@[gardnan]("http://ubuntuforums.org/member.php?u=1312003")

Thank you for the response. I don't know enough about the Apple ecosystem to be familiar with applications that are common to OSX and Linux. It seems to me, though, that there might be an opportunity for proprietary software that already works on OSX to be ported to Linux at relatively low cost. The demand seems to be there.

---

### Post by guestolo on 2011-12-31
> **N00b-un-2 said:**
> 1) Mac On Linux is for PPC architecture only, and Old pre-Intel Macs are pretty much the only PPC based computers, so what's the point if you can run OSX natively?  obviously I know there are other ARM based platforms like cell phones and tablets, but in terms of desktop/laptop computers, Apple was pretty much the only game in town and they no longer make PPC based macs, nor are they supported anymore.

2) Mac On Linux is virtualization software like VirtualBox, QEMU, or VMWare intended to allow you to run PPC OSX (Leopard and before) on PPC hardware, hence it will not allow you to run modern OSX software like iLife.  It is NOT a way to natively run Mac apps on Linux like you can with WINE.  Not only that, but it's not being actively developed and is long since defunct.  It hasn't been updated since 2007.  And I must reiterate -- IT'S ONLY FOR PPC!  It can not and will not run on Intel x86 based computers regardless of how many arguments you try to pass to it at compile time for the same reasons why it's impossible to run Windows natively on a PPC based Mac.

3) Your second suggestion is a deprecated guide for installing WINE on Intel Macs.  completely irrelevant and off topic.

blah blah blah
So wine does run on Mac, is that correct???

---

### Post by crazy bird on 2011-12-31
> **N00b-un-2 said:**
> That is not at all what the op was saying.  The OP's question was what is the OSX equivalent of WINE.  There is none.

True, but most Linux users think that WINE is a **WIN**dows **E**mulator which is no the fact. So comparing Windows to WINE does WINE no good. That's what i was aiming for.

---

### Post by N00b-un-2 on 2012-01-02
> **guestolo said:**
> blah blah blah
So wine does run on Mac, is that correct???

Wine does, Crossover is far more compatible albeit not free.  But then again, what is free on Mac?

---

### Post by bruno9779 on 2012-01-02
> **PhilGil said:**
> @[gardnan]("http://ubuntuforums.org/member.php?u=1312003")

Thank you for the response. I don't know enough about the Apple ecosystem to be familiar with applications that are common to OSX and Linux. It seems to me, though, that there might be an opportunity for proprietary software that already works on OSX to be ported to Linux at relatively low cost. The demand seems to be there.

Apple is not happy just selling their software. They want you to buy all their hardware line to run that. In other words, it is never gonna happen.

---

### Post by N00b-un-2 on 2012-01-02
> **PhilGil said:**
> I've often wondered why there aren't more Mac applications ported to Linux. It seems like it would be easier than porting Windows software (as Mac is UNIX-like). And at least one major component of Linux is Apple-developed.

I don't know anything about the internals of Mac software, though. Maybe it's not possible.

The major component you're talking about is CUPS.  And the distinction must be made, OSX is not UNIX like, it is BSD.  OSX is built on top of an open source fork of BSD called Darwin, but apart from being POSIX compliant and using some of the GNU tools, OSX is NOT open source.  It is certainly possible to port any Linux or BSD software to OSX with the right tools either using the native Aqua interface which uses proprietary coding languages like Cocoa and Java, and OSX even ships with an optional X11 server which can run on top of OSX.  However, the reverse is not true for Linux/BSD.  Not without a great deal of work anyway because most Apple software relies on portions of the OSX operating system which are closed source in addition to the BSD underpinnings so it would be practically impossible to directly port an Aqua app to using X, and it would be particularly difficult to translate native Mac software to being X compatible.  Not to mention the fact that doing so would beat all of that highly polished OSX shinyness with an ugly stick the way WINE does to Windows apps.

---

