---
title: "Wireless issue in 9.10"
date: 2010-09-23
forum: General Help
---

### Post by omicron42 on 2010-09-23
Hi.

To start off, I am proficient at Snow Leopard and Windows... trying to get the hang of Ubuntu now.

I have a MacbookPro 5,1 (I posted here instead of the Apple forum, since I've heard that this was a more general problem with 9.10 - please move this if warranted) that triple boots Snow Leopard, Windows 7, and Ubuntu 9.10. I have all the partition tables and everything setup properly and all of the OS run properly... except that I can't connect wirelessly to the internet inside Ubuntu. The "Wireless Manager" icon that should be in the upper right corner isn't there - only one for wired connections. I couldn't find any other way to reach the wireless manager.aw

I ran through the support provided with it, and when I ran the "sudo lshw -C network" command inside of Terminal, I didn't get the info I was apparently supposed to (either enabled, disabled, etc..).

I got two sections of info, one beginning with:
*-network
          description: Ethernet Interface
and a bunch of other details which I couldn't relate to whether my wireless card was going or not, and the second batch of info beginning with:
*-network
         description: Network Controller
with similarly lacking info.

Also, I'm really just trying to connect so that I can update to 10.04 which I'm guessing might solve my issue of the missing wireless icon... but I can't connect inside of 9.10, so I'm in a bit of a Catch-22.


Any guidance would be greatly appreciated!

---

### Post by Vigh on 2010-09-23
You got another computer? Download 10.04 lucid lynx image, and install that. Wireless should work out of the box. I noticed myself 8.04, 9.04 etc. wireless worked, and on 9.10 I had some difficulties. Otherwise try plugging into the hub via ethernet cable, update and should fix your wireless problems. Have run 10.04 with no problems, now running 10.10 beta with no problems.

---

### Post by omicron42 on 2010-09-23
Just have the one computer, or else I would've tried that too. I just noticed however, that I posted on this same topic back in June when I first tried to fix it... I'm going to try some of the updates in that thread since I forgot about it and post back here if I have any success. Getting access to the hub might be tricky, but I think I'll have to do that if nothing else works.

Thanks

---

### Post by omicron42 on 2010-09-23
Okay, so I ended up just connecting to the router and downloading a copy of 10.04... but that didn't solve the wireless issue.

However, as I went about investigating the repeat problem..... I accidentally deleted the top menubar. I have absolutely no idea how to get it back, or how to navigate ubuntu without it.

Help?

---

