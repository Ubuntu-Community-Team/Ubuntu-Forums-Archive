---
title: "Cannot get 10.04 desktop to load"
date: 2011-01-31
forum: General Help
---

### Post by sks24 on 2011-01-31
I'm having a very similar problem to the one described [here]("http://ubuntuforums.org/showpost.php?p=9975074&postcount=13").  Is the solution offered in the same place applicable to a unetbootin 10.04 USB install?  I tried to install 10.04 - Studio and Desktop - about a month ago, and the same thing happened with both of them: I would get to the Ubuntu logo splash, and then, when it would "try" to load the actual desktop, the graphics would kind of disintegrate, the screen would go black, and nothing else would happen.

Puppy Linux loads and works well, BTW.  

My preference is to install 10.04 Studio.  So, two questions:

1) Is there some other trick I should know about which will allow for an installation?

2)  It's not clear to me whether installing Studio from a USB stick is a good idea.  (I can get more DVDs, but I'm out just now, and so a USB would be convenient.)

3) Does "upgrading" Ubuntu 10.04 desktop with the packages pre-installed with 10.04 Studio get kludgy with this or that dependency not getting satisfied, or will the Synaptic PM - or, I guess the software center - take care of dependencies?  Waht would be really cool would be a one click "upgrade" for a switch from the 10.04 Desktop to Studio.

---

### Post by oldos2er on 2011-01-31
Can you tell us your hardware specs, specifically your video card?

---

### Post by sks24 on 2011-01-31
Derp!  Sorry, here:

Intel(R) 82852/82855 GM/GME Graphics Controller [Display adapter] (2x)
Seiko Epson [Monitor]

Hewlett-Packard HP Pavilion dv1000 (DZ731AV#ABA) Rev 1
Windows XP Home Edition Service Pack 3 (build 2600)
2GB RAM
1.70 gigahertz Intel Pentium M
64 kilobyte primary memory cache
2048 kilobyte secondary memory cache
Not hyper-threaded
Board: Quanta 09B8 34.20
Bus Clock: 100 megahertz
BIOS: Hewlett-Packard F.22 08/08/2005
Intel(R) 82801DBM Ultra ATA Storage Controller - 24CA
Primary IDE Channel [Controller]
Secondary IDE Channel [Controller]

And I did try the "escape" key remedy listed at that link for the 10.10 install, and it doesn't appear to work for a USB key installation.

---

### Post by sks24 on 2011-01-31
Please tell me if you need more information about my machine.

I went out and boughted me uh CD, and burned a 10.04.1 iso, checked the sum before then and disk integrity after the burn, and then tried several different combinations of the F6 install options, then ALL checked but "nodmraid," and they all gave me a black screen whenever I tried to load the OS into RAM.  

Would installing 9.10 and then upgrading from that work? Or would I be setting myself up for trouble on down the line.

Thanks in advance,
Scott

---

### Post by oldos2er on 2011-01-31
I know very little about Intel video on Linux, but I managed to find this: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
Don't know if anything there will help you or not.

---

### Post by sks24 on 2011-01-31
okie dokie.  I'll take a look . . .

---

### Post by sks24 on 2011-01-31
The "GTT Incoherency Patchs" look to be the most promising, but it's not clear to me how I would implement them.  How do I [update my system with unsupported patches]("https://launchpad.net/~brian-rogers/+archive/graphics-fixes-testing") absent an installed system?

Is there a way to slipstream files with Ubuntu?  

Is there a tutorial somewhere about how to set up an installation so that the OS is separate from all the files I create with it?  Because I can get a desktop with 9.10, and I could just nuke it with 11.04 when it is released with, presumably, a fix for this issue.  ("Brian Rogers has packaged this fix as an experimental Natty (11.04) kernel.") 

Thanks,
Scott

---

### Post by sks24 on 2011-02-18
Thanks so much os2er:  

I actually have two DV1000s, and they both died last week.  I did install 9.10 on them both, though, and one ran beautifully and the other had some sort of bug where it wouldn't run the update manager.  I took an actual photograph of the screen, then stored the photograph in the machine and didn't back it up to Picasa.  When I get it running again, I'll post it.

---

