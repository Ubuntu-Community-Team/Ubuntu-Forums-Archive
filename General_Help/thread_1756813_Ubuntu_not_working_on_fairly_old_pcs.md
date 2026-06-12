---
title: "Ubuntu not working on fairly old pcs?"
date: 2011-05-12
forum: General Help
---

### Post by Netguy101 on 2011-05-12
[SIZE=3][FONT=Arial]Hi,

I installed Ubuntu 11.04 on my laptop, and it runs great! I love using it and it just helps me get all my work done. But later, I decided to install Ubuntu 10.10 on my desktop pc, because I like it and wanted to see how it would work. So after installing it, My computer began to work fine until I rebooted the pc, I noticed that the boot screen was terrible, there was an Ubuntu 10.10 text and four dots under it. Later, I found out that the computer would not boot. After logging in the login screen just flashes, and then the screen turns blank and sents me back to the login screen again. 

Is there anything I can do to fix or buy to get my pc to run ubuntu respectively?

P.S. My Computer has
512MB of Ram
1.20GHZ Intel Celeron Processor
20GB or Hard Disk space
1280x1400 screen resolution
And its a HP Vectra XE310-32
[/FONT][/SIZE]

---

### Post by trozamon on 2011-05-12
On a computer with specs like that, I would recommend Xubuntu. The UI is specifically built to run on low resource machines; I believe minimum requirements are 1.0GHz CPU and 256 MB ram, so you should be good with Xubuntu.

---

### Post by jerrrys on 2011-05-12
i have a celeron running xubuntu and working good.  you didn't say what kind of video you got.

and did you run it live befor installing?

---

### Post by lithopsian on 2011-05-12
The desktop/windows manager is by far the biggest resource hog in the full Ubuntu install.  That is obvious when you consider that the requirements for a server install are a 300MHz i386 equivalent with 128MB of RAM.  You could fiddle about and install XFCE or Openbox from the command line, or you could just use a different distro as suggested.

---

### Post by lukeroge on 2011-05-12
Try using Lubuntu, its a little lighter than Xubuntu and it just recently got recognized as an official Ubuntu version. It should run fine on older computers.

---

### Post by NormanFLinux on 2011-05-12
Try Ubuntu LTS 10.04. Oz Unity runs like a charm on a resource constrained netbook and on my Pentium 4 laptop with no problems. Boot up and shut down is blazingly fast.

---

### Post by Netguy101 on 2011-05-15
[FONT=Arial][SIZE=3]Thank you,[/SIZE][/FONT]

[FONT=Arial][SIZE=3]I guess I'll choose Xubuntu or Lubuntu since they both seem to focus on older pcs...[/SIZE][/FONT]

[FONT=Arial][SIZE=3]Also, what version would you think is best 11.04, 10.10, or 10.04?[/SIZE][/FONT]
[FONT=Arial][SIZE=3]I noticed that Lubuntu and Xubuntu have really added a lot in their 11.04 versions.[/SIZE][/FONT]

---

### Post by mörgæs on 2011-05-15
Try them in the order you wrote: 11.04 first, then 10.10 if it does not work.

Remember to have wired internet access while installing.

By the way, 10.04 is not long term support in Lubuntu (just so you know there is no special reason for using this one).

---

### Post by MAFoElffen on 2011-05-15
> **mörgæs said:**
> Try them in the order you wrote: 11.04 first, then 10.10 if it does not work.

Remember to have wired internet access while installing.

By the way, 10.04 is not long term support in Lubuntu (just so you know there is no special reason for using this one).
+1 on this.
> 
[SIZE=3][FONT=Arial][SIZE=2]P.S. My Computer has
512MB of Ram
1.20GHZ Intel Celeron Processor
20GB or Hard Disk space
1280x1400 screen resolution
And its a HP Vectra XE310-32[/SIZE]
[/FONT][/SIZE]                                          I noticed that you didn't say what "graphics card" you had in this desktop, which may be the only problem that you are experiencing on making your current installation work... with just a few configuration changes.

I have many installs of Ubuntu, Kubuntu and Xubuntu working for people that are running on a whole lot less resources.

---

### Post by mörgæs on 2011-05-15
Whoops, Lubuntu 10.04 has actually been 'upgraded' to long term support. Sorry for being too fast.

Nevertheless, there has been so much development going on in Lubuntu that I would recommend one of the newer ones.

---

### Post by Duncan Williams on 2011-05-15
As stated a couple of posts back:
*I noticed that you didn't say what "graphics card" you had in this desktop, which may be the only problem that you are experiencing on making your current installation work... with just a few configuration changes.*
I know from experiance that installation and general running of ubuntu can have a lot to do with:
**Graphics Card** > drivers > versions of drivers.
also:
**Bios settings**. (may work fine in windows but need settings changed for linux > settings for >agp aperture / S.M.A.R.T. settings in particular.

Coincidently you may have hardware issues (I had a ram-card fail at the same time I had other software probs - took me a awhile to work it out by removing and testing my video,sound,ram cards and all cabling/connections.

Also you have issues like > is it usb 1 (or 2).
(a failed device on your system may not be recognised or used in windows. In ubuntu, on installation it will check your whole system out)
If you get ubuntu up you may be best using 2D unity (seperate install from software center) or classic mode.

---

### Post by Netguy101 on 2011-05-16
[FONT=Arial][SIZE=3]Thank you everyone,[/SIZE][/FONT]

[FONT=Arial][SIZE=3]I would just like to say, is it safe to use CrunchBang Linux? I have heard about this distro many times, but have never used it. Is it good for my old machine which I would just like to "set and forget" and occasionally use when needed?[/SIZE][/FONT]

---

### Post by Duncan Williams on 2011-05-16
don't know about crunchbag but a very lightweight, small, fast, minimum resources needed distro is:
[_peppermint ice_]("http://peppermintos.com/2010/07/peppermint-ice-faster-lighter-aiming-for-the-clouds/")

This is also mainly cloud based 
(uses apps and saves data > online, instead of using onboard software).

This means you need minimum for fastest speeds out.

---

### Post by claracc on 2011-05-17
I have just installed ubuntu 10.04.02 in an old laptop (coppermine, 20 GB HDD, 512 MB ram from which 64 MB go for sis 630/730 graphics card, pentium III 1 GHz) and it works very well (responsive and quick enough to surf the web with firefox, use openoffice, listen to music and also to see videos with mplayer and low specs command options).

I only had to comment the sisfb driver in blacklist-framebuffer.conf and include video=sisfb in grub2 and sisfb in modules in initramfs in order to use ctrl+alt+f1 to f7 keys.

I only have a problem, that is the brightness of the lcd screen which is in its maximum and i cannot change (tried setpci, xbacklight, gnome-power-manager options..., I continue looking for a way to reduce brightness). I think this is due to the old 1997 BIOS, that needs special modules for acpi or perhaps apm.

Anycase, I would recommend ubuntu lucid lynx 10.04, which is a long term support distro and from my experience works in old computers (It make them usable).

---

### Post by Zill on 2011-05-17
> **Netguy101 said:**
> ...I would just like to say, is it safe to use CrunchBang Linux? I have heard about this distro many times, but have never used it. Is it good for my old machine which I would just like to "set and forget" and occasionally use when needed?
CrunchBang Linux is based on Debian Squeeze so is a very stable OS that performs very well.  Although not specifically built for low-spec machines, it's low system requirements, and in particular the OpenBox window-manager,  means that it does generally run quicker on such machines than more "bloated" OS's.

However, IMHO, CrunchBang is not particularly suited to a total Linux newbie.  A certain amount of tweaking is necessary to get things working properly and this is best done by someone with experience who can search for required information.

The great advantage of FOSS is that we can all try things out for free so my advice is to burn a CD and give the Live version of CrunchBang a try.  If you like it then you can install it later.

Despite the name (and the [disclaimer]("http://crunchbanglinux.org/wiki/about")!) I trust CrunchBang on my PCs. ;-)

---

### Post by DeadlyOats on 2011-05-29
Thanks for asking this question.  I noticed that my Ubuntu 9.10, Karmic Koala, is no longer supported for updates and the like (cry!), so I decided to upgrade to 10.10, and saw that there's actually an 11.04 out.  I too worried about my hardware not being supported, (P4 CPU, nVidia Gforce 7800 GT, Adaptec 2410 SA raid adapter, Razor Baracuda (spelling) sound card, etc) so I looked in the forums to see what was being said about it.

Then I found [[COLOR="Red"]_this page_[/COLOR]]("https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements"), and I figured I'd share what I found here where the question about old hardware was brought up.  I hope you don't mind.

Basically what I found is that my CPU, mobo, and graphics card shouldn't have any problems, but my "exotic" Razor Baracuda (spelling) and Adaptec RAID adaptor are still unknowns.  I'll update this post when I try it out and see what happens (typing this from Karmic Koala).

EDITED on 31 May 2011:

I tried 10.04 LTS, and then 11.04.  All of my "exotic" hardware was supported by both versions of Ubuntu.  AFTER updating my video card drivers to the nVidia proprietary drives, Unity was supported on my hardware.  I like Gnome better.  So, I'm using the Gnome Desktop.  But I'll look through the Unity Desktop again later (I like the window switcher in Unity, but that's the only feature that gets my attention, so far).

---

