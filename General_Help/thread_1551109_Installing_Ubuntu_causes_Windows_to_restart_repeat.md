---
title: "Installing Ubuntu causes Windows to restart repeatedly during startup"
date: 2010-08-11
forum: General Help
---

### Post by CrossbowFFS on 2010-08-11
Hi guys, I recently installed Ubuntu (the full version). I liked Wubi a lot, but that's because I just had to press down and enter during startup. After uninstalling it, I went to the full version, but that's been giving me more trouble than Wubi, lol. 

First, it replaced my Windows Boot Manager with GRUB (which IMO sucks because it takes like 15 seconds to load the menu and it lags when you want to press an arrow key). Second, it screwed up my Windows (the first time I started up Windows I got like 50 lines of errors and after that I had to do the disk check thing but now it works). I use Vista x32, and when I try to boot into Windows it gets to the (C)Microsoft with the green loading bars thing and after about 5-10 seconds my computer randomly (without warning, the screen just turns black) restarts. Goes back to the BIOS menu, a full restart.

Can anyone help me? My first priority is to get Windows fully running without restarts during boot time. Then I'd like to use Windows boot manager to start Ubuntu (I checked with EasyBCD, Ubuntu doesn't show in WBM.

If you can help, thanks in advance!:)

Oh BTW, dual-booting ubuntu 10.04 and WinVista SP2.

---

### Post by Unknown-Demon on 2010-08-11
Are you able to uninstall/reinstall wubi?

---

### Post by CrossbowFFS on 2010-08-11
Yeah, I can still boot up into Windows, it just takes multiple restarts (and maybe a boot into Ubuntu) to get to the Windows Logon screen.

edit: BTW, I use Ubuntu as a way to backup my files in case Windows ever screws up and I can't boot into it. I don't see the point of it screwing up my PC if it's supposed to be an emergency OS... lol. And the point of the full install is so that if my WinVista partition screws up I can use Ubuntu, if I use Wubi that wouldn't work.

---

### Post by bcbc on 2010-08-11
Did you use the ubuntu installer to shrink your windows partition, or did you use the disk management tool in Vista?

PS post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")

---

### Post by lisati on 2010-08-11
A minor digression here:

Like BCBC mentioned, using the disk management tools provided by Vista (in preference to the partitioner used by the Ubuntu installer) is often a good idea. I ran into a different but equally annoying problem one time with Vista when I was moving from Wubi to a regular installation, and used the partitioner in Ubuntu's installer for resizing.

Your question reminds me of one time where I'd installed XP's SP3, and then tried installing Ubuntu before restarting XP - things went horribly wrong rather quickly, with XP wanting to restart all the time before getting anywhere near its desktop being displayed. Part of the problem was that the particular machine I was doing this on needed a patch to be applied BEFORE installing SP3. 

Good luck.

---

