---
title: "(Dapper) pppoeconf not working"
date: 2006-03-17
forum: General Help
---

### Post by robbbert on 2006-03-17
Hi,

I've just setup Dapper Flight 5, and would like to access the internet using DSL.

In pppoeconf's second dialog window ("Searching for an access concentrator on eth0"), the progress bar reaches 100%, then, for a very short time, an unreadable message appears before the system completely freezes.

When I choose "No" in the first dialog window ("Are all our ethernet interfaces listed above? (If No, modconf will be started..."), an error message appears, telling "modconf" was not installed ("modprobe modconf" returns negative, too), and the system also freezes.

There are two network cards in my PC. On installation, I was asked which one of them to choose as "default" one. Well, I installed Dapper two times, choosing the other network card respectively, to make sure I didn't choose the wrong one.
Using Windows, at least one of those network cards did work recently.

On my other computer - with Breezy - pppoeconf does work.

Could someone point me to how to make accessing the internet work? Thanks sincerely.

[Edit]Additionally, the system freezes when I close gnome-terminal, in which pppoeconf was running.[/Edit]

---

### Post by Dominus Suus on 2006-03-17
That sounds really odd.  pppoeconf works perfectly on my machine (Dapper flight 5) and the garbage output you're getting suggests to me that something's wrong with the files itself.

I haven't tried it, but you may think about [# sudo apt-get remove pppoeconf], change your repositories install Breezy's pppoeconf if the other packages will allow it.

---

### Post by robbbert on 2006-03-17
Thanks. I've uninstalled pppoeconf and installed it from the 5.10 CD. The system's still freezing.

[Edit]In the meantime, I copied /etc/ppp/peers/dsl-provider to my new computer (currently, I've not set a password but there should be a prompt or an error when I try to connect, right?)

    #pon dsl-provider

produces strange output at the command line, characters like "}&} }?>...", coming in chunks.
/var/log/messages says, "Connect: ppp0 <--> /dev/pts/1" but not much more until I abort.

In Ubuntu's Networking dialog, eth0 is marked as "active" and appears to be OK.[/Edit]

---

### Post by robbbert on 2006-03-18
This is solved.

The system froze when inspecting eth1. This strange ethernet card also had an odd plug socket, I didn't know what for it's used. After I removed the card, pppoeconf (and other tools I made up in the meantime) worked, but still did not find an "access concentrator" on eth0.

When I booted Windows, the network card was "disabled". I enabled it and booted Linux - and finally it's working!

---

### Post by robbbert on 2006-03-18
Me again...

I'd rebooted and pppoe didn't work (didn't find an "access concentrator"). Next, I booted into Windows, but the ethernet card wasn't disabled this time. Then, I booted into Ubuntu again, and eth0 was inactive. I activated it but pppoe wouldn't find it ("access concentrator"). Before all that I'd installed kubuntu-desktop (amongst other applications). So I removed kubuntu-desktop and suddenly pppoe would work again...

Hm hm hm...

---

### Post by robbbert on 2006-03-27
Although nobody seems to be interested in this thread, I'd like to close it. - For the record:

At boot time, recognizing the network card always failed. At runtime, I'd been able to "activate" it by using the GNOME "Networking" dialog. In most cases, after booting, I had to repeat that step multiple time before pppoeconf would work.

The issue got solved when I updated the Linux kernel (from 2.6.18 to 2.6.19). Now the network card gets recognized and pppoeconf even establishes the DSL connection automatically at boot time - great!

- After all, I'd been warned about using an alpha version of Dapper, and won't complain. Seriously: Thanks for giving me one of the best pieces of software I ever had.

---

