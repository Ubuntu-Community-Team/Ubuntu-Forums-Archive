---
title: "GUI failing to start"
date: 2010-12-05
forum: General Help
---

### Post by Beastlicker on 2010-12-05
Hey all. I had an Ubuntu 10.10 installation that ran fine for around a month or so. I decided to go out and try to install aptosid (formerly known as sidux) as a dual boot. I couldn't get the desktop to boot in the LiveCD and kept getting an error saying that the nouveau module could not be loaded.

I rebooted and at the main LiveCD screen, I added xmodule=vesa xres=1440X900

I was able to get a 1024x768 resolution. I decided that I really didn't like aptosid, so I shut it down and took out the LiveCD. When I booted back into Ubuntu, my resolution changed down to 640x480 for some reason.

I decided to remove the proprietary nVidia driver I had installed via jockey. Once it was removed, I restarted. Now, I see no startup splash or a login screen - my monitor just goes to sleep.

I have all my files backed up already, so I decided to pop in my Kubuntu 10.10 LiveCD to install that. Once I choose the "Start Kubuntu" option, my monitor goes to sleep.

I tried putting in Linux Mint Debian Edition LiveCD to see if that would work, and I had the same issue. 

After this, I went for the nuclear option and installed Windows 7 to see if it would wipe out any memory of my Linux drivers from the system. The Windows drivers for my card worked fine, so I decided to put the Kubuntu LiveCD back in and got the same problem.

Does anyone know what my problem could be? I am currently running a Partition Magic LiveCD, but could only boot into it using the Xvesa option instead of Xorg.

My video card is an nVidia 9800 GT - and it has always worked in the past.

---

