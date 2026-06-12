---
title: "Multiple Problems"
date: 2010-07-07
forum: General Help
---

### Post by rccgop on 2010-07-07
Hi all,

I wanted some input on chronic problems with Ubuntu:
1. Why does wireless almost never work right on Ubuntu?
2. Why, when Ubuntu just decides to turn off my wireless card, can I not just turn it back on?
3. Why do tar balls almost never unpack right?
4. Why are printer drivers so buggy?
5. Why do my MP3 players and digital cameras not work with Ubuntu?

I spent 3 hours last night trying to unpack a tar.bz2 file so I can run my Ralink network card. It worked fine until my son unplugged my computer. Now my card is disconnected and it will not reconnect. When I check forums no one has a simple answer for something as simple as turning a network card back on.  On my Apple, it's simple: click my wireless icon and hit "on."

I've tried to bear with things like this for three years now, but I'm about to get in my car and by a Windows computer so I can get rid of these headaches. The network thing might be the last straw for me.

If someone could tell me an easy way to just turn my wireless card back on, it would renew my faith a little in Linux.

Thanks!

---

### Post by cariboo on 2010-07-07
> **rccgop said:**
> Hi all,

I wanted some input on chronic problems with Ubuntu:
> 1. Why does wireless almost never work right on Ubuntu?

It would help if you told us the  make, model and chipset of your device. I have several wirless devices, all but one which is windows only, work out of the box. The windows only device works on the 32-bit version using ndiswrapper.

> 2. Why, when Ubuntu just decides to turn off my wireless card, can I not just turn it back on?

Have  you tried right-clicking on the network icon in the top panel and dis-abling, then enabling wireless?

> 3. Why do tar balls almost never unpack right?

How do you unpack tar files, I just double click them, and let file-roller do the work.

> 4. Why are printer drivers so buggy?

Again without knowing what make/model printer you have, its pretty hard to help. I have a Brother networked laser printer and Epson R340, currently that work flawlessly. I have also used HP previously with zero problems. The Brother automagically installs the drivers from the manufacturer

> 5. Why do my MP3 players and digital cameras not work with Ubuntu?

I have an mp3 player that has to be set to MPT mode in order for the system to see it. I have Sony, HP and Kodak cameras that just work when connected. The only camera I've had a problem with was a brand new Nikon, we didn't have the correct cable for it, as the owner left it at home in Europe. 

> I spent 3 hours last night trying to unpack a tar.bz2 file so I can run my Ralink network card. It worked fine until my son unplugged my computer. Now my card is disconnected and it will not reconnect. When I check forums no one has a simple answer for something as simple as turning a network card back on.  On my Apple, it's simple: click my wireless icon and hit "on."

Again, how are trying to decompress your tar file?

> I've tried to bear with things like this for three years now, but I'm about to get in my car and by a Windows computer so I can get rid of these headaches. The network thing might be the last straw for me.

Instead of purchasing a new computer, why not just buy a supported wireless device

> If someone could tell me an easy way to just turn my wireless card back on, it would renew my faith a little in Linux.

Thanks!

---

### Post by Abu Azzubair on 2010-07-07
> 1. Why does wireless almost never work right on Ubuntu?

I'm only a beginner like you so please don't get angry at me Lol

When my Laptop had Linux Ubuntu 10.04 LTS installed on it, it also had problems with the type of built-in wireless card that was on my laptop

I forgot what the technician exactly said, but from what I understood was that not all wireless cards accept to work on Linux (in general), and NOT Linux not being able, or not accepting to work on them all

As we all know, Microsoft and other companies have certain secret formats to their products and softwares that no one knows of...simply because they are a top-secret kinda thing

But the technician that installed Linux Ubuntu simply went through Terminal, and found an update and in a couple of seconds my wireless was picking up signals - the Internet updated everything and was working fine...etc

No need to worry. I also thought that I had to wait for days for a reply and that everyone here was a geek and that they spoke in a complicated manner Lol. But obviously all that wasn't true at all, and everyone made it so simple for my slow brain, to the point that I also started helping (even though I'm a complete beginner) after doing some research O:)

---

### Post by TBABill on 2010-07-07
Abu, great job getting things back up and running. For the future, something that often helps when you install a version of Ubuntu is to plug into your router after first boot. Doing so will allow the system to go online and check for updates, download them and install them. If your wireless is recognized without plugging in, no need to do so. But if it is not detected, or if it requires a proprietary driver like mine that cannot be installed automatically from the LiveCD, plugging in will allow the system to probe for proprietary hardware and prompt you to install the drivers for that hardware.
 
Not a big deal, but that is something that will help you if you choose to install other distros and come back to Ubuntu, or if you install it on another machine whose wireless is not picked up immediately. You'll often find after that first update that you have a proprietary video or wireless driver ready to install (by clicking on the icon on the panel or by going through system/hardware).
 
Drivers are definitely an issue for peripherals. I got rid of a Kodak printer because they are simply not supported by Kodak with drivers for Linux. I got an HP and it works like a champ. Sometimes you need to swap hardware if you want good support in Linux distros as it is continuing to evolve and increase support for various hardware. Our continued use increases the community of Linux users and that increase may someday prompt many more manufacturers to better support the Linux kernels.
 
Good luck and enjoy your time with Linux. It's great once you learn from your frustrations.

---

### Post by rccgop on 2010-07-07
Thanks for your replies.  Here are some answers to your questions.

I bought what multiple compatibility sites said was a supported wireless card, and it was, but not by the most recent driver. It's a Ralink 2760 chipset supported on Synaptic by a wireless g driver.  To get the most recent n rated driver (2760) I had to download a tar.bz2 file. Package manager extracts it but will not unpack, configure, make and install. I went to Synaptic and downloaded file roller and it appeared nowhere. So I did it command line and it finally installed and was working at g speeds.  However, my son accidentally turned off my computer and when I powered back up the wireless card was disabled.  I had no idea that turning it back on required an IT degree.  I spent the whole morning scouring forums and documentation and can find no solution to turning it back on.  I have a wireless manager that had been connecting fine.  I tried all the diagnostics.  The driver is there, the computer knows the card is there.  It just won't let me turn it on.  I even tried a hard pull and reinstall and nothing.

As for printers, I'm using one I already had. It works okay but periodically decides not to print and will not restart if there is any kind of hiccup like running out of paper. I could buy a new printer that's better supported but part of my reasoning in coming to Ubuntu was the cost savings for the OS and other software.  I'm willing to stick with Ubuntu but it has been a little rocky.  Again, main problems: wireless, printers, mp3 players, digital cameras, online parental controls (Dan's Guardian not effective), and video on demand (all but amazon).  The main problem I want to fix, however, is turning the card back on.

Thanks again for your input.

---

