---
title: "Best distro for old computer"
date: 2011-05-04
forum: General Help
---

### Post by ravij96 on 2011-05-04
I was in my garage and found an old computer.  It is a Dell Dimension 4550.  The specs are 
Intel Pentium 4 CPU 2.00GHz
1.99GHz, 256mb of RAM.

Out of all of that I only understand the ram part :/.  So can anyone help I tried Ubuntu but the live CD froze, I tried Kubuntu but the CD froze, I tried Xubuntu but the Live CD GUI wouldn't load correctly and I made a second CD just to check if it wasn't a problem with a disk but it still happened, and I tried Lubuntu but the live CD only shows a command prompt and I tried it twice to.  So someone please help me I have been trying this all day.

---

### Post by Riku Reed on 2011-05-04
I'd recommend Lubuntu.

Could you post the output from the terminal your having problems with?

---

### Post by ravij96 on 2011-05-04
Oh man I messed up Xubuntu wouldnt load the background and nothing would load and lubuntu was the one with the terminal.  All it would say is welcome to Ubuntu 11.04. Ill try putting a picture up.

---

### Post by ravij96 on 2011-05-04
Sorry the picture is hard to see its says from top to bottom.

* Starting NTP Server ntpd                                                                                      [ok]
* Starting Bluetooth                                                                                                [ok]
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-8generic i686)

* Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$


This happened when I tried lubuntu from the live cd

---

### Post by santy_kushwaha on 2011-05-04
i would suggest ubuntu 10.04 rather than trying ubuntu 11.04

---

### Post by ravij96 on 2011-05-04
I am trying to install lubuntu currently.  Also, doesn't grub install on a separate partition for 10.04 I'm not very good with these things and i don't want it to cause problems if I ever have to reinstall or upgrade :/

---

### Post by oracle2b on 2011-05-04
I'd use puppylinux or slitaz (30MB)..

---

### Post by lykwydchykyn on 2011-05-04
Any version of Ubuntu, no matter what desktop environment, is going to have the same graphics drivers; and if you're just getting a terminal login, it means the driver is not working.

I'm going to take a stab in the dark and guess that you have an Intel graphics chip, since that's what's in 90% of the Dell P4 computers I've seen (and I've seen way too many of them).

If Lubuntu doesn't work, you may want to try Debian stable.  I've found it's a little more reliable with older graphics hardware.

---

### Post by jramshu on 2011-05-04
What about LinuxMint? You can download the dvd version that has all the drivers and it's based on Ubuntu. 
That's not a lot of memory for your machine. Just a thought, could the RAM be bad?

---

### Post by peyre on 2011-05-05
I have an old (11yo) laptop; I run Lubuntu on it, and it runs very well.

Your problem might be due to lack of RAM.  The *buntu with the lowest RAM requirement is Lubuntu, but even it requires at least 128MB.  And if you have under 160MB, to install it you'll need to do a minimal install:

[https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall]("https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall")

Alternatively, if the latest version of *buntu won't run on your machine, try installing the latest LTS (long-term release), 10.04.  That's what I had to do for my laptop last time around; 10.10 wouldn't run right on it, though 11.04 seems to be running ok.

---

### Post by michaelzap on 2011-05-05
Crunchbang Xfce, Linux Mint Debian Edition, or Lubuntu are all very light but full-featured Debian-based distros. But 256 MB of RAM ain't much. If one of those doesn't run acceptably well, you may be better off with Puppy or Slax.

---

### Post by gwilson on 2011-05-05
I agree that Crunchbang Linux XFCE would be a good choice. I have Crunchbang running on 400 MHz and 600 MHz laptops with under 200 MB of ram. Both of these dinosaurs are pretty darned functional, and your system is way ahead of these. You'll also be able to run up-to-date apps like Firefox 4 with no issues. You can choose between XFCE and OpenBox for your desktop or install something else. Give it a try.

---

### Post by jramshu on 2011-05-05
Might want to consider running memtest86 from the cd, never know. Not very much memory there and if it's half bad you've lost a lot. I hear it can take several hours to run. 
Just a suggestion.

---

### Post by mastablasta on 2011-05-05
It's not the RAM problem. if any of you would read the system requirements you wouldn't say htings like not enough RAM, you have too little ram and similar rubish.
 
I am running Ubuntu 10.04 on 224 RAM just fine.
 
The problems as it was mentioned is the graphics card and poor driver for it. the OP never gave his card but indeed it is probably an old intel which wasn't much in any system. and troubleshooting starts here not RAM.
 
Also in my case Ubutnu and especially Xubuntu don't run propperly in live session but run fine on install.
 
Adition - it would be a good idea to use text installer so that it install propperly on the computer first. then you can try to solve the drivers issue.
 
---
 
**>  System Requirements**> 
 
The minimum memory requirement for Ubuntu 11.04 is 384 MB of memory for Ubuntu Desktop. Note that some of your system's memory may be unavailable due to being used by the graphics card. If your computer has only the minimum amount of memory, the installation process will take longer than normal; however, it will complete successfully, and the system will perform adequately once installed. 
The minimum memory requirement for Ubuntu Server 11.04 is 128 MB of memory. Systems with less memory may be able to select "Install Ubuntu" from the boot menu to run just the installer, rather than the whole desktop, or may be able to use the alternate install CD

 
And this is ment porbably to run Unity on it or soemthing as GNOME really needs abotu 140MB-160MB ram to run. not to mention XFCE or LXDE...
 
With minimal instal ISO you need much much less RAM.

---

### Post by Mashepherd on 2011-05-05
I would also recommend Lubuntu, i installed it on my sister's old laptop that was about 10/11 years old after i'd tries xbubuntu and Lubuntu worked like a dream, runs really fast now

---

### Post by ravij96 on 2011-05-05
Ill try crunchbag when I get home. Also sorry I didn't mention it but my computer does have an Intel chip.

---

### Post by NightwishFan on 2011-05-05
Puppy was already mentioned: [http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

Pros: Designed specifically for use in low memory situations. Good set of default packages. Simple and easy to use. Is very easy to use as a live distro as well.
Cons: Not much software easily available for it.



Or Debian Stable/Oldstable: [http://www.debian.org/](http://www.debian.org/)

Pros: Very universal operating system. Well tested and debugged. Lightweight and fast. Supported for a long time.
Cons: You might need to install a few packages you want to have a full featured install.

---

### Post by ravij96 on 2011-05-05
I was actually already going to try puppy, burned a CD but didn't have time to try it. Also are you sure they will work on my computer :/

---

### Post by khaozzer0 on 2011-05-05
Really no one mentioned Archlinux....it ran really fast on my old laptop.

---

### Post by ravij96 on 2011-05-05
Alright when I get home I am going to be putting puppy linux onto my computer because I feel it is the best choice.  I may upgrade the RAM to 1 gb then try another distro but I need this comp up today so it is my only choice right now. Thanks for the help I'll post how it goes after the install.

---

### Post by rolnics on 2011-05-05
Puppy is the way to go!

I had it running on a P3 with 512mb.....after a scrapped it together....I'm sure it did have 256mb before. Plus, you can use Ubuntu repositories as well! It's perfect!

---

### Post by verymadpip on 2011-05-05
+1 for Lubuntu.  I'd use the alternate install CD.
I've always had problems with Puppy's wireless.  I could just be a bit dense though.

---

### Post by michaelzap on 2011-05-05
> **mastablasta said:**
> It's not the RAM problem. if any of you would read the system requirements you wouldn't say htings like not enough RAM, you have too little ram and similar rubish.

Well, I actually have a lot of experience installing various distros on old computers with limited resources, and I think that RAM is definitely a limiting factor. Try playing a video compressed with h.264 in a browser with no RAM to spare and you'll see what I mean. A system can install and start up fine but still not be all that usable in real-life situations, so it depends on what youwant  to do with it.

---

### Post by ravij96 on 2011-05-05
The wireless won't be a problem since its a desktop and the reason I'm going with it is for the ubuntu repertory support.

---

### Post by ravij96 on 2011-05-05
Also, I am upgrading the RAM to 1gb, I would do 2 but I cant afford it right now, and that will also hopefully speed up things.

---

### Post by ravij96 on 2011-05-05
Alright I have a question how do I install it to the hard drive and making it my main os.  I want to replace windows xp with linux.

---

### Post by NoNameWill on 2011-05-05
I ran Xubuntu 10.04 on a celeron of similar specs and age except it had more RAM and a Nvidia card. Nothing special on the vid card just a Geforce 5200.

---

### Post by NoNameWill on 2011-05-05
> **ravij96 said:**
> Alright I have a question how do I install it to the hard drive and making it my main os.  I want to replace windows xp with linux.

Just change the boot order in BIOS to the optical drive.

---

### Post by ravij96 on 2011-05-05
Alright also do you think after installing 1 gb of ram my computer will be able to run xubuntu?

---

### Post by lykwydchykyn on 2011-05-05
> **ravij96 said:**
> Alright also do you think after installing 1 gb of ram my computer will be able to run xubuntu?

Absolutely.  1Gb is more than sufficient.

That doesn't mean your graphics chip will be compatible.

Did you manage to get a desktop to load?

---

### Post by StrayEddy on 2011-05-05
Puppy Linux or Slitaz FTW.
 
Also you could try Slax.

---

### Post by ravij96 on 2011-05-05
> **lykwydchykyn said:**
> Absolutely.  1Gb is more than sufficient.

That doesn't mean your graphics chip will be compatible.

Did you manage to get a desktop to load?

The desktop loaded but the background was gray and nothing would open.  I connected the computer to the internet and windows xp decided to install 200 updates there is only 5 more left, then I am going to try lubuntu again.

---

### Post by WhiteNoiseParser on 2011-05-05
Damn small linux is good too.  I have heard of that running on 486 hardware.

---

### Post by lykwydchykyn on 2011-05-05
Not to pick on anyone trying to help, but let's all keep in mind this is a Pentium 4 2 GHz machine that now has 1 Gb of RAM in it.  This thing could probably decently run just about any Linux distro out there, nevermind a medium-weight Ubuntu spinoff like Xubuntu or Lubuntu.

There's no reason to put up with the limitations of some uber-lightweight micro-distro that was designed to keep the Pentium II alive.

Both my desktops at home are older than this and have only half a gig of RAM each, yet we run Ubuntu with LXDE, XFCE and even KDE (albeit the latter slowly and without compositing) just fine.

---

### Post by NoNameWill on 2011-05-05
> **lykwydchykyn said:**
> 
Both my desktops at home are older than this and have only half a gig of RAM each, yet we run Ubuntu with LXDE, XFCE and even KDE (albeit the latter slowly and without compositing) just fine.

Actually I was misleading on running xubuntu. I didn't mean to be. I installed Ubuntu then installed XFCE desktop. The onboard graphics was Intel graphics chipset but like I said there was a nvidia card in the machine. 
The card wasn't special just a pci FX5200 (not geforce). I have seen these on the second hand market for 10 dollars and under.

---

### Post by ravij96 on 2011-05-05
Ok I am starting to give up Lubuntu loads the desktop but the bars don't show up.  Also, Puppy Linux refuses to start.  I don't think this computer wants linux.

---

### Post by ravij96 on 2011-05-05
Ok I got puppy working I'm going to try lubuntu again and if it doesn't work I'll just stick with this.

---

### Post by ravij96 on 2011-05-05
Ok I got puppy working thanks for the help guys.

---

