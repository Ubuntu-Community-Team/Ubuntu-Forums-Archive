---
title: "Thermal shutdown after running 9.10 !!"
date: 2010-03-31
forum: General Help
---

### Post by Ernesto RD on 2010-03-31
A while ago i used ubuntu 9.04 on my PC without any problems (well no hardware problems at least), then due to work issues, i was forced to swich back to windows 7. 
A few days ago i decided i miss ubuntu, and installed 9.10 in dual boot mode (ubuntu and windows 7) with a spare hard drive i have. I finished installing ununtu on the other drive, installed all updates, installed the driver for my radeon video card, and everything seemed to be running smoothly.

After roughly 30 minutes of using ubuntu, i had to swich to windows to run Dreamweaver, so i shut down my computer, turned it on again and booted to windows, and even before i was able to start dreamweaver, the PC shutdown, i turned back on, and i got the warning beeps from the motherboard, i tought it was just a coincidence (nothing to do with ubuntu), and that maybe the silicon heat transmiting grease between the CPU and heatsink was dry or something, so i took the cover off, and when i touched the cpu heatsink it burned my fingers!
In later inspection i discovered that there was nothing wrong with the heatsink or naything else. I got spooked, removed the new disk (the one with ubuntu), and after 2 days of intensive use the PC seems to be working fine with windows 7 (no overheat).

mhh, out of curiosity i installed the ubnuntu hard drive again, booted to it, used it for about 1 hour and AGAIN, the PC shutdown due to overheating.

I love ubuntu, but now im affraid it will PHYSICALLY damage my computer! this PC has been used with windows XP, Windows 7, ubuntu 9.04 and ibe NEVER had any problems with it!
And whats more, i have a Dell inspiron mini 10v coming, and i planned on installing ubuntu 9.10 netbook remix on it, but now im affraid it will damage it.

Again and just to make this perfectly clear, There is nothing wrong with my PC, it works perfectly with windows 7, i can have dreamweaver, visual studio, firefox and several other apps running at the same time, and it does NOT overheat. It only happens when i run ubuntu.

Is there a chance theres something wrong with the kernel, a driver or something (in ubuntu) thats causing this?
Should i be worried?
Can i install ubuntu on my new netbook with out worriyng it might be damaged?

Im pretty worried about this. :(

For reference, myPCs specs are...

Intel Pentium D dual core 2.8Ghz CPU
Intel motherboard
Sapphire ATI HDG4670 PCI-E graphics card
3Gb DDR 2 Kingston RAM in dual channel config.
320Gb Seagate SATA drive
500W power supply

thanks in advance for your help and opinions

---

### Post by TBABill on 2010-03-31
I experienced heat issues as well with Karmic. I had a laptop pad to absorb some of that heat but I would find my machine would do the same things. It would run hot and the fan ran on high very often, especially with videos online (known issue with Adobe Flash using tons of CPU). And if I would reboot with it warm like that it would often get to the Acer/Bios screen, then shut back off. After letting it sit it would come back on, but it would run hot often.

Can you try another distro, possibly one not based on Ubuntu? That would tell you at least if it's Linux specific or Ubuntu specific. PCLinuxOS is really nice in beta right now and installs simply, plus it uses Apt and Synaptic so it'll feel somewhat the same as Kubuntu. There are lots of others (Mandriva, Fedora, SUSE) that you could try as well that are not Ubuntu based to find out of it is the distro or something with a Linux configuration and your machine.

Just ideas off the top of my head. Surely there are those with experience correcting the actual heat/fan issue that may be much simpler than my suggestion. Just a shot in the dark.

---

### Post by TBABill on 2010-03-31
I experienced heat issues as well with Karmic. I had a laptop pad to absorb some of that heat but I would find my machine would do the same things. It would run hot and the fan ran on high very often, especially with videos online (known issue with Adobe Flash using tons of CPU). And if I would reboot with it warm like that it would often get to the Acer/Bios screen, then shut back off. After letting it sit it would come back on, but it would run hot often.

Can you try another distro, possibly one not based on Ubuntu? That would tell you at least if it's Linux specific or Ubuntu specific. PCLinuxOS is really nice in beta right now and installs simply, plus it uses Apt and Synaptic so it'll feel somewhat the same as Kubuntu. There are lots of others (Mandriva, Fedora, SUSE) that you could try as well that are not Ubuntu based to find out of it is the distro or something with a Linux configuration and your machine.

Just ideas off the top of my head. Surely there are those with experience correcting the actual heat/fan issue that may be much simpler than my suggestion. Just a shot in the dark.

---

### Post by Ernesto RD on 2010-03-31
Thanks for your reply & sugestions :)
You know, before trying ubuntu a while ago, i tried a lot of other distros, fedora, suse, even debian. And to tell you the truth, i dont like any of them. I find them too complicated to use, too much time spent in configuring the thing to run (instead of actually getting my work done), a lot less user friendly, etc. 
I guess it boils down to this: if i cant use ubuntu, ill stick to windows.

---

### Post by Ernesto RD on 2010-03-31
TBABiII: I forgot to ask, did you try other versions of ubuntu (such as 9.04) on that computer? if so, did you have those problems with the other versions as well?

I remember running 9.04 some time ago on this same computer without any problems. Maybe this issue is specific to 9.10 only?

---

### Post by TBABill on 2010-03-31
No 9.10 was the first Ubuntu I tried. If you like easy to setup give PCLinuxOS beta a try. It's fast and simple. My fan runs on varying speeds during use, but never full blast for very long like in Ubuntu. I'm like you though. I just like Ubuntu and the community.

---

### Post by bigsmitty64 on 2010-03-31
Off the wall thought here, do you have another hard drive hanging around you could try?

---

### Post by ram2500 on 2010-03-31
I would try using the CPU scaling monitor as a temporary fix.  (read below for more information.) Throttling back your processor should keep the heat down, and is okay if you aren't doing heavy tasks. However, my nephew is 12-years old and loves Flash games.:p so this will sacrifice performance.

I posted a while ago about an inquiry about potential ATI driver issues in Ubuntu as I was purchasing a pair of off-lease HP dx5150 PCs (circa 2005-06) for my nephews. Anyways, one of the machines works fine, but the other has occasionally overheated. I have exhausted all the possibilities: thermal paste, clean out dust (these were in a corporate environment, there was NO dust--it was just like new!), check processor speed, check the fan, etc. 

Needless to say: there was thermal paste, there was NO dust, the fan worked and the processor was clocked at 2.2 GHz, its normal "designed" speed. The processor was seated properly and the heatsink was secured in the socket. However, it does overheat and shut off often and its fans run _really loud_ when operating at its maximum speed (2.2 GHz)...does anyone own a HP dx5150 that can give any ideas? I have my nephew using the CPU scaling monitor applet to run at its lowest (1 GHz) and this seems to work, but like most 12-year-olds, he wants to play Flash games.

edit: I forgot to mention that it is very well possible that your system may not throttle, or Linux doesn't know how to throttle that particular system. CPU throttling works in Linux if the CPU is able to do so, it just has to have the cooperation of having drivers to interface correctly with the system (regarding the BIOS and fan/CPU throttling, not the CPU). Additionally, since it's probably an obscure driver inhibiting the proper operation of the system under Ubuntu, I would try an earlier version on a flash drive or CD (or maybe even the beta that's available, Ubuntu 10.04), and see if anything changes.

---

### Post by TBABill on 2010-04-01
I would still suggest trying a different distro to see if the problem persists across Linux distros or if it is Ubuntu related. It doesn't take too long if you have broadband and a CD burner to download and try another distro on a separate partition. Few hours of work maybe to get up and running to where you can use the Internet with Flash. Mint and PCLinuxOS I am certain come with flash already installed and configured. There are surely many others, but these I can attest to, so even if unfamiliar with them you may have an easier time than trying to learn a not-so-easy new OS.

---

### Post by azagaros on 2010-04-01
I had noticed this laptop I put ubuntu 9.10 it ran harder than it did under vista.  This laptop was a Celeron 1.8 with 512mb.

Kbuntu didn't seem to run as hard but I didn't leave on the box long enough, didn't like KDE 4.0, loved KDE 3.x.

I haven't figured out what makes it run so hard for a web browser and max out the swap.  I never had a 486 run this hard running a linux, with xwindows, and kde/Gnome.

---

### Post by TBABill on 2010-04-01
I wish I knew that answer. I had moved to Mint 8 because it ran faster on flash apps than Ubuntu and was smoother with videos, games, etc. But that was after the most current flash version was put into the repos. Before that they were both pretty bad with flash. Now I can't see why Ubuntu would lag behind Mint in flash performance, but it's significant. Being based on ubuntu it seems unreasonable that they'd perform differently, so it must be configuration in Mint that is slightly better in one aspect than Ubuntu? Just a guess. I love Ubuntu, but till it's faster in Flash I tend to stick to other distros and test Lucid regularly to see if speed improves.

---

### Post by Ernesto RD on 2010-04-02
I found my old ubuntu 9.04 CD, and i booted my PC with it (with the "try ubuntu without altering your system" option). Used it for a couple of hours, reeboted to W7, then used ubuntu again for about an hour (mostly internet surfing in firefox), then i left the computer on all night with ubuntu.
**No overheat whatsoever!** in fact, i could hear the CPU fan was running at low speed. :)

And more news! i am EXTREMELY happy cause i just got my Dell Inspiron mini 10v Netbook, :)
I removed the windows xp home edition (AKA CHEAP edition), and installed Windows 7 Professional, AND Ubuntu network remix 9.**04** (i dint have the courage to risk trashing my new netbook with 9.10), and right after installing ubuntu, everything worked perfectly :) No overheat there either.
The only issue im having with the netboock is that the mousepad doesnt seem to work well, its kinda "jumpy", dragging a window for example is nearly impossible. (anyone seen this problem and hopefully have a fix for it?)

NE way, i think i can say with some confindence, that the overheat problem occurs because theres something wrong with ubuntu **9.10** as running 9.04 dint give me any problems at all. No need to try other distros.

I only hope that the new LTS version of ubuntu is not as buggy as 9.10, cause to be  honest, seeing the list of reported problems with 9.10 on this forum, it seems to me that 9.10 is to ubuntu what vista was to microsoft :)

P.D. Anyone have any idea of what could be wrong with the touchpad on my netbook? something wrong with the driver on ubuntu 9.04? (needless to say the mousepad works perfectly on W7).

---

### Post by chaosz911 on 2010-05-17
Hello,

Unfortunately I have the same issue. The laptop overheats with quite simple daily tasks and with heavier stuff it will go into thermal shutdown.
I thought it was fixed with $ sudo sensors-detect and adding the 'coretemp' module to /etc/modules, but alas. It only delays the thermal shutdown :(
Like you it did not happen with 9.04 on the same laptop (MSI VX600). Unfortunately I would really like 10.04 for it's iPhone/iPod support.
When you Google for this problem there are quite a lot of threads about this issue, which makes me wonder why it hasn't been fixed with the official release of 10.04 ?!
Oh well, today there is a new kernel available, perhaps that will work :/

---

### Post by digitography on 2010-09-22
If this is a small form factor PC then adding the second drive may be pushing the internal cooling facilities to the limit. Even though you are only using one HD at a time, they are both running, and therefore both generating heat.

I have experienced some HDs that will work fine but run hot enough to burn your fingers if you touch them too soon after shutdown.

my suggestion is put the Ubuntu drive in on it's own, leave the win 7 disk out (if your boot loader is on the win7 drive then you may have to reinstall Ubuntu). Then run Ubuntu to see if you get the same results

---

