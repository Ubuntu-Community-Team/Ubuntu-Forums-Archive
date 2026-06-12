---
title: "Is Ubuntu netbook remix (10.04) going to have a normal desktop option?"
date: 2010-04-10
forum: General Help
---

### Post by BadName on 2010-04-10
This annoyed me about 9.10 which was my reason for not sticking with it. Would like to upgrade but the netbook remix interface is not my thing. I like having a desktop to work on (which is what a desktop is for). It is quite frustrating for me trying to work on the netbook interface. Love ubuntu though and really would like to upgrade. Been running Jaunty and i love it but i'd like to switch to the LTS version if it is going to have this feature (and is stable unlike 9.10 which didn't even offer it). Anyone know if it's going to be included as a stable feature? Thanks :D

---

### Post by tgm4883 on 2010-04-10
I'm running it but don't see a regular desktop mode (although I haven't really looked).

If you don't like the netbook interface, why don't you just install the regular desktop?

---

### Post by BadName on 2010-04-10
Isn't the UNR lighter on resources though? Optomised for netbooks? Or is it just the interface?

---

### Post by haddog on 2010-04-10
> **BadName said:**
> This annoyed me about 9.10 which was my reason for not sticking with it. Would like to upgrade but the netbook remix interface is not my thing. I like having a desktop to work on (which is what a desktop is for). It is quite frustrating for me trying to work on the netbook interface. Love ubuntu though and really would like to upgrade. Been running Jaunty and i love it but i'd like to switch to the LTS version if it is going to have this feature (and is stable unlike 9.10 which didn't even offer it). Anyone know if it's going to be included as a stable feature? Thanks :D

In 10.04 Beta1 Ubuntu Netbook Edition, (formally called UNR) You can get to a standard GNOME desktop without rebooting? Log Out of UNE, then while in the GDM screen, on the bottom right choose the Gnome option from the menus. Then log in. You will now be in a GNOME session using the GNOME window manager vice the UNE Maximus window manager. Hopefully this login option won't/hasn't be removed.

---

### Post by tgm4883 on 2010-04-10
AFAIK it is just the interface

---

### Post by kmsalex on 2010-04-10
but when your in the defualt interface it's actually a little heaver on resorses, the only reson to in stall the net book version is for the gui, so if you don't like it just use the desktop edition.

---

### Post by sgosnell on 2010-04-10
From what I've seen (not that much because I hate the NR interface) the standard desktop is actually lighter on the resources, and the only other difference is the interface.  I don't like the busy interface, and so I removed it a few versions back.

---

### Post by mauricep on 2010-04-12
Canonical claims the the Netbook Remix is optimised for the Intel Atom processor.

This is why I run 9.10 with the Netbook Interface removed. But this required some fiddling. I could not find an easy way to do this in 10.04. However, the old solution will certainly still work (removing the netbook launcher and maximus from autostart, and installing the normal desktop). I did not try haddog's solution of logging out and back in though.... yet.

I much prefer the look of the Kubuntu 10.04 interface. These guys have really tried something a little innovative. If I can find out how to switch easily between netbook and normal interfaces in Kubuntu, I may switch to KDE for the first time...

---

### Post by snowpine on 2010-04-12
> **mauricep said:**
> Canonical claims the the Netbook Remix is optimised for the Intel Atom processor.

It is. So is regular Ubuntu. Because one option is optimized does not mean the other isn't. :)

---

### Post by travy4911 on 2010-04-12
UNR actually boots and runs slower on my acer aspire 1.  Just thought I'd trow my 2 cents in.

---

### Post by mauricep on 2010-04-12
@snowpine
I had a suspicion that the Intel Atom optimisations should also be included in Ubuntu vanilla. But then Canonical is being a little misleading on this:
"All of the initial Ubuntu Netbook remixes combine optimisations from the Moblin project for Intel® Atom™ processors"
(From [http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr))

Should it read "All Ubuntu remixes...."/"The Ubuntu kernel...."?

---

### Post by snowpine on 2010-04-12
> **mauricep said:**
> "All of the initial Ubuntu Netbook remixes combine optimisations from the Moblin project for Intel® Atom&#8482; processors"
(From [http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr))

I believe that page is outdated marketing material. It describes a special OEM version of Ubuntu 8.04 that Canonical sold to hardware makers like Dell for their Mini series. It used a special LPIA (Low Power Intel Architecture) "port" compiled specifically for the Atom architecture. LPIA was never part of "regular" Ubuntu Netbook Remix, and Canonical dropped support for it last year.

Based on my experience with Ubuntu LPIA and its current lack of support, I cannot recommend it. 

Notice this link and disclaimer at the bottom of the page:

> If you are interested in trying out Ubuntu Netbook Remix for non-commercial purposes please see [http://wiki.ubuntu.com/UNR](http://wiki.ubuntu.com/UNR) for detailed instructions.

---

### Post by mauricep on 2010-04-12
This is interesting. Thanks for the info and the sharp eye. Even more obvious evidence that the site is out of date is the title referring to "UNR" rather than "UNE". They need to get someone on that...

---

### Post by psusi on 2010-04-12
That's kind of the whole point of UNR.  If you want the normal desktop, then install normal Ubuntu.

---

### Post by Jerry N on 2010-04-12
I installed the 9.10 UNR on a dual-core ATOM330 desk-top machine I built up and didn't like it.  I kept changing it (got rid of the busy user interface right off) to get it the way I wanted and finally installed the real Ubuntu 9.10.  I'm using it now as a wireless print server, serving both Linux and Windows nodes on my network.    

Jerry

---

### Post by la3875 on 2010-04-16
I think my question might be appropriate here. I am considering upgrading my older laptop from Hardy desktop to Lucid netbook because I actually like the interface. Can I do this as a standard distribution upgrade or will I have to upgrade from a downloaded image?

I have been lurking around here since 5.10 and Lucid is clearly the best version yet.

---

### Post by mauricep on 2010-04-16
> **la3875 said:**
> I think my question might be appropriate here. I am considering upgrading my older laptop from Hardy desktop to Lucid netbook because I actually like the interface. Can I do this as a standard distribution upgrade or will I have to upgrade from a downloaded image?


I think it should be possible to upgrade using the repositories with the upgrade option. However, I have heard several people reporting problems and bugs with the upgrade process. I would strongly recommend you do a fresh install, especially since you are skipping some versions.

Even with a fresh install you can however keep all of your settings by keeping your /home/user directory. If it is on a seperate partition, just designate it as your /home partition again during the install, and specify that it should not be formatted. If it is on the same partition as the install (which I believe is the default), you will have to back it up and restore it after installing. If you do that, just make sure to get all of the hidden directories.

Mauricep

---

### Post by la3875 on 2010-04-18
By far the best Ubuntu yet! After much fooling around - see other post, I'm running UNE on the Dell 600m whose specs are very similar to the netbooks out there. I find everything seems faster. I don't know if its the distro or the fact that I moved /home to a separate partition on install.

Regardless, great work all!:KS

---

