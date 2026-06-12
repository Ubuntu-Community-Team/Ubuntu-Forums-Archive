---
title: "C:// to Wine"
date: 2011-01-13
forum: General Help
---

### Post by Nictra Savios on 2011-01-13
This is probably the stupidist question ever.... BUT. What would happen if i took my C from my windows partion and put it where the current wine c drive is?... Would that allow me to run anything windows since i have ALL the windows components? Or is there somethings i should transfer so that i can fully integrate my old into my new?

---

### Post by davidmohammed on 2011-01-13
no is the simplest answer.

You should just get the installation media - consult winehq.org for your application and any fixes/workarounds you need and then install using something like

wine setup.exe

or whatever your setup program you need.

n.b. remember there are often better native linux applications - so try to find and use those before you try to install windows programs into wine.

---

### Post by sharathcshekhar on 2011-01-13
@ Nictra Savios
Any full executable windows binary should work with wine. You have to just give "wine /mount/path/of/window-C/drive/something.exe"
But for this the application has to be a independent executable. But dont expect all the applications to run like this. They might need some libraries which wine does not know about. As the previous post suggests, you will have to run the setup.exe  through wine.

---

### Post by kn0w-b1nary on 2011-01-13
While i have not actually tried it, i am saying what i am based off of my current knowledge of windows and wine.

First, not everything that works on windows works with wine.
Second, copying your entire C drive is unnecessary as wine is only for programs, and C drive also contains non-program data, which can be read from within Ubuntu.
Third, I would recommend just installing the programs you want with wine instead of just copying. just open the windows partition in Ubuntu and copy over the installer.

Good Luck!

---

### Post by Cheesehead on 2011-01-13
Do NOT map your Wine c:\ drive to your actual Windows partition!
NOT! NOT! NOT!

Wine will happily corrupt your Windows registry, severely damaging your Windows install.

---

### Post by Nictra Savios on 2011-01-13
> **davidmohammed said:**
> no is the simplest answer.

You should just get the installation media - consult winehq.org for your application and any fixes/workarounds you need and then install using something like

wine setup.exe

or whatever your setup program you need.

n.b. remember there are often better native linux applications - so try to find and use those before you try to install windows programs into wine.

Sadly.... there isnt. Photoshop CS5, dreamweiver CS5 and itunes 10.1 .... Im a jailbreak Dev. I make themes and tweaks for the jailbroken iphones. Those 3 tools are all i have ever known and i really could never learn anything else... its not ignorance its habit and practice. Nothing could ever compare to them for me :( I cannot get the master collection or iTunes to work in any way... *sigh* Looks like i cant get rid of windows 100% for now :(

i NEED i tunes, there is NO workaround for the restore process (yet, a few rumors as of late ... doubt they will be linux thought) and when you restore daily.... yea...

---

### Post by 3Miro on 2011-01-13
Some windows program do work if you just copy paste the folder where they were installed, however, other will not and it is possible to damage your windows partition.

For iTunes, you should consider VirtualBox. If this is the only reason for you to use Windows, VB is probably the best solution.

---

### Post by davidmohammed on 2011-01-13
in that case - stick to a dual boot setup... :-)

---

### Post by Nictra Savios on 2011-01-13
> **3Miro said:**
> Some windows program do work if you just copy paste the folder where they were installed, however, other will not and it is possible to damage your windows partition.

For iTunes, you should consider VirtualBox. If this is the only reason for you to use Windows, VB is probably the best solution.

And photoshop CS5 (ONLY CS5 WILL DO) and Dreamweiver? (which need the various other programs installed with them such as adobe bridge and etc....

And i alredy tried copying all the program files. I need a microsoft visual c++ library.

---

### Post by davidmohammed on 2011-01-13
> **Nictra Savios said:**
> And photoshop CS5 (ONLY CS5 WILL DO) and Dreamweiver? (which need the various other programs installed with them such as adobe bridge and etc....

And i alredy tried copying all the program files. I need a microsoft visual c++ library.

I think you misunderstood - virtual box is a virtualisation software - you install windows inside virtual box.  You then install your windows apps into the window operating system.

virtual box is quite a neat way to see both windows apps and linux apps side-by-side (sort of) - it has a "seamless" mode that almost but not quite makes the windows app appear to be running within ubuntu.

---

### Post by Nictra Savios on 2011-01-13
> **davidmohammed said:**
> I think you misunderstood - virtual box is a virtualisation software - you install windows inside virtual box.  You then install your windows apps into the window operating system.

virtual box is quite a neat way to see both windows apps and linux apps side-by-side (sort of) - it has a "seamless" mode that almost but not quite makes the windows app appear to be running within ubuntu.


Hmm, so your saying the programs i need would run flawlessly within this program? I cannot tolerate bugs. If a bug makes photoshop close thats x amount of hours down the drain... Many times i cannot simply remake something. Could you provide me with links to anything i may need?

---

### Post by matt_symes on 2011-01-13
Hi

My advice... Stick with windows. ;)

If you want to play with Ubuntu create a persistent USB, use wubi or install Ubuntu in a VM under windows. These are the least dangerous methods. Partitioning can sometimes cause problems. 

Just my advice though :D 

Kind regards

---

### Post by Nictra Savios on 2011-01-13
> **matt_symes said:**
> Hi

My advice... Stick with windows. ;)

If you want to play with Ubuntu create a persistent USB, use wubi or install Ubuntu in a VM under windows. These are the least dangerous methods. Partitioning can sometimes cause problems. 

Just my advice though :D 

Kind regards


I am alredy partioned, that was nothing for me. Ive been dealing with computer systems for well over 10 years now, partions are childs play. I understand the iOS better then a chemist understands hydrogen. I've just been stuck out of my element. I had a Motherboard and harddrive burn out and had to buy a labtop ASAP. I'm now stuck with vista, so i switched to Ubuntu. Since the Linux Framework is somewhat similar to the Linux Em i deal with on jail broken ipods. Im already quite experienced with the terminal.

---

### Post by 3Miro on 2011-01-13
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

VirtualBox works great with anything non 3D and non 2D hardware accelerated stuff. It is a bit slower and maybe considerably slower for Photoshop, I don't know. However, you will not get any more bugs than you would under Windows.

However, in your case, dual-boot may be a better option (plus yelling at Adobe to release a Linux version of their software). At least in the beginning, dual-boot should be preferable.

---

### Post by Nictra Savios on 2011-01-13
> **3Miro said:**
> [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

VirtualBox works great with anything non 3D and non 2D hardware accelerated stuff. It is a bit slower and maybe considerably slower for Photoshop, I don't know. However, you will not get any more bugs than you would under Windows.

However, in your case, dual-boot may be a better option (plus yelling at Adobe to release a Linux version of their software). At least in the beginning, dual-boot should be preferable.

A dual boot is what  have now... Should i consider formating my windows partion, reinstalling just those 3 programs and vista.... that way my partion is as small as possible?

---

### Post by davidmohammed on 2011-01-13
only you can answer that - what disk space do you require for ubuntu for now and the future compared to what you need with windows?

---

