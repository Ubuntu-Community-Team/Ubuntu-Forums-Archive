---
title: "pcmcia works, but doesn't work"
date: 2006-03-08
forum: General Help
---

### Post by dmizer on 2006-03-08
so i have a wireless pcmcia network card that works perfectly in ubuntu.  i'm happy with that.  however, i can't use the wireless at work, so i need to get a network adapter running.

my box is a japanese version nec versapro va90j.

the integrated nic is shot (i think), as it won't pull an ip in any os i've installed on it (haven't tried windows yet though).  but there shouldn't be a problem with the integrated nic, because it's a linux supported intel pro 100 82557 (rev 8).

so i defaulted to my old standby for linux os network support, my (once again natively supported) linksys np100 adapter.  but ubuntu doesn't even see it.  it shows in the device manager as an unknown device.

i've done some fairly extensive hunting on the internet and haven't been able to come up with any definitive answers.

the network adapter works fine in knoppix 3.8, so i know the pcmcia slot isn't bad, and i know that the card works.

according to dmesg, my card bus is a yenta, and i've read that those are particularly troublesome.

---

### Post by dmizer on 2006-03-09
i found the problem.  just not to sure how to correct it.

according to cardctl ident:
cardctl ident:
Socket 0:
product info: "Psion Dacom", "Gold Card Global 56K+Fax", "56K+Fax", "V8.25"
manfid: 0x016c, 0x0005
function: 2 (serial)
Socket 1:
product info: "Network Everywhere", "Fast Ethernet 10/100 PC Card", "3.0", "AX88190"
manfid: 0x0149, 0xc1ab
function: 6 (network)

the card is listed as AX88190, but my dmesg lists it as:
pcnet_cs: this is an AX88190 card!
pcnet_cs: use axnet_cs instead.
pcnet_cs: unable to read hardware net address for io base 0x300

i attempted to update my config.opts file according to this post:
[http://lists.suse.com/archive/suse-linux-e/2002-Feb/1114.html](http://lists.suse.com/archive/suse-linux-e/2002-Feb/1114.html)

but that didn't seem to fix my problem.

any other ideas?

---

### Post by 11hjpphty76lkjj on 2006-03-12
Any luck with this?  I'm having the same problem.

Aaron

---

### Post by dmizer on 2006-03-13
yes in fact, just now.

there are two listings in /etc/pcmcia/config for the linksys card.  one i had changed to axnet_cs but i missed the other one.

just open up the config file and do a search for "NP100" and that should point you to where the changes need to be made.

i'm going to go see if i can pull an ip now.

edit: i currently edit this post from my wired network everywhere np100 pcmcia card.

---

### Post by elgormando on 2006-08-26
[FONT="Book Antiqua"][COLOR="Navy"][SIZE="2"]I have tried everything and searched everywhere for this answer.  I am running Dapper Drake on a Compaq Presario 1200TA Laptop and cannot get the Network Everywhere 10/100 Fastethernet card to work.  Here's what I've tried.

Changed the pcnet_cs entries to the cards that look like they should work in the /etc/pcmcia/config filr to axnet_cs.  It still lists this as pcnet_cs in the info.linux.driver key in the Device Manager and does not work.  Before I migrated to ubuntu, I had SuSE on this laptop and this card worked better than it ever has with any other OS.

After searching through the same file, I figured that I simply missed an entry, I changed every card that was listed as binding to pcnet_cs to axnet_cs, because I'm pretty sure that I won't be using any other pcmcia devices (modem still works, wireless is usb and works great).  Still nothing.

I then came across a posting for this problem in Debian and it said to do the same changes and run /etc/init.d/pcmcia reload to which I got an error because of the kernel and then ran /etc/init.d/pcmciautils reload.  Still nothing.

Anyone have any other solutions to this or suggestions?  Really impressed with ubuntu and seriously considering migrating away from Windows for most things after having Service Pack 2 continuously cause problems and reloads.[/SIZE][/COLOR][/FONT]

---

### Post by dmizer on 2006-09-25
okay ... finally sat down and ground this one out again.

i just added pcnet_cs to the end of /etc/modprobe.d/blacklist

also added this entry to /etc/pcmcia/config.opts:
```
card "Fast Ethernet 10/100 PC Card"
  version "Network Everywhere", "Fast Ethernet 10/100 PC Card", "3.0", "AX88190"
  manfid 0x0149, 0xc1ab
  bind "axnet_cs"
```

don't know if the second part made any difference at all or not, but i left it there, because it works now.

i wish i could make config.opts work like it use to so you don't have to blacklist.  would kinda suck if you had another card later that needed pcnet_cs.

edit to add:
i seems it's not necessary to add anything to pcmcia config.opts.  i've created a howto for this card here: [http://www.ubuntuforums.org/showthread.php?t=264954](http://www.ubuntuforums.org/showthread.php?t=264954)

---

### Post by elgormando on 2006-09-25
[FONT="Book Antiqua"][COLOR="DarkSlateBlue"]Thanks, worked like a charm.  I don't know why I didn't think of that before, I was just in there when I first loaded to blacklist IPv6.[/COLOR][/FONT]

---

