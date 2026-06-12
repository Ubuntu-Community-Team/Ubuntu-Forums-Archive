---
title: "Have to put Ubuntu aside for the time being"
date: 2006-06-23
forum: General Help
---

### Post by Fred Doolie on 2006-06-23
Well, it happened in Dapper just like it did in Breezy. One day I boot up Ubuntu and no access to the repositories. Very bad net too. Same old system I had a few hours ago but now 80% of net access is gone. Try the same urls in Wnblows. Perfect and fast. In Ubuntu very very slow or no access. 

Reformat/reinstall. No good. Can't find the repositories during the install. Can't reload them in Synaptic. Try to install stuff though Automatix. hardly anything will dowload. 

Try some urls after doing the ipv and pipeline thing..

[www.google.com](www.google.com) - Windows yes. Ubuntu slooooow.
[www.yahoo.com](www.yahoo.com) - Wndows yes. Ubuntu no.
[www.ubuntuforums,org](www.ubuntuforums,org) - Wndows yes. Ubuntu sometimes.
[www.modthesims2.com](www.modthesims2.com) Wndows fast. Ubuntu no.

So I reformatted the 2nd HDD and went back to a Winblows system.
I LIKED Ubuntu! VERY MUCH! But if it's going to do that I can't trust it.
Brezzy did this too. I reinstalled it every few weeks just to see. No good. Then once day it DID work again. Dapper worked fine  too until now.

I'm NOT saying it's Dapper's fault. How could I? Dapper worked fine for quite a while. Breezy worked fine for quite a while. Then one day (and lasting for many weeks) almost no net access. 

Maybe it's my ISP. Maybe some weird thing in my router locks up. 

So, I'll try installing again in a few weeks and see if it works. 

Will keep checking the forum to see if anybody has any good ideas. I can always install Ubuntu in a VMWare machine to see if it works yet and try different things.

---

### Post by Kurt` on 2006-06-23
Did you do any tests to isolate the problem?

Does "sudo ifconfig" from a terminal show your eth0 as having a valid IP address? (if it doesn't, it could be network/hardware failure)

Does "ping -c 1 google.com" give you a "unknown host" error? (indicating DNS failure)

It could be many things, but things don't just stop working for no reason. :)

From your descriptions, it seems to be a DNS problem somewhere on your local network

---

### Post by nix4me on 2006-06-23
Sounds like a network card/driver issue.

nix4me

---

### Post by _simon_ on 2006-06-24
I'd tend to agree with Kurt and say DNS issue.

If you haven't already, then in your router, change DNS from automatic and enter them in manually.

---

### Post by lamego on 2006-06-24
Just some general guide lines about troubleshooting Ubuntu
 1 - If you have a problem after a fresh install, reinstalling is wasting time
 2 - You should report problems before removing the system so that you can help the people that is helping you.

---

### Post by Fred Doolie on 2006-06-25
[QUOTE=lamego]1 - If you have a problem after a fresh install, reinstalling is wasting time[/QUOTE]

That's what worked last time though. During one of my bi-weekly "Well, maybe THIS time it will work" reinstalls ....it did work again". It took weeks and many reinstalls but it started working again. 

Maybe my ISP changes something once in a great whle*. Something that Winblows checks every time and uses automatically but is hard-coded into Ubuntu?

*Something that get changed after/during lightning storms. That's when Ubuntu (but not Windows) loses the repositories and reliable net access for weeks.

---

### Post by ihavenoname on 2006-06-25
What type of network  card do you have? Could you give us some more information on your hardware, network setup, and ISP?

---

### Post by joshrobinson on 2006-06-25
[QUOTE=ihavenoname]What type of network  card do you have? Could you give us some more information on your hardware, network setup, and ISP?[/QUOTE]

the ethernet port in my laptop dies out all the time, and i have to redo the dhcp of it.. so it could be a driver issue as some are saying.. my wireless works on it fine though, so its only the first 20mins of a reinstall that i have to deal with it before i get my wireless up and running

---

### Post by Fred Doolie on 2006-06-30
A possible "DUH!". After many days of thinking I remembered something about Ubuntu not being able to handle IPV6.  Reinstalled, commented out the ipv6 line in  /etc/modprobe.d/aliases and maybe all's well. Seems good so far, The repositories go ZOOM now when I reload them and they all load. They never zoomed before! 

We'll see. Thanks for the ideas though. It's only been a half hour so far. Let's see if it still works two weeks from now.

Edit
Another clue. Following the instructions for Automatix I edited  /etc/apt/sources.list by adding "deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main" and then "sudo apt-get update". Repositories won't respond. Synaptic Package Manager which worked fine two minutes ago won't update most of the repositories either. Running Automatix generates 404 errors all over the place. Remove that line and all's well again.

---

### Post by ihavenoname on 2006-07-03
[QUOTE=Fred Doolie]A possible "DUH!". After many days of thinking I remembered something about Ubuntu not being able to handle IPV6.  Reinstalled, commented out the ipv6 line in  /etc/modprobe.d/aliases and maybe all's well. Seems good so far, The repositories go ZOOM now when I reload them and they all load. They never zoomed before! 

We'll see. Thanks for the ideas though. It's only been a half hour so far. Let's see if it still works two weeks from now.

Edit
Another clue. Following the instructions for Automatix I edited  /etc/apt/sources.list by adding "deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main" and then "sudo apt-get update". Repositories won't respond. Synaptic Package Manager which worked fine two minutes ago won't update most of the repositories either. Running Automatix generates 404 errors all over the place. Remove that line and all's well again.[/QUOTE]

I am glad that you have been able to (hopefully) resolve most of your problems on Ubuntu...sadly I have not (yet) solved my problems :cry:  ( [http://ubuntuforums.org/showthread.php?t=196201&page=2](http://ubuntuforums.org/showthread.php?t=196201&page=2)

---

