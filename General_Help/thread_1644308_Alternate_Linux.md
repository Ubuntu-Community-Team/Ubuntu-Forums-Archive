---
title: "Alternate Linux"
date: 2010-12-13
forum: General Help
---

### Post by katykat on 2010-12-13
As I mentioned on another thread, I have 2 Ubuntus - Jaunty and Meerkat - as separate drives on my secondary IDE channel. 

I am removing Jaunty. Meerkat blows it away. And is certainly my preferred OS. 

However I am looking for a replacement for Jaunty that is more flexible in certain key areas than Ubuntu appears to be.

I dont want to be restricted to Debian versions of things like Perl, MySQL, PHP and others. 
I can run LAMPP, but I would prefer to compile and have the versions of my choice as part of a main test system (apart from Meerkat that is). 

I have had enough nightmares in Jaunty with things getting broken and spiralling  out of control. I want a distro that doesnt rely on the GUI and its attendant utilities, but can run them when called. Meerkat is stable and has resisted me breaking it so far, but I do not want to push my luck. I have too much time invested in it. 

I intend to use Meerkat as my primary system on the machine, but want an alternative to *PLAY* with. 

Any ideas? 

Slackware?????

---

### Post by Verbeck on 2010-12-13
fedora?

---

### Post by katykat on 2010-12-14
Thanks for the suggestion.

I see Fedora 14 does not have a default Perl.

That is a good thing. 
I want to add my own. 

Ubuntu integrates Perl, and a mismatched module can putz up the system.

Its software selection does not seem as rubust as Debian, but its not what I really want, as Meerkat is my choice system. This is something I can play with.

---

### Post by oldos2er on 2010-12-14
Yes, Slackware, Arch....

---

### Post by QLee on 2010-12-14
[QUOTE=katykat]...
I want to add my own. 
... 
This is something I can play with.[/QUOTE]

I agree with olddos2er about Slackware, although I haven't tried Arch.

...in addition, since you want to play, and presumably learn from that play, you might want to consider, Linux From Scratch:
[http://www.linuxfromscratch.org/lfs/](http://www.linuxfromscratch.org/lfs/)

---

### Post by katykat on 2010-12-14
> **QLee said:**
> I agree with olddos2er about Slackware, although I haven't tried Arch.

...in addition, since you want to play, and presumably learn from that play, you might want to consider, Linux From Scratch:
[http://www.linuxfromscratch.org/lfs/](http://www.linuxfromscratch.org/lfs/)


I just downloaded LFS and can see the possibilities, especially for building specialiazed boot disks. 

I have played a little with Arch, definitely a start from scratch system...

Slackware, my old favorite, I see has FAQs that havent been updated in 10 years. 

Scary....

---

### Post by QLee on 2010-12-14
[QUOTE=katykat]...
Slackware, my old favorite, I see has FAQs that havent been updated in 10 years. 

Scary....[/QUOTE]

The configuration files used to be well annotated, I haven't used it since version 9 though.

---

### Post by WorMzy on 2010-12-14
I use Arch, it's very flexible, and allows you to cherry pick packages (rather than restricting your options with false dependencies like Ubuntu does).

One thing worth noting is that on Arch, Python = Python 3, not Python 2. On Ubuntu, the opposite is true (or was, I'm not up-to-date with Ubuntu developments).

Arch is not for people afraid of the CLI though. All a base install gives you is the very basics, it's up to you to configure you internet connection and download and install the system you want -- including the desktop environment.

---

### Post by TeoBigusGeekus on 2010-12-14
> **WorMzy said:**
> I use Arch, it's very flexible, and allows you to cherry pick packages (rather than restricting your options with false dependencies like Ubuntu does).

One thing worth noting is that on Arch, Python = Python 3, not Python 2. On Ubuntu, the opposite is true (or was, I'm not up-to-date with Ubuntu developments).

Arch is not for people afraid of the CLI though. All a base install gives you is the very basics, it's up to you to configure you internet connection and download and install the system you want -- including the desktop environment.

+100000000
Arch, arch and arch again!

---

### Post by katykat on 2010-12-15
While Arch sounds defintiely interesting - building a system up from scratch is maybe a project for the future: A bit short on time these days. 

I installed Fedora 14, after disconnecting Meerkat and putting a junk XP disk in. 

To my horror I realized that Fedora doesnt use grub2, and that it didnt even offer me a menu to boot to the XP system. I restored the MBR to the XP drive so that it returned to normal function. 

Then I reconnected Meerkat, and plugged in another XP boot drive, this one with grub2 already on it.
Booted to Meerkat, did update-grub, it found the Fedora - and works fine with a three way boot now. 

I might not keep Fedora though. It is very annoyiong and I hate systems that dont let me log in as root. If I want to see 'access denied' I will stick with Windoze. Time will tell.

I was also disappointed that Fedora doesnt come with a working Nvidia driver, even though my card is a bit old. Meerkat has no problems with the card. 

I also noticed that  when I went to remove a bunch of useless languages, that it wanted to take half the system with it. Dependency hell. 

Arch is looking better.....

---

### Post by WorMzy on 2010-12-15
Arch uses grub legacy too, although grub2 is available in the "extra" repository. Arch only gives you a root account by default, so you'll like that; still, I feel compelled to point out that using root as your user = bad, but I'll assume that you know the risks and leave the decision up to you.

---

### Post by Simian Man on 2010-12-15
> **katykat said:**
> I might not keep Fedora though. It is very annoyiong and I hate systems that dont let me log in as root. If I want to see 'access denied' I will stick with Windoze. Time will tell.
Fedora actually comes with a root account and Ubuntu does not.  Unless you mean logging in graphically as root - in which case that's bad practice no matter what.

> **katykat said:**
> I was also disappointed that Fedora doesnt come with a working Nvidia driver, even though my card is a bit old. Meerkat has no problems with the card. 
You can get a working Nvidia driver from RPM Fusion.

---

### Post by katykat on 2010-12-17
> **Simian Man said:**
> Fedora actually comes with a root account and Ubuntu does not.  Unless you mean logging in graphically as root - in which case that's bad practice no matter what.
You can get a working Nvidia driver from RPM Fusion.

At least in Ubuntu I have the option of switching between Root and User. 
I use mc and othe rfile managers. I do not ever 'accidentally' delete files unintentionally, though I may at times regret it afterwards. I've run Linux on and off through the years, since v0.9 and have never experieonced a problem when running as root. 

This ia a peer-to-peer local network. Anyone at a keyboard should have absolute control, short of remote desktop functions (verboten here). 

The GUIs are however rather new to me, so could someone post a link as to exactly *why* they are to be dreaded as root. 

Mind you, I have no qualms about dropping back privelidges when doing simple things like cruising the web, but for reconfiguration and maintenance, which is something I often do, sudo just dont cut it. 

As a matter of fact I currently have a bug in the Meerkat system that does not even let me boot into a user account.......
Someday I'll get around to that, but have much larger issues on the system now. Such as configuring a server and installing develpment apps. 

I am behind a hardware firewall, with hosts.deny set to ALL:ALL , if that is any help....

---

### Post by andrew.46 on 2011-01-01
Hi katykat,

> **katykat said:**
> Slackware, my old favorite, I see has FAQs that havent been updated in 10 years. 

Scary....

There are very comprehensive documents included in the root directory of the installation disk. Have a quick look here:

[http://slackware.osuosl.org/slackware-13.1/](http://slackware.osuosl.org/slackware-13.1/)

Andrew

---

