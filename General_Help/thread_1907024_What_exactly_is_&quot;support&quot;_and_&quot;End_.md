---
title: "What exactly is &quot;support&quot; and &quot;End of life date&quot; ?"
date: 2012-01-10
forum: General Help
---

### Post by Nickolai_Leschov on 2012-01-10
Hello,

[Releases]("https://wiki.ubuntu.com/Releases") wiki article talks about "support" and "End of life date". I would like to clarify what exactly is meant by those terms. It looks like those terms mean the same, or "End of life" equals "End of support". Is it so?

I assumed that "support" term means the period of time during which Ubuntu developers keep releasing minor patches for security and compatibility of software packages constituting particular Ubuntu release. As long as I don't need new features and ready to take risks living without new security and compatibility patches I could continue to use old Ubuntu releases indefinitely, I thought. But, it looks like this is not the case?!

I have recently installed Ubuntu 9.04 (Jaunty) on an older system, only to discover that I can't install or update anything through Update Manager nor apt-get. To sum up my frustration:

1. What exactly "End of life" and "support" stand for? (the same?)

2. Is there meaningful way to use an Ubuntu release past its "End of life"? How can one install/update packages in such a system (from a CD/DVD, presumably)?

3. Where can I get a DVD of [Ubuntu 9.04?]("http://old-releases.ubuntu.com/releases/9.04/") (i386, desktop or alternate) There should have been DVDs, but I only see CDs left on the mirrors.

---

### Post by Paqman on 2012-01-10
> **Nickolai_Leschov said:**
> 
1. What exactly "End of life" and "support" stand for? (the same?)


Yes.

> 
2. Is there meaningful way to use an Ubuntu release past its "End of life"? How can one install/update packages in such a system (from a CD/DVD, presumably)?


It's possible, but not advisable for a machine that's connected to the internet because, as you mention, you won't get any security updates. If there's a vulnerability in a package on your system that's only found after support ends you won't get the fix and will be a target.

There's nothing to stop you installing .deb packages on the system though, as long as the package manager can satisfy the dependencies.

> 
3. Where can I get a DVD of [Ubuntu 9.04?]("http://old-releases.ubuntu.com/releases/9.04/") (i386, desktop or alternate) There should have been DVDs, but I only see CDs left on the mirrors.

Doesn't look like they are still on the download pages, but if you can find someone who can provide you with the MD5 hash for the Jaunty DVD you might be able to find it elsewhere on the internet (torrent?).

---

### Post by Nickolai_Leschov on 2012-01-11
What is the easiest way for me to use the older system like Ubuntu 9.04? I need to be able to install software, by apt-get if possible. Can I make apt-get install software from my Ubuntu installation CD/DVD? I think there should be many stuff that doesn't get installed by default, on the DVD at least.

I wanted to clarify: is it true that after 1.5 or 3 years after release  apt-get/Ubuntu Software Center just stops working because Canonical  deletes the files on the servers (looks like that), or can one expect apt-get et al. to  work for a longer period than updates are issued? (maybe some mirrors are still on?)

It looks crazy to me that anyone would use a system with built-in  obsolescence, and such a short term at that. And those 1.5 years worth  of updates, do they get thrown away and one cannot reach the previously  released updates when "End of life" comes?

---

### Post by mcduck on 2012-01-11
When Ubuntu release reaches it's end of life, the original repositories are closed, but all the existing packges are moved to another server at old-releases.ubuntu.com. The main purpose is to provide any user with an outdated version the ability to still upgrade to a later, still supported release (sometimes that might require updating through another already EOL vreleae version).

So if you edit your software sources, you can still install applications. They will just be outdated versions and without any security patches newer than the EOL date. It's possible to use an outdated OS, I'd just seriously recommend against doing that if the machine is going to be connected to any non-private network)

Why would the "built-in obsolescence" make any difference? That year and a half is worth three new Ubuntu releases, and the upgrading is free and in most cases very quick and easy as well. And if you prefer longer support times, there are always the LTS release, with 3 years of support on desktop and 5 on server (5 years on both starting from 12.04 LTS)

edit: doesn't every piece of software have the same built-in obsolescence? They will all some day reach the day when their developers stop supporting them. Each Windows version and each OS X version stops getting support, new software and security updates at some point... And same goes for most other software of course. ;)

---

### Post by cryptotheslow on 2012-01-11
> **Nickolai_Leschov said:**
> What is the easiest way for me to use the older system like Ubuntu 9.04? I need to be able to install software, by apt-get if possible.

If the reason for the desire to run v9.04 is because you have older / low performance hardware then you may want to consider a more up to date version of one of the lighter Ubuntu remixes e.g. Lubuntu

[http://lubuntu.net/](http://lubuntu.net/)
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

---

### Post by mcduck on 2012-01-11
> **cryptotheslow said:**
> If the reason for the desire to run v9.04 is because you have older / low performance hardware then you may want to consider a more up to date version of one of the lighter Ubuntu remixes e.g. Lubuntu

[http://lubuntu.net/](http://lubuntu.net/)
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

+1 to this. Even the latest versions of Ubuntu wrk just great on older hardware as long as you pick a desktop environment and applications suitable for the machine's resources.

I have a Ubuntu 11.04 system running on a old Athlon XP 2800+, with 512MB of RAM. The machine runs even the normal desktop OK, but a minimal install + Openbox and a selection of only the background services and tools I need, and the machine just flies (using a reasonable 36MB of RAM on desktop, leaving enough to use even heavier apps like Firefox and OpenOffice ;)).

---

### Post by mastablasta on 2012-01-11
also DVD just adds more language packs mostly..

and new Ubuntu (12.04) will be on DVD only.

stick with LTS if oyu want support on long periods of time. 10.04 is excelent edition (still supported until 2013) and doesn't use more memorry or anythign like that than 9.04.

but can you tell us why you want to use 9.04 version specifically? because of proprietary graphics drivers you need and that worked then or why?

---

### Post by Nickolai_Leschov on 2012-01-14
Thanks for hint, **mcduck**! I've replaced all occurrences of "us.archive" and "security" in /etc/apt/sources.list with "old-releases" and apt-get et al. works again! (in 9.04) Strangely, in 8.04 it still works by default. I wonder what it means for the original question of this thread.

I use Radeon 9600 video card and two monitors. I was using 10.04 until the abysmal desktop performance due to [inadequate graphics driver]("http://ubuntuforums.org/showthread.php?t=1893072") finally bugged me so much that I decided to downgrade Ubuntu. The driver from the amd.com says it only supports up to 9.04, so I wanted to try either 9.04 or 8.04 (because it's LTS). I never actually had any success installing driver from amd.com (that merits another thread), but I think something like this driver is included with Ubuntu up to 9.04 because right out of the box it works pretty snappy, desktop effects are enabled and glxgears works (unlike in 10.04). I only managed to make dual-screen work on 9.04, but not 8.04 (without proprietary driver there's no ATI Catalyst Control panel)

9.04 looks like the best option for me right now regarding performance. Unfortunately, I'm afraid of running into trouble being not able to install some needed software. So I investigate Lubuntu 11.10 too; looks promising for now. I detailed my stumbling blocks [in this thread](http://ubuntuforums.org/showthread.php?p=11611387), the main being I don't know how to enable dual-screen.

Re: built-in obsolescence. By this I mean making products that will become unusable by design after certain date. As Ubuntu 8.04 and 9.04 would indeed become by now if all servers that you specify in sources.list would go offline. Fortunately, it happened not to be quite so. One could argue that Macs and Windows PC do not even provide the functionality that is turned off on Ubuntu (apt-get), but it's not quite so: Macs and Windows have [a different culture](http://www.joelonsoftware.com/articles/Biculturalism.html) if not infrastructure of building software; it's customary to distribute software in binaries there, and in Unix you use the source. Therefore, even proprietary Linux drivers I download from amd.com require installing a dozen or two packages from repo's and build duing installation (but they wouldn't work for me anyway); on Windows or Mac they just don't that. So I would argue that in Unix systems such repositories are even more needed.

In Windows some of the software I use is around 15 years old and the OS itself (Windows XP) is over 10 years now and still usable and one can still use all the latest software for it. But suddenly Ubuntu 9.04 which is not 4 years out, is too old! I guess I took for granted all along and took peace of mind from the fact that if some new software [pulls Hitler on me](http://xkcd.com/528/), (I don't like the course of its development) I could always just stick to the old one. Doesn't look like that anymore. 

Thanks for help!

---

### Post by mcduck on 2012-01-15
8.04 still has it's repositories open, as it is still supported (to some level, at least). It's an LTS release and even though suport for desktop has already ended, it's still supported on server use until April 2013.

I can definitely understand tat you'd like to stick to an old version because of the graphics drivers. It's still a bit of a risk, though, better graphics versus security updates...

Actually the old AMD machine I mentioned has a Radeon 9600XT, so I had exactly the same problem with AMD not supporting it in it's new drivers any more, and old drivers not being capable of running on any up-to-date system.Running a lighter desktop environment definitely helped there, with Openbox I can even use xcompmgr to get some transparency effects and stuff like that even on the opensource drivers.

---

