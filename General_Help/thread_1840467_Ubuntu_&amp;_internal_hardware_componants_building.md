---
title: "Ubuntu &amp; internal hardware componants: building a computer help"
date: 2011-09-07
forum: General Help
---

### Post by Starbug on 2011-09-07
I hope I'm putting this in the right section, since it's not specific to  any particular problem. If not, admin please move to correct section.


A short background: I am currently running Windows XP. It has never  failed me, always does what I want, and I've never had a problem with  bugs, compatibility, or viruses. I refuse to downgrade (yes, I do mean _down_grade)  to Vista or Windows7. There is nothing good about those operating  systems. Microsoft should be ashamed of themselves for inflicting it  upon the poor unsuspecting masses. It's a beautiful piece of eye candy,  but that's it. I'll let Apple rape my wallet before submitting to Vista  or Win7. (Tell us how you really feel, Starbug. LOL, sorry guys....)

So here's what I'm planning, and where my questions begin. I am going to  be building a new computer, built into a custom-made desk (it will look  a lot like this:  [http://www.pcworld.com/article/224804/casemod_builds_a_pc_into_a_desk_looks_awesome.html](http://www.pcworld.com/article/224804/casemod_builds_a_pc_into_a_desk_looks_awesome.html)   There is both a night and day pic in there). I would like either a single  large widescreen monitor (around 25-30") for my graphics work and some  gameplay, or a dual monitor setup (19-25" each will suffice). I'm  interested in using a multi-core CPU, undecided yet as to Intel vs AMD. I  read Linux doesn't like ATI graphics cards, so I'll be using Nvidia. 

Questions:
**1)** Can Ubuntu support dual monitor setups?
**2)** Can it support multi-core CPU's? Dual, quad, or both? Is there an Intel or  AMD compatibility preference (like the graphics cards have)?
**3)** What internal hardware does Ubuntu prefer? What does it NOT like?
**4)** Is there a stability difference between 32-bit and 64-bit OS versions? Quirks or issues between them?
**5)** Viruses. Is it really *that* true, that Ubuntu doesn't get  infected? That there is truly no need for a firewall or  anti-virus/malware software? I find this hard to believe, since there's a  bored hacker out there somewhere, with nothing better to do with  himself than to invent horrible worms for various computers.... even  Apple gets infected once in a while. So, if Linux does indeed get  infected from time to time, what anti-virus and firewalls work with  Linux? Mine are all Windows-specific (as far as I know)....
**6)** Dual booting. I plan to put the two OS on separate hard drives (in case one decides to implode or catch a virus, etc, the other will not be affected), and have a third hard drive for storing all my files (graphics, photos, music, video, big stuff) so that hopefully I can access them equally between the two OS. I know things like .jpg are universally-read between the two OS types, for instance. Having never dual booted before, can I do this with two separate hard drives, or do they need to be on a single partitioned hard drive? (if single, I need to install XP first, then Ubuntu, right?)
**7)** Video cards: Nvidia yes, ATI no. Still correct with Ubuntu's newest version? 
**8 ) **Sound cards: what works, what doesn't?[B]
9)[/B] What else do I need to know?
**10)** After thought, curiousity... with touchscreen monitors becoming available (I think Windows 8 is supposed to be introducing this feature, or something?) Would this be something the Ubuntu people might include in a future release? I'm not currently looking for this feature, but it may be kind of fun in the future. Not a deal breaker if it won't be. I don't honestly care one way or the other, as finger prints would be annoying, scratches occur, and the touch screens at my work show what kind of problems that technology has.... (ex: "stupid button, REGISTER my finger-press! ARRRGGHHH!" *tap-tap-tap-tap-tap* LOL.) On the other hand, if I could build my computer to be somewhat like the one in TRON and similar futuristic scifi shows, that would be way cool. So yeah, just a curiosity point right now. 


Since I will be upgrading everything as I go, and that means also hard  drives, I figured it would be fun to try a new OS. But since not  everything works in Linux (like Photoshop and some games), I will be  dual booting between WinXP and Ubuntu. If Ubuntu doesn't like a  particular program or peripheral, I can always switch back to XP and get  it done. Simple.

Thank you all for your time. Sorry for all the questions! I'm looking forward to your answers. The  sooner I get them, the sooner I can start buying computer parts...  mua-hahahahaha..... \\:D/




PS, completely unrelated to Linux or Windows, but so cute and funny (and  even computer-related), that I thought I'd share. Keep your eye on the  cat, especially at the end. Enjoy (speakers on!):  [http://www.simonscat.com/Films/Cat-Mouse/](http://www.simonscat.com/Films/Cat-Mouse/)  (VERY work safe and kid-friendly)

---

### Post by Starbug on 2011-09-12
....so....nobody out there can shed a little light on at least one question? If I am looking for answers in the wrong place, could somebody please direct me to a different source?

---

### Post by pqwoerituytrueiwoq on 2011-09-12
i am using a quad core with lucid now full details in sig
if you get a nvida gpu get a 8000 class or higher for vdpau
if you have a 64bit processor use a 64bit os
only reason for  worrying about viruses is to keep them from getting to a windows system
on that note use common sense only use software from sources you trust
out of the box ubuntu will prefer a intel gpu as they use open source drivers (you will be promoted to install nvida/ati proprietary drivers)
certified hardware for Ubuntu [http://www.ubuntu.com/certification/catalog](http://www.ubuntu.com/certification/catalog)
as for sound cards just use what is on the motherboard no need to wast money there
read the reviews on the part you are buying search for ubuntu (usally anything with 50+ reviews will have someone who will tell you how it works on linux)
installing windows in a dual boot is the easies way but it is not mandatory (google fix grub after windows install)
as for the dual monitors use 2 with the same resolution (based on my exp with nvidia cards idk how it is for ati/intel)
you can use one hdd per OS or 1 hdd for multiple OSes it does not matter you (you can use 2 hdds for one os)

only issue i had was some apps using the wrong sound device disabling the hdmi audio made everything use the motherboard audio (my monitor does not have hdmi is has vga/dvi)
i used this file to disable it
/etc/modprobe.d/blacklist.conf
added this line [FONT=Courier New]blacklist snd_hda_codec_nvhdmi[/FONT]

---

### Post by oldfred on 2011-09-12
I like at least one operating system per drive so each drive is bootable and Windows & Linux on separate drives.

You will need to format your shared data partition(s) as NTFS as both Windows & Linux read NTFS. Only mount Windows system partiiton as read only if you mount it at all, except if you have to do repairs.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
I like the reason, except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by Starbug on 2012-12-20
Life got in the way and my computer build had to go on the back burner, but now I am revisiting this project again.

Thank you both for your answers. I like that Linux and Windows can each have their own separate hard drive, and yet you can still dual boot between them. That's cool, and in light of this info I will be changing my hard drive arrangement plans. Do you still set the hard drives up as one Master and one Slave on the motherboard? Or do they both have to be set up as a Master in order for this to work?

The graphics card scene looks like it's gone through some major changes since I was last looking (it's seriously been a *long* time since I looked). I am hoping to use a Radeon 7970 GHz Edition. Does the current Ubuntu still prefer nVidia brand over a Radeon?

Thanks guys! ):P


Edit: If it matters, I'm currently looking at using the following parts.... 
Intel Core i7 3770K 3.5GHz processor, 
16GB 2133MHz DDR3 RAM, 
Radeon 7970 GHz Edition graphics card, 
and I think [this Asus motherboard]("http://www.frys.com/product/7155662?site=sr:SEARCH:MAIN_RSLT_PG") (still kind of researching this part).

---

