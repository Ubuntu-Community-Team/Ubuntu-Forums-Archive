---
title: "How to optimize 12.04 on a netbook"
date: 2012-09-03
forum: General Help
---

### Post by galois1 on 2012-09-03
Hi. I'm using 12.04 on my laptop and it works Fine. Now I've installed it in my netbook (Toshiba nb500) and works slow. What can I do in order to improve its efficiency?

---

### Post by GreatDanton on 2012-09-03
Please post your computer configuration.

Regards.

---

### Post by galois1 on 2012-09-03
Here you are: [http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&com.broadvision.session.new=Yes&PRODUCT_ID=1101441]("http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&com.broadvision.session.new=Yes&PRODUCT_ID=1101441")

---

### Post by jmate24 on 2012-09-03
Use Lubuntu 32-bit OS. instead of Ubuntu, Kubuntu, UbuntuStudio, or Xubuntu.

---

### Post by GreatDanton on 2012-09-03
My first thought would be that you don't have enough ram. Ubuntu 12.04 needs at least 1gb of ram (which you have), but I assume you ran out of ram. I usually need more than 1gb of ram, but that also depend on what you are doing. You can lower the swappines (which most likely causes the problems). Look at this link: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq).

But if I were you I would install Xubuntu or Lubuntu, which are less resource hungry, and also good looking IMO. Your Netbook will be much much faster if you try to run Xubuntu, or Lubuntu on it.

Regards.

---

### Post by ajgreeny on 2012-09-03
The OP is already using Lubuntu, so some of your comments are irrelevant.

@ OP: How slow is slow? And what are the comparative specs of your laptop which you say is not slow?

You may simply be expecting too much from a netbook with that spec, but to give a clue of how slow it is, how long does it take for a cold boot, from pressing the power button to the login screen, and then how long after you hit enter from your password to arriving at the full desktop?

I have Lubuntu 12.04 on a similar, but in fact older and slower netbook than yours, and I think mine is fast compared with my other machines.  I will time it later and let you know my times.

---

### Post by galois1 on 2012-09-03
Thank's for your answers. I'll try with Lubuntu; I think it will improve my computer.

---

### Post by temetvince on 2012-09-03
> **galois1 said:**
> Thank's for your answers. I'll try with Lubuntu; I think it will improve my computer.

I agree with everyone else. I ran ubuntu on my netbook (hp mini 110) and it ran horribly, but lubuntu was very nice.

This was quite awhile back, though, so things may have changed.

---

### Post by DogMatix on 2012-09-03
I have run Ubuntu 12.04 on an Acer One ZG8 netbook with very similar specs. to your laptop. I found it ran more slugish than on my higher spec. desktop. ie. startup time, opening applications, etc.

I also ran Lubuntu 12.04 on the same netbook and was happily surprised at the better performance it gave.

Having said that you could check this thread on ask ubuntu for ideas for optimization

[How-to-impove-ubuntu-performance-on-netbook]("http://askubuntu.com/questions/147321/how-to-impove-ubuntu-performance-on-netbook")

BTW Your initial post does have a Lubuntu tag? Are you running it already?

---

### Post by TenPlus1 on 2012-09-03
I have an old Compaq M2000 with a similar spec running Intel 1.6ghz processor with 1gb memory and Intel graphics...  On this I have installed Xubuntu 12.04 and added the following line to the end of /etc/sysctl.conf file:

vm.swappiness = 10

This makes Xubuntu use physical memory before touching the swap partition on the hard-drive which helps speed things up a lot...  Also, Xubuntu is a lot lighter than Ubuntu with Unity interface so works a whole lot better on battery...

---

### Post by temetvince on 2012-09-03
> **TenPlus1 said:**
> I have an old Compaq M2000 with a similar spec running Intel 1.6ghz processor with 1gb memory and Intel graphics...  On this I have installed Xubuntu 12.04 and added the following line to the end of /etc/sysctl.conf file:

vm.swappiness = 10

This makes Xubuntu use physical memory before touching the swap partition on the hard-drive which helps speed things up a lot...  Also, Xubuntu is a lot lighter than Ubuntu with Unity interface so works a whole lot better on battery...

I have found that while Xubuntu is supposed to be lite on resources, it actually is quite resource intensive. I suspect that is why Lubuntu is an official Ubuntu variant and Xubuntu is not, but that is my personal opinion.

Personally, if the only goal is to save system resources, then I would opt for Lubuntu over Xubuntu.

---

### Post by ajgreeny on 2012-09-04
@OP
You tagged this thread as "lubuntu so I assumed you were actually using Lubuntu 12.04, hence my post #6.

Anyway to give you the info I said that I would, it takes 33 secs from power button to login screen, and then 3 or 4 secs from hitting Enter after giving my password to get to the full usable desktop.  That seems pretty fast to me for such a low powered netbook.

---

