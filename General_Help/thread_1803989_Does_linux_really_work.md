---
title: "Does linux really work?"
date: 2011-07-14
forum: General Help
---

### Post by ebu on 2011-07-14
Hi there,
I'm just trying to figure out if the level of instability i'm experiencing with ubuntu  is higher than average. I'd be very thankful if you reply following answers:

1) Are you running ubuntu on desktop or notebook?
2) Ubuntu version?
3) How many times per day your system crashes (reboots itself)?
4) How many times per day it becomes so slowly that you decided to reboot it manually?
5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?
6) Did you do something special to make your system more stable?

My answers to the questions above are as following:

1) notebook (HP EliteBook 8440p, 8G RAM)
2) 11.04, Gnome
3) once in a day or two
4) once
5) 3-5
6) no

As you may guess I'm quite frustrated with this situation.  When i worked on Windows the figures were at least 10 times lower. So I'm now trying to figure out if it worth to somehow fix it or give up and move back to Windows.

Best regards, Eugene.

---

### Post by iclestu on 2011-07-14
> **ebu said:**
> Hi there,
I'm just trying to figure out if the level of instability i'm experiencing with ubuntu  is higher than average. I'd be very thankful if you reply following answers:

1) Are you running ubuntu on desktop or notebook?
2) Ubuntu version?
3) How many times per day your system crashes (reboots itself)?
4) How many times per day it becomes so slowly that you decided to reboot it manually?
5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?
6) Did you do something special to make your system more stable?

My answers to the questions about are as following:

1) notebook (HP EliteBook 8440p, 8G RAM)
2) 11.04, Gnome
3) once in a day or two
4) once
5) 3-5
6) no

As you may guess I'm quite frustrated with this situation.  When i worked on Windows the figures were at least 10 times lower. So I'm now trying to figure out if it worth to somehow fix it or give up and move back to Windows.

Best regards, Eugene.

1) both
2) kubuntu 11.04
3) never
4) never
5) almost never - like cant remember last time specifically but know I have done it
6) no

---

### Post by haqking on 2011-07-14
laptop
10.10
never
never
never
i paid attention

---

### Post by nothingspecial on 2011-07-14
1) 2 desktops, 1 laptop, 2 netbooks and one server
2) 11.04, 11.10, 10.04
3) Never
4) Never
5) Very rarely
6) No

What's your actual problem?

---

### Post by arena001 on 2011-07-14
You must be having some hardware problem or hardware incompatibility with ubuntu etc. I can't believe that someone saying MS is more stable then Ubuntu (Linux)

---

### Post by ebu on 2011-07-14
> **nothingspecial said:**
> What's your actual problem?

Unfortunately i don't have any exact problem suitable for asking on the forum about. All troubles described in questions happen to me regularly.

---

### Post by ebu on 2011-07-14
> **arena001 said:**
> You must be having some hardware problem or hardware incompatibility with ubuntu etc. 

This can be cause for sudden reboots, but i can't find anything suspicious in the logs. And i don't think hardware  incompatibility can cause LibreOffice or Firefox to slowdown.

---

### Post by Karlchen on 2011-07-14
Hello, Eugene.
> 1) Are you running ubuntu on desktop or notebook?Both. The office machine is a Dell notebook.
>  2) Ubuntu version?v10.04.2 (Lucid Lynx) 32-bit
> 3) How many times per day your system crashes (reboots itself)? Never.
> 4) How many times per day it becomes so slowly that you decided to reboot it manually? Never.
>  5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen? There is one Java app which needs to be killed every once in a while (kill <pid>). But the same Java app needs to be killed every once in a while on Windows as well. The scenario in which this Java app needs to be killed is well defined and predictable and unrelated to the OS it has been started on.
>  6) Did you do something special to make your system more stable? No. Install only software from the Canonical repositories. Install software not available in the Canonical repostiories from other official sources like Ubuntuzilla or Mozilla or Oracle. No nightly builds, no experimental builds on my machines.

_Summary:_
Does Linux really work? Well, Lucid Lynx definitely does and has been doing so for the past 13 months here.

Cheers,
Karl

---

### Post by coffeecat on 2011-07-14
1 - 1 desktop, 2 laptops, 1 netbook.
2 - Natty (mostly)
3 - never
4 - never
5 - rarely
6 - no

@ebu, rather than looking for a hardware incompatibility I would suggest looking for a hardware fault. The first thing that comes to mind is memory. Because of the different way in which Linux addresses memory it is more likely to uncover a memory fault than Windows, particularly when this is in the upper registers. You could try memtest but that can be very unrewarding. Faults can be intermittent and a negative memtest means only that any fault, if present, didn't manifest itself during the test. The only meaningful memtest is a positive one.

So.. how to test? You have 8GB which is quite a lot. Is that 4 x 2GB or 2 x 4GB? Try taking out all sticks except one and running the machine on that one for a few days. Then the next stick and then the next and so on. If one stick only is faulty, that *might* show it up. However, tracking down faulty memory can be extremely frustrating.

---

### Post by Topsiho on 2011-07-14
> **ebu said:**
> Hi there,
I'm just trying to figure out if the level of instability i'm experiencing with ubuntu  is higher than average. I'd be very thankful if you reply following answers:

1) Are you running ubuntu on desktop or notebook?
2) Ubuntu version?
3) How many times per day your system crashes (reboots itself)?
4) How many times per day it becomes so slowly that you decided to reboot it manually?
5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?
6) Did you do something special to make your system more stable?

My answers to the questions about are as following:

1) notebook (HP EliteBook 8440p, 8G RAM)
2) 11.04, Gnome
3) once in a day or two
4) once
5) 3-5
6) no

As you may guess I'm quite frustrated with this situation.  When i worked on Windows the figures were at least 10 times lower. So I'm now trying to figure out if it worth to somehow fix it or give up and move back to Windows.

Best regards, Eugene.

1) a number of computers: desktops, laptops, netbook
2) 10.04, 11.04, others like Mint, Gnome
3) almost never (I never say never :) )
4) No slowdowns at all. Only the netbook in which the very small and bad SSD is probably the bottleneck
5) almost never. FF did sometimes play up, but now that is history
6) No, not really

If something happens that is out of this order, then it is ALWAYS hardware. Might be defective memory (did you test this: as Linux uses memory very effectively, it may use part of the memory which Windows never uses). It might be a failing hard disk (what does disk utility say?) or other, such as a driver for a graphics adapter which is not so good.

My guess (for the TS) is: check your memory, a good many passes. Sometimes a memory fault only shows up after some passes. 

Topsiho

---

### Post by Grenage on 2011-07-14
Such sporadic instabilities (especially across installs) tend to be hardware related.

> 1) Are you running ubuntu on desktop or notebook?
2) Ubuntu version?
3) How many times per day your system crashes (reboots itself)?
4) How many times per day it becomes so slowly that you decided to reboot it manually?
5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?
6) Did you do something special to make your system more stable

1) Laptop and several desktops.
2) 11.04
3) None, I can only recall one crash - that's for all machines in the last 5 years.
4) None; I only reboot for kernel updates, and I never turn off my main work PC.
5) None; if there was a daily average, it would be less than 0.1.
6) Other than using quality components and using decent software, no.

---

### Post by haqking on 2011-07-14
> **ebu said:**
> Hi there,
I'm just trying to figure out if the level of instability i'm experiencing with ubuntu  is higher than average. I'd be very thankful if you reply following answers:

1) Are you running ubuntu on desktop or notebook?
2) Ubuntu version?
3) How many times per day your system crashes (reboots itself)?
4) How many times per day it becomes so slowly that you decided to reboot it manually?
5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?
6) Did you do something special to make your system more stable?

My answers to the questions about are as following:

1) notebook (HP EliteBook 8440p, 8G RAM)
2) 11.04, Gnome
3) once in a day or two
4) once
5) 3-5
6) no

As you may guess I'm quite frustrated with this situation.  When i worked on Windows the figures were at least 10 times lower. So I'm now trying to figure out if it worth to somehow fix it or give up and move back to Windows.

Best regards, Eugene.

how can it be 10 times lower than 3-5 and once in a day or two ? ;-)

So i see you have 8gb ram which means you are most likely using the 64 bit version, what apps are you using ?
What problems causes the problems ?

we cant help fix it with what you said ;-)

---

### Post by ebu on 2011-07-14
> **coffeecat said:**
> 
So.. how to test? You have 8GB which is quite a lot. Is that 4 x 2GB or 2 x 4GB? Try taking out all sticks except one and running the machine on that one for a few days. Then the next stick and then the next and so on. If one stick only is faulty, that *might* show it up. However, tracking down faulty memory can be extremely frustrating.

Frankly i don't know if it's 4 x 2GB or 2 x 4GB. The notebook is provided by company so i didn't care about its internals and I can't open it and take one of the memory sticks out. Also even if I ask support to do so I won't be able to work - 4 GB are not enough to run oracle i need for development. But of course I'll try to check it somehow, at least with some software util. Thank you for this suggestion.

---

### Post by ebu on 2011-07-14
> **haqking said:**
> how can it be 10 times lower than 3-5 and once in a day or two ? ;-)

Well, it can be 0.3-0.5 per day :) Statistically speaking ;)

> **haqking said:**
> 
So i see you have 8gb ram which means you are most likely using the 64 bit version, what apps are you using ?


Yes, you're correct, i'm using 64 bit version.

> **haqking said:**
> What problems causes the problems ? we cant help fix it with what you said ;-)

That is probably my main problem - i don't do anything special with it (all installations are from trusted sources like ubuntu soft center, oracle, eclipse) and thus can't provide more specific descriptions of my problems. 

The only 'special' thing I use is disk encryption (the one which encrypts whole partition). Does anybody of you use it?

---

### Post by WorMzy on 2011-07-14
**1) Are you running ubuntu on desktop or notebook?**
I only have a desktop.

**2) Ubuntu version?**
I have 9.10, 10.04, and 11.04 installed, all running GNOME2 (and Unity, in 11.04's case). I also have four versions of Arch Linux -- two running GNOME2, one running Openbox, and one with just virtual terminals and a framebuffer. These days I spend most of my time on my Openbox and VT installs.

**3) How many times per day your system crashes (reboots itself)?**
None. Current uptime: 1d 10h 38m, the last time I reset was because there was a kernel update (3.0-rc6 - 3.0-rc7)

**4) How many times per day it becomes so slowly that you decided to reboot it manually?**
None, but I do need to periodically restart xcompmgr on my Openbox installation.

**5) How many times per day you have to kill something (office app, eclipse, firefox etc) because it become frozen?**
There have been a few instances of this happening, but on average? 0 times a day.

**6) Did you do something special to make your system more stable?**
Not purposely. I compile my own kernel to cut out all the bloat that I don't need. I use nouveau for KMS. And I use systemd for the boot time benefits.

---

### Post by Ghost_Mazal on 2011-07-14
> **ebu said:**
> Hi there,
I'm just trying to figure out if the level of instability i'm experiencing with ubuntu  is higher than average. I'd be very thankful if you reply following answers:

1) Are you running ubuntu on desktop or notebook?
2) Ubuntu version?
3) How many times per day your system crashes (reboots itself)?
4) How many times per day it becomes so slowly that you decided to reboot it manually?
5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?
6) Did you do something special to make your system more stable?

Best regards, Eugene.

1. I run Kubuntu on the laptop in my sig as well as on a desktop (Core2Duo E6850)
2. Kubuntu 11.04 64bit (all updates done)
3. None
4. None
5. None
6. Nope. I always only add the essentials and a few extra apps I use.

---

### Post by iiiears on 2011-07-14
Hello, 

Take a look at /var/log/
sudo nautilus /var/log


Linux works better everyday.

(Don't believe me download 
Ubuntu Warty Warthog or
Redhat 5.0 - E-eek!)

---

### Post by DanaLou on 2011-07-14
**1) Are you running ubuntu on desktop or notebook?**
Laptop: HP Pavilion dv5

**2) Ubuntu version?**
11.04

**3) How many times per day your system crashes (reboots itself)?**
Never

**4) How many times per day it becomes so slowly that you decided to reboot it manually?**
Never

**5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?**

Never
**6) Did you do something special to make your system more stable?**

Yes; installed Ubuntu ;)

---

### Post by ebu on 2011-07-14
> **iiiears said:**
> Hello, 

Take a look at /var/log/
sudo nautilus /var/log


Could you please give me a hint on what to look for? There are hundreds of error messages, hardly i will ever by able to fix all of them. 

> **iiiears said:**
> 
Linux works better everyday.

(Don't believe me download 
Ubuntu Warty Warthog or
Redhat 5.0 - E-eek!)

Well, about 10 years ago i worked for a company which used linuxes (Debians) too. It was much more stable, especially if compared with Windows of these times, but support for hardware was poor.

---

### Post by Rasa1111 on 2011-07-14
> **ebu said:**
> Hi there,
I'm just trying to figure out if the level of instability i'm experiencing with ubuntu  is higher than average. I'd be very thankful if you reply following answers:

 Hi, 

**1) Are you running ubuntu on desktop or notebook?**

Both

**2) Ubuntu version?**

Notebook/Laptop- 11.04 , 
Desktop 1- 10.10, 
Desktop 2- 10.04 , 
Desktop 3, 10.04

**3) How many times per day your system crashes (reboots itself)?**

Zero (0)

**4) How many times per day it becomes so slowly that you decided to reboot it manually?**

Never

**5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?**

Never
[B]
6) Did you do something special to make your system more stable?[/B]

Killed windows and installed Ubuntu. ;) :P

Really though, Nope. :KS

---

### Post by Ad@m on 2011-07-14
> **coffeecat said:**
> 

The first thing that comes to mind is memory. ***Because of the different way in which Linux addresses memory it is more likely to uncover a memory fault than Windows***, particularly when this is in the upper registers. You could try memtest but that can be very unrewarding. Faults can be intermittent and a negative memtest means only that any fault, if present, didn't manifest itself during the test. The only meaningful memtest is a positive one.



In other words Windows is more resilient to faulty memory. That doesn't sound right.

---

### Post by matt_symes on 2011-07-14
Hi

Do you have a support question. The only reason i ask is this is your first thread on these forums.

At least give us some inclining as to the issues you may be experiencing. 

It sounds more as if you are trying to conduct a survey ;)

Kind regards

---

### Post by Grenage on 2011-07-14
> **Ad@m said:**
> In other words Windows is more resilient to faulty memory. That doesn't sound right.

Not more resilient, just less likely to encounter them; I've seen it on several machines, as I'm sure many others here have.

---

### Post by Elaztic on 2011-07-14
1) 1 desktop and 1 laptop at home but have installed several for family members.
2) 11.04 on desktop and 10.10 on laptop
3) I think I have experienced it once ever.
4) never
5) Perhaps once a week.
6) no

Note: I know a few applications will crash if I perform certain actions but they are known bugs.

---

### Post by Ad@m on 2011-07-14
Sorry for going off topic.

> **Grenage said:**
> Not more resilient, just less likely to encounter them; I've seen it on several machines, as I'm sure many others here have.

You are impliedly saying Windows is a more stable platform given you are less likely to encounter the effects of faulty memory.

Hence, Windows is more resilient to faulty memory.

---

### Post by Grenage on 2011-07-14
> **Ad@m said:**
> Sorry for going off topic.



You are impliedly saying Windows is a more stable platform given you are less likely to encounter the effects of faulty memory.

Hence, Windows is more resilient to faulty memory.

Not at all, it's just less likely to use the memory that's defective.  Both Windows and Linux are very stable platforms.

---

### Post by fooman on 2011-07-14
1)4 desktops, 3 notebooks, 3 netbooks
2)11.10 on 1 hard drive in this machine, 11.04 on another, 11.04 on 2 of the notebooks.... 10.10 on the rest of the machines
3)never
4)never
5)per day=never....has happened occasionally though
6)a few tweaks to make flash work better on 64bit machines

---

### Post by ebu on 2011-07-14
> **matt_symes said:**
> Hi

Do you have a support question. The only reason i ask is this is your first thread on these forums.



So far the only one i can come up with is:

     > 
                                                                  [I]                     Originally Posted by **iiiears**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11046078#post11046078")
Take a look at /var/log/
sudo nautilus /var/log[/I]
                                 
Could you please give me a hint on what to look for? There are  hundreds of error messages, hardly i will ever by able to fix all of  them. 

> It sounds more as if you are trying to conduct a survey ;)yes, but that's just for me do decide what to do with it.

---

### Post by Jouke74 on 2011-07-14
I'll play along:

Laptop: Asus EEE 1001PX 

2) version: 10.10 and for some time tried 11.04.

3) reboots: 10.10 Never vs. 11.04 Never.

4) slowness: 10.10 never vs. 11.04 a few times I wanted too reset.

5) kill apps: 10.10 rarely vs. 11.04 frequently. 

6)

10.10 is a minimal Ubuntu install with a 2.6.32 Hardy(!) kernel. I selected this kernel because as compared to kernels 2.6.35 - 38 it uses waaaaaaay less power and gives therefore much better battery life. Installed are Ubunutu minimal and Gnome-core + utils + network manager + the apps I want. No desktop effects (they do work fine if I install them) no fancy stuff, just Gnome and speedy use. 

11.04 I tried a minimal install as well as a full install. Minimal install cannot run and also installs compiz+unity+lots of programs (why??). With a full  install the laptop is working, but slow and not-responsive often. Had to jump through quite an amount of hoops to get the 11.04 desktop on screen at all, because after the initial install I have a black screen of death (like many other people with Intel graphics). The 11.04 distro is buggy, and the supposed alternatives are not working very well (classic desktop, unity 2d, even tried Kubuntu). It sucks batterylife like crazy, fan goes wild often and it is a gamble if I get my work done in time. 

Hence I went back to 10.10 and downloaded all debs into a mirror repository on HD. If Maverick gets unsupported at least I can still install stuff and run Gnome 2 for a while until either Gnome 3 is back to efficient use or unity is running without issues.

---

### Post by ebu on 2011-07-14
> **Jouke74 said:**
> 
11.04 I tried a minimal install as well as a full install. Minimal install cannot run and also installs compiz+unity+lots of programs (why??). With a full  install the laptop is working, but slow and not-responsive often. Had to jump through quite an amount of hoops to get the 11.04 desktop on screen at all, because after the initial install I have a black screen of death (like many other people with Intel graphics). The 11.04 distro is buggy, and the supposed alternatives are not working very well (classic desktop, unity 2d, even tried Kubuntu). It sucks batterylife like crazy, fan goes wild often and it is a gamble if I get my work done in time. 

Hence I went back to 10.10 and downloaded all debs into a mirror repository on HD. If Maverick gets unsupported at least I can still install stuff and run Gnome 2 for a while until either Gnome 3 is back to efficient use or unity is running without issues.

Ok, that's already something quite close to my experience. The funny thing is that i somehow managed to install 11.04 without understanding what i'm doing. It offered some update, i did it. The warning from local support to not upgrade to 11.04 arrived next morning, but it was already too late :)

---

### Post by desnaike on 2011-07-14
> **ebu said:**
> Hi there,
I'm just trying to figure out if the level of instability i'm experiencing with ubuntu  is higher than average. I'd be very thankful if you reply following answers:

1) Are you running ubuntu on desktop or notebook?
2) Ubuntu version?
3) How many times per day your system crashes (reboots itself)?
4) How many times per day it becomes so slowly that you decided to reboot it manually?
5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?
6) Did you do something special to make your system more stable?

My answers to the questions about are as following:

1) notebook (HP EliteBook 8440p, 8G RAM)
2) 11.04, Gnome
3) once in a day or two
4) once
5) 3-5
6) no

As you may guess I'm quite frustrated with this situation.  When i worked on Windows the figures were at least 10 times lower. So I'm now trying to figure out if it worth to somehow fix it or give up and move back to Windows.

Best regards, Eugene.
1. Both
2. 10.10 on desktop,10.04 on laptop.
3. None
4. Never
5. none
6. +1 with the person that said pay attention.

---

### Post by mastablasta on 2011-07-14
> **coffeecat said:**
> @ebu, rather than looking for a hardware incompatibility I would suggest looking for a hardware fault. The first thing that comes to mind is memory. Because of the different way in which Linux addresses memory it is more likely to uncover a memory fault than Windows, particularly when this is in the upper registers. You could try memtest but that can be very unrewarding. Faults can be intermittent and a negative memtest means only that any fault, if present, didn't manifest itself during the test. The only meaningful memtest is a positive one.
 .
 
aside from RAM fault it can also be bad capacitors or system overheating.
 
otherwise stability really isn't the problem of linux. if anything linux is stable. problems are elsewhere (hardware & software support...)

---

### Post by Topsiho on 2011-07-14
First: I want to react on the remark that Windows appears to be more resilient to defective memory than Linux, if it fails in Linux and not in Windows. That is putting things bottom up.
Fact is that Linux uses memory more effectively. If you have, let's say 4 GB of RAM, you use 4 GB of RAM (more often), while in Windows you never or almost never reach that amount. So why have it anyway, in Windows. If the upper reaches of the memory is faulty, in Linux it's detected, while in Windows it is not.

But even if Windows is considered more resilient, from whatever considerations, having defective memory makes your system independable, and you should not trust any results you get with it.

But why I react here is that an upgrade is not the same as a clean install. I get that ebu has upgraded to 11.04, and now experiences trouble. An upgrade, which really is a huge update, is a risky process, that often (more often than not?) goes haywire, and leaves you with a buggy system.

So ebu might include the next question: did you do a clean install, or did you do an upgrade. AND: did you an upgrade from a previous version or from a version before that? (I think that the latter is impossible, except from LTS to LTS, so this might be silly).

Topsiho

---

### Post by ebu on 2011-07-14
> **Topsiho said:**
>  So ebu might include the next question: did you do a clean install, or did you do an upgrade. AND: did you an upgrade from a previous version or from a version before that? (I think that the latter is impossible, except from LTS to LTS, so this might be silly)

I did upgrade, i'm not sure, but I think it was 10.10. Before upgrading i worked no more than couple of weeks with ubuntu so i don't remember exactly.

---

### Post by Topsiho on 2011-07-14
OK, then you might try your mileage with doing a clean install this time. But at the same time: 11.04 is considered to be not a very good version of Ubuntu by some (and me), so I advise you to go for Ubuntu 10.04 LTS (after July 21st the 10.04.3 version is available, which then is the latest version of 10.04, which will save you from having to download and install a great many updates).

Topsiho

---

### Post by ebu on 2011-07-14
> **Topsiho said:**
> OK, then you might try your mileage with doing a clean install this time. But at the same time: 11.04 is considered to be not a very good version of Ubuntu by some (and me), so I advise you to go for Ubuntu 10.04 LTS (after July 21st the 10.04.3 version is available, which then is the latest version of 10.04, which will save you from having to download and install a great many updates).

Topsiho

But this means a day (at least) out of work... will i be able to reuse encrypted partition with clean install and just reformat / (i have everything installed in /opt)?

---

### Post by malspa on 2011-07-14
1) Are you running ubuntu on desktop or notebook? **Both.**
2) Ubuntu version? **Lucid and Natty, along with several other distros.**
3) How many times per day your system crashes (reboots itself)? **None. Can't remember the last time that has happened here, or if it ever has.**
4) How many times per day it becomes so slowly that you decided to reboot it manually? **Never.**
5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen? **This isn't normal, either. Happens on occasion, but not every day, not even once a week or anything like that.**
6) Did you do something special to make your system more stable? **No.**

> **ebu said:**
> I'm just trying to figure out if the level of instability i'm experiencing with ubuntu is higher than average.

Much higher.

> **ebu said:**
> As you may guess I'm quite frustrated with this situation.  When i worked on Windows the figures were at least 10 times lower. So I'm now trying to figure out if it worth to somehow fix it or give up and move back to Windows.

I'd say it's definitely worth it.

---

### Post by el_koraco on 2011-07-14
I'd suggest you carve out a 10 GB partition, and do a clean install of 11.04 there. If your problems persist, try Ubuntu 10.10, Linux Mint 11, Fuduntu or Fedora - they're all pretty easy to work with. once you've found out which version you prefer, use it. 

Although, if your problems on Windows are 10 times less frequent tha in Linux, we're still talking about spontanious reboots, system crashes and the like once a week. Your problem is likely either hardware related, or has to do with drivers.

---

### Post by tommpogg on 2011-07-14
> **ebu said:**
> Hi there,
I'm just trying to figure out if the level of instability i'm experiencing with ubuntu  is higher than average. I'd be very thankful if you reply following answers:

1) Are you running ubuntu on desktop or notebook?
2) Ubuntu version?
3) How many times per day your system crashes (reboots itself)?
4) How many times per day it becomes so slowly that you decided to reboot it manually?
5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?
6) Did you do something special to make your system more stable?

My answers to the questions above are as following:

1) notebook (HP EliteBook 8440p, 8G RAM)
2) 11.04, Gnome
3) once in a day or two
4) once
5) 3-5
6) no

As you may guess I'm quite frustrated with this situation.  When i worked on Windows the figures were at least 10 times lower. So I'm now trying to figure out if it worth to somehow fix it or give up and move back to Windows.

Best regards, Eugene.

1) notebook and laptop
2) 10.10
1) 0
3) 0
5) Sometimes, but with applications that were not made to run on Ubuntu
6) +1 to the person who said "+1 to the person who said pay attention"

Eugene, have you tried a different version of Ubuntu? It seems that people are experimenting problems with Ubuntu 11.04. Personally, I suggest Ubuntu 10.04.

---

### Post by b1tchacked on 2011-07-14
1) Are you running ubuntu on desktop or notebook?
sony-vaio y-series

2) Ubuntu version?
Ubuntu 11.04 64-bit

3) How many times per day your system crashes (reboots itself)?
never

4) How many times per day it becomes so slowly that you decided to reboot it manually?
never

5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?
never

6) Did you do something special to make your system more stable?
Just a few tweaks to get my drivers working

---

### Post by ebu on 2011-07-14
> **tommpogg said:**
> 
Eugene, have you tried a different version of Ubuntu? It seems that people are experimenting problems with Ubuntu 11.04. Personally, I suggest Ubuntu 10.04.

I worked a bit with 10.something, but not enough to get any impression on stability.

---

### Post by Topsiho on 2011-07-14
I am not sure, no experience with encrypting. And I don't know what you mean that you have everything installed in /opt.

The usual install is that you have all your system files in /, and all the user files in /home, and that you have a swap partition, which is at least one or more times your ram.

Your experiences might be due to having "everything installed in /opt", which is very weird.

So doing an install you should create a partition for /  (say 10GB), a swap partition (amount depends on your ram), and the remaining for /home, which will contain your personal files, and those of the other users, if any.

That is 3 partitions. If you also have Windows, it uses also one or more partitions. As you can have only 4 (primary) partitions on one disk, you have to be creative: one primary partition you may sacrifice as a container for quite a number of logical partitions.

So for example on one of my computers the situation is like this:

sda1 contains the Windows partition.
sda2 is the container for the rest (called extended partition)
sda5 is the first logical partition, for /  (ext4, mountpoint is /)
sda6 is the second logical partition, for /home (ext4, mountpoint /home)
sda7 is the third logical partition (swap partition)

As for your encrypted files: I don't know how best to proceed.
You might backup them somewhere, unencrypted or both unencrypted and encrypted, and later put them back, if possible in the encrypted form.
But have the unencrypted files as a backup, to not to loose them if anything goes wrong.
If all goes well, you might get rid of the unencrypted files later, if you wish to do so (I wouldn't :) ).

Topsiho

---

### Post by Topsiho on 2011-07-14
To be more precise:

sda means the first disk, the following being sdb, sdc, ...
sda1 means the first primary partition on the first disk
Primary partitions are numbered sda1 .. sda4
Logical partitions are numbered from sda5.

In Windows disks and partitions are "numbered" from A:\, B:\ (floppies), and C:\, D:\  (hard disks and hd partitions).

In Linux there is only one file system, from / downwards in a single tree. This file system may extend over one or more disks.
In Windows flile systems extend downwards from C:\, D:\, etc, not counting the floppy disks.

Hope this helps ...

Topsiho

---

### Post by Vahe Nersesian on 2011-07-14
1) notebook (Compaq)
2) 11.04, Gnome
3) never
4) never
5) never
6) sometime I am running: apt-get autoclean autoremove

---

### Post by ebu on 2011-07-14
> **Topsiho said:**
> I am not sure, no experience with encrypting. And I don't know what you mean that you have everything installed in /opt.

i meant i have third-paty apps like oracle, eclipse etc installed to opt. sorry, didn't put it clear.

---

### Post by ebu on 2011-07-14
> **Vahe Nersesian said:**
> 6) sometime I am running: apt-get autoclean autoremove

mmm, is it safe to run without backing up all you work?

---

### Post by ssreddy555 on 2011-07-14
The answer is an emphatic YES & IT REALLY WORKS.

I have been using 11.04 since the time it is made available & I have no real problems with it except when I tried to play with Compiz & I find Classic's menu more convenient & use it.

On my desktop, I have a quad boot with Ubuntu 11.04 32 Bit, Mint 10 32 Bit, Mint 11 64 Bit & Windows 7 64 Bit on different partitions. My RAM is 2 GB.

On my netbook, I run Jolicloud, Win XP & Ubuntu 11.04 via WUBI. It has a 1 GB memory.

All have been functioning without a hitch. No crashes.

My experience with Linux has been extremely pleasant - I have been using it for the last 7 months -  & I have all but forgotten Windows.

---

### Post by ratcheer on 2011-07-14
**Does Linux really work?**

Yes. Yes it does.

Tim

---

### Post by UltraNEO* on 2011-07-14
> **ebu said:**
> 
1) Are you running ubuntu on desktop or notebook?
[B]
MacBook 4,1[/B] 2Gb RAM, 500Gb HD. No MacOS, just 100% Linux. 
**MacPro 5400 **Xeon 3.2Ghz, 20Gb RAM, RAID 5. Dual Boot MacOSX Snow Leopard on 1TB & Linux on 320Gb Drive.

> **ebu said:**
> 2) Ubuntu version? 

MacBook: 10.10
MacPro: 11.04

> **ebu said:**
> 3) How many times per day your system crashes (reboots itself)?

None.

> **ebu said:**
> 4) How many times per day it becomes so slowly that you decided to reboot it manually?

None. 

> **ebu said:**
> 5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?

System been up and running now for a fair few days and it's been really stable. Has been manually restarted to get web-server running but that's about it. 

> **ebu said:**
> 6) Did you do something special to make your system more stable?

Non, just updated the system with the most recent patches... And like my MacOSX, Ubuntu just works. 

Ain't sure why people are having issues with the installation, it's not like brain surgery is it?

---

### Post by johnnybgoode83 on 2011-07-14
1) Are you running ubuntu on desktop or notebook? NOTEBOOK

2) Ubuntu version? UBUNTU 10.10

3) How many times per day your system crashes (reboots itself)? ZERO

4) How many times per day it becomes so slowly that you decided to reboot it manually? - ZERO

5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen? - ONCE OR TWICE

6) Did you do something special to make your system more stable? - JUST INSTALLED IT

---

### Post by dFlyer on 2011-07-14
> **ebu said:**
> Hi there,
I'm just trying to figure out if the level of instability i'm experiencing with ubuntu  is higher than average. I'd be very thankful if you reply following answers:

1) Are you running ubuntu on desktop or notebook?
2) Ubuntu version?
3) How many times per day your system crashes (reboots itself)?
4) How many times per day it becomes so slowly that you decided to reboot it manually?
5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?
6) Did you do something special to make your system more stable?

My answers to the questions above are as following:

1) notebook (HP EliteBook 8440p, 8G RAM)
2) 11.04, Gnome
3) once in a day or two
4) once
5) 3-5
6) no

As you may guess I'm quite frustrated with this situation.  When i worked on Windows the figures were at least 10 times lower. So I'm now trying to figure out if it worth to somehow fix it or give up and move back to Windows.

Best regards, Eugene.

1) Dell 1735 Studio 4gig
2) 11.04 Unity
3) Never
4) Never
5) Never
6) No

Sorry to hear your having problems. I've been using Ubuntu since 6.06 and have found it to be very stable. The only time I had problem with Linux was when a hard drive was failing. I replaced the drive and the problems went away.

---

### Post by johnnybgoode83 on 2011-07-14
> **ebu said:**
> Hi there,
I'm just trying to figure out if the level of instability i'm experiencing with ubuntu is higher than average. I'd be very thankful if you reply following answers:
 
1) Are you running ubuntu on desktop or notebook?
2) Ubuntu version?
3) How many times per day your system crashes (reboots itself)?
4) How many times per day it becomes so slowly that you decided to reboot it manually?
5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?
6) Did you do something special to make your system more stable?
 
My answers to the questions above are as following:
 
**1) notebook (HP EliteBook 8440p, 8G RAM)**
**2) 11.04, Gnome**
**3) once in a day or two**
**4) once**
**5) 3-5**
**6) no**
 
As you may guess I'm quite frustrated with this situation. When i worked on Windows the figures were at least 10 times lower. So I'm now trying to figure out if it worth to somehow fix it or give up and move back to Windows.
 
Best regards, Eugene.
 
 
I did use 11.04 for a bit as well and found that my answers were similar to yours but then I reinstalled 10.10 and I have very few problems apart from 1 or 2 application freezes but that's it.

---

### Post by coffeecat on 2011-07-14
> **coffeecat said:**
> Because of the different way in which Linux addresses memory it is more likely to uncover a memory fault than Windows, particularly when this is in the upper registers.

> **Ad@m said:**
> In other words Windows is more resilient to faulty memory. That doesn't sound right.

> **Grenage said:**
> Not more resilient, just less likely to encounter them; I've seen it on several machines, as I'm sure many others here have.

> **Ad@m said:**
> Sorry for going off topic.

You are impliedly saying Windows is a more stable platform given you are less likely to encounter the effects of faulty memory.

Hence, Windows is more resilient to faulty memory.

> **Grenage said:**
> Not at all, it's just less likely to use the memory that's defective.  Both Windows and Linux are very stable platforms.

Sorry to all for going slightly off-topic, but this is an important point, and relevant to the OP's situation.

**@Ad@m**, you are misrepresenting what I originally posted and making a mis-assumption. Grenage has already answered you, but let me add my two-penno'th. Windows is not more resilient to faulty memory. It is simply less likely to encounter faulty memory if it is in the upper registers. And/or - Linux is more likely to uncover faulty memory if it is present. That's simply a function of the different ways in which Windows and the Linux kernel allocate chunks of memory to running processes.

---

### Post by Wim Sturkenboom on 2011-07-14
1) Are you running ubuntu on desktop or notebook?
[COLOR="Blue"]noname desktop, fujitsu siemens amilo P1505 laptop[/COLOR]
2) Ubuntu version?
[COLOR="Blue"]10.04 64 bit and 10.04 32 bit respectively[/COLOR]
3) How many times per day your system crashes (reboots itself)?
[COLOR="Blue"]Never; both systems are often on 24 hours a day[/COLOR]
4) How many times per day it becomes so slowly that you decided to reboot it manually?
[COLOR="Blue"]Never[/COLOR]
5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?
[COLOR="Blue"]Never; there is one non-standard application (darktable) installed on the desktop that does not close properly and needs to be killed after closing it. Not installed on the laptop.[/COLOR]
6) Did you do something special to make your system more stable?
[COLOR="Blue"]The desktop needed a 'nomodeset' fix to solve issues with the nVidia 8400 based video card (else it would not completely boot). Further it at occasion does not boot properly, but once booted there are no issues.[/COLOR]

---

### Post by rg4w on 2011-07-14
1) Are you running ubuntu on desktop or notebook?
Both, plus servers

2) Ubuntu version?
Currently 10.04, 10.10, and 11.04

3) How many times per day your system crashes (reboots itself)?
Zero

4) How many times per day it becomes so slowly that you decided to reboot it manually?
Zero

5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?
Zero

6) Did you do something special to make your system more stable?
Installed drivers needed for the components that came with the system.  In fact, I only had to do that on two systems, and in both cases Ubuntu prompted me to get them.


And:

0) Does linux really work?
No.  This web site, Canonical, and all the folks who post here are all conspiring in an elaborate ruse designed to trick people into downloading a 700MB ISO file that doesn't actually do anything.

---

### Post by AlanR8 on 2011-07-14
Saw the first few posts couldn't be bothered with all the middle ones.

Here's the thing. Does the internet work?

What tends to power the Web......?

The answer is NOT windows.

---

### Post by Wim Sturkenboom on 2011-07-14
> **AlanR8 said:**
> 
Here's the thing. Does the internet work?

What tends to power the Web......?

The answer is NOT windows.Electricity :lolflag:

---

### Post by Dangertux on 2011-07-15
Notebook
Lucid
Never
Never
Never
Understand what is happening without mindlessly clicking/typing/installing/sudo'ing to do something.

---

### Post by Brushstroke on 2011-07-15
> **ebu said:**
> Hi there,
I'm just trying to figure out if the level of instability i'm experiencing with ubuntu  is higher than average. I'd be very thankful if you reply following answers:

1) Are you running ubuntu on desktop or notebook?
2) Ubuntu version?
3) How many times per day your system crashes (reboots itself)?
4) How many times per day it becomes so slowly that you decided to reboot it manually?
5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?
6) Did you do something special to make your system more stable?

My answers to the questions above are as following:

1) notebook (HP EliteBook 8440p, 8G RAM)
2) 11.04, Gnome
3) once in a day or two
4) once
5) 3-5
6) no

As you may guess I'm quite frustrated with this situation.  When i worked on Windows the figures were at least 10 times lower. So I'm now trying to figure out if it worth to somehow fix it or give up and move back to Windows.

Best regards, Eugene.
I've been using Ubuntu 10.04 LTS and it's very stable and very fast. Ubuntu 11.04 is quite unstable even after the final release, and I think Canonical made a mistake in releasing the new Unity interface this early. As for your questions: 

1) Toshiba Satellite L455D laptop (500GB HDD, 4GB RAM)
2) 10.04, GNOME 2
3) No crashes so far. Dead serious.
4) It stays pretty consistently fast even with five to six programs (Firefox, Pidgin, Audacious, GIMP, FrostWire, and maybe something else) open at once.
5) Never.
6) Customized the partition scheme to give less swap space than default, and adjusted the "swappiness" to around 30 or so, and I get the latest software updates through PPAs rather than the default repositories.

If you're having problems with 11.04, I highly recommend you downgrade to 10.04. It's a Long-Term Support (LTS) release, which means it's supported until 2013. For over three years (2010 to 2013).

---

### Post by ebu on 2011-07-15
Thank you everybody for your responses!

Today's mem test didn't find any error, so the next step will be downgrading to 10.10. I'm not sure when i will have time for this, but when done i hope i'll be able to post my statistics here with all 'never' against all problems i had :)

Best regards, Eugene.

---

### Post by kaldor on 2011-07-15
> **ebu said:**
> Thank you everybody for your responses!

Today's mem test didn't find any error, so the next step will be downgrading to 10.10. I'm not sure when i will have time for this, but when done i hope i'll be able to post my statistics here with all 'never' against all problems i had :)

Best regards, Eugene.

After reading the first post I was almost instantly going to jump in with "faulty RAM", but I guess that's out of the picture. Make a fresh install of 10.04 (Lucid Lynx) and see how that will go, since it is an LTS release and should be more stable.

And just to answer your original questions:

1) Both

2) 11.04 64-bit on Desktop, 10.10 32 bit on laptop.

3) Never on desktop. Lately on laptop, but I think it's a hardware issue (worked fine for the last 3+ years)

4) Never.

5) Not often. Sometimes a particular program will go rogue, but that's unrelated to Ubuntu. All I need to do is press the close button and it'll force quit.

6) No.

---

### Post by SavageWolf on 2011-07-15
Ebu, why did you install Eclipse yourself? Why not from the software centre?

Anyway, answers!
1. Uh, a laptop and a desktop which has been set up as a minecraft and printing server.
2. Laptop is running 11.04 with Gnome 3, and my server is running 10.4
3. Occasionally when using a 2.6.38 kernel it will fail to boot or restore from a suspend, but 2.6.35 works fine. My server has been up 26 days (and requires a reboot for updates... Tsk...)
4. Occasionally it slows down to a crawl, but I don't reboot it, I go to top and see what is up, or kill the XServer... I have like 50 tabs open so that happens quite a bit...
5. Not as much as I used to actually... Mostly it's because it gets a little laggy and I can't be bothered waiting...
6. I use an older kernel! Yay!

---

### Post by el_koraco on 2011-07-15
> **ebu said:**
> Thank you everybody for your responses!

Today's mem test didn't find any error, so the next step will be downgrading to 10.10. I'm not sure when i will have time for this, but when done i hope i'll be able to post my statistics here with all 'never' against all problems i had :)

Best regards, Eugene.

Also, make sure you do a [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") of the downloaded iso before you install.

---

### Post by NERDMAN! on 2011-07-15
> **ebu said:**
> Hi there,
I'm just trying to figure out if the level of instability i'm experiencing with ubuntu  is higher than average. I'd be very thankful if you reply following answers:

1) Are you running ubuntu on desktop or notebook?
2) Ubuntu version?
3) How many times per day your system crashes (reboots itself)?
4) How many times per day it becomes so slowly that you decided to reboot it manually?
5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?
6) Did you do something special to make your system more stable?

My answers to the questions above are as following:

1) notebook (HP EliteBook 8440p, 8G RAM)
2) 11.04, Gnome
3) once in a day or two
4) once
5) 3-5
6) no

As you may guess I'm quite frustrated with this situation.  When i worked on Windows the figures were at least 10 times lower. So I'm now trying to figure out if it worth to somehow fix it or give up and move back to Windows.

Best regards, Eugene.

ive heard alot of people complaining about 11.04 having issues. try 10.04 lucid lynx. its a long term support distro, so it will recieve updates for the next year or so. ive never had it crash on me and the only thing ive ever had to kill manually was minecraft when java decided to be moody.

i would say your likely just experiencing the issues people were complaining about when 11.04 came out. i know i had a few problems getting applications installed through wine to even start when i tried 11.04.

when it boils down to it the answer to your original question is yes linux is indeed stable assuming that the distro isnt trying out a relatively new and experimental package, (unity in 11.04 as an example)

>  When i worked on Windows the figures were at least 10 times lower.

in response to this i would have to say ubuntu is alot more stable than windows according to my experience, as my windows install frequently experiences issues ranging from application crashes to total lockups on a daily basis, i am sure it is repairable but i cannot find the cause of them. in reality the only reason i keep it is because my TAFE course requires that i use it.

so the gist of it is your problems are likely related to the distro itself. i suggest you check out 10.04 LTS. :D
regards
NERDMAN!

---

### Post by ericrichards420 on 2011-07-15
I have ubuntu 10.10 running on 2 of my desktops, ubuntu 10.04 server eddition powering my web server and ubuntu 11.04 on my laptop. The 10.04 and 10.10 run flawlessly but I have noteced that the 11.04 is a bit buggy. what I think you should do is do is install ubuntu 10.10 and wait until 11.04 is better revised.

---

### Post by ebu on 2011-07-15
> **SavageWolf said:**
> Ebu, why did you install Eclipse yourself? Why not from the software centre?

i need a bunch of eclipses for rcp dev, modelling, jee, 'main' work, 'my' work, each with different set of plugins.

---

### Post by jmlynn on 2011-07-15
Ebu,

Yeah, I had upgraded from 10.04 to 11.04, it is slow, Eclipse crashes multiple time a day.  Right after I upgraded, I had extreme difficulties to configure my external display.  After a few XServer reconfig and reboot, it now sees the external monitor for no apparent reason.  (The same configuration I did for the fist few time had no effect, until the last reconfig).  Weird.

And worst yet, I was unable to configure network printer as the "Add" button in Printing was disabled.  Post question in forums but seems nobody had any clues.  Lucky I had dual boot installed in the notebook, so I can just boot up Windows and print whatever I need, that is a ridiculous by any standard.

So I guess I will downgrade my Ubuntu back to 10.04 LTS when I got some slack time.

Good luck to your problem.

Jeff

---

### Post by KeyserSoze93 on 2011-07-15
My current systems are very stable (desktops and laptop.) I am actually running Debian but ran Ubuntu for several years.

HOWEVER, in response to any perceived instability with Ubuntu, I have had systems which behaved terribly.

I think part of it is that Linux seems more "sensitive" about broken hardware, which is both good and bad - i.e. a system that seems to run Windows fine can crash more on Ubuntu.

It's always turned out to be some piece of hardware which was on the way out, though. GFX card, hard drives, PSU, bad RAM. Windows could perhaps make this hardware seem to be OK by silently ignoring erros, but if it's broken it's broken.

When you get good hardware, however, systems are virtually unbreakable. It's very rare that I've bad any software malfunction that wasn't actually down to a hardware error (e.g. Firefox crashing when I scrolled fast.)

Windows, on the other hand, manages to break itself pretty arbitrarily.

---

### Post by Ghostcore on 2011-07-15
The only issue I have experinced thus Far with 11.04 Desktop was totem and Banshee not playing video files after installing some extra codecs. Which I resolved by simply reinstalling the effected software.

As for crashes slowdowns etc not once has this version done either of those.

As others suggested You might want to look in the direction of your hardware RAM/HDD

Im running a HP Pavilion dv6 Notebook
6gb Ram
500gb sata HDD
intel core2 duo
Intel Video
Compiz and several Effects enabled

All that being said for me this has been the most responsive version to date. (after trashing unity of course)

---

### Post by akand074 on 2011-07-15
1 - Both.
2 - 11.04 currently
3 - never
4 - never
5 - not often
6 - no

Have you tried a new clean install? Do you have your proprietary drivers installed? Is your hardware compatible? You might want to try Ubuntu 10.04 LTS (far more stable). Also Ubuntu isn't Linux... Linux is a kernel, not an OS. There are tonnes of Linux-based OS. Debian is one known for it's stability. There's a distribution for just about everyone's needs. Ubuntu is just a mainstream general user OS. I'm sure there is a reasonable explanation. There always is in Linux-based OS (from my experience), where as other OS' tend to do things and stop doing things and I can never find out why.

---

### Post by HermanAB on 2011-07-15
Linux should never crash.  

# uptime
 03:09:32 up 626 days, 14:15,  2 users,  load average: 4.93, 4.71, 4.28

---

### Post by linuxyogi on 2011-07-15
> 1) Are you running ubuntu on desktop or notebook?
2) Ubuntu version?
3) How many times per day your system crashes (reboots itself)?
4) How many times per day it becomes so slowly that you decided to reboot it manually?
5) How many times per day you have to kill something (office app, eclipse, fireforx etc) because it become frozen?
6) Did you do something special to make your system more stable?1) Two Desktops
2) Natty 32 (LXDE), Natty Minimal Install (openbox)
3)Never
4)Never 
5)Never .....I sometimes do "kill -9" when a Game running under Wine crashes but that's different.
6) Using LXDE coz its lighter & I am loving it.

```

sudo apt-get install lubuntu-desktop
```

---

### Post by fuduntu on 2011-07-15
> **HermanAB said:**
> Linux should never crash.  

# uptime
 03:09:32 up 626 days, 14:15,  2 users,  load average: 4.93, 4.71, 4.28

That probably isn't a desktop, and you should probably patch it.

---

### Post by Wim Sturkenboom on 2011-07-16
> **fuduntu said:**
> That probably isn't a desktop, and you should probably patch it.

:lolflag:

---

### Post by arunssha on 2012-07-06
My answers to the questions above:

1) notebook (Dell Latitude6420, 4G RAM)
2) 11.04, Natty
3) once in a day or two
4) Never
5) 3-5
6) no

I am really frustrated with ubuntu 11.04, suddenly it stops responding and then I have to hard reboot it loosing all the data.
many softwares crashes every now and then. Darktable is the biggest culprit, most defective software I have ever seen. Now situation is it doesn't even work even after i tried complete removal and reinstall.
wireless Internet stops working randlomly once or twice in a month and then even 3hours of R&D on google won't fix it. And worst thing is I can't simulate it and have nothing to show to technical service person.
I have to kill running applications many times as they stop responding quite frequently. I am not linux expert but I am a techie person, so i don't just leave problems until i do a deep R&D on how to fix it.  But I am tired of looking for solutions there are endless problems in it. Ubuntu is most unstable OS I have ever seen at least the 11.04 natty not sure about other versions. I have to live with this hopeless peace of zunk as this is my office notebook. I hope 12.04 gets better.

---

### Post by coffeecat on 2012-07-06
Old thread closed.

@arunssha, if you need help please start a new thread rather than resuscitating an old one.

---

