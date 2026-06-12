---
title: "Asus eee pc 1005ha, wireless not working, 10.04"
date: 2010-06-16
forum: General Help
---

### Post by meh_phistopheles on 2010-06-16
Hi,

I have wired internet on my asus 1005ha, but I can't figure out how to get the wireless to work. I've been searching for an answer for the past 2 days and can't find anything. I've tried [this]("http://ubuntuforums.org/showthread.php?t=1467073") and a whole bunch of other things which I'm unable to describe because I had no idea what I was doing in the first place.

Fyi, I bought my computer from this website called eracks (absolutely terrible experience, don't ever buy anything from them) which pre-installed ubuntu 10.04 for me. When I got the computer, there was a note with it that said there were custom kernels installed, and that I shouldn't download anything that begins with "linux-" in the update manager. That's how my problem started in the first place, I updated a bunch of "linux-" things thinking I could easily find a solution, but I was wrong.

---

### Post by CharlesA on 2010-06-16
Can you try booting off a livecd/usb and see if wireless works for you?

Also, is it turned on in the BIOS?

I've got a Asus EEEPC 1005HA that runs Ubuntu 9.10 fine for wireless. I'm booting off a livecd and seeing what happens with 10.04.

EDIT: Checked with a 10.04 livecd, wireless works fine. lspci -nn shows this:
```

01:00.0 Ethernet controller [0200]: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adaptor [1969:27c5] (rev 02)
02:00.1 network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
```

---

### Post by meh_phistopheles on 2010-06-16
I tried booting off a live usb and it was the same as it is now, the wired worked but the wireless didn't. The BIOS said wireless was enabled both before the live usb boot, and after, so I don't think it changed to disabled or anything during the boot. Also, here's what I get when I do lspci -nn. It's the same for both the live usb and now:

```
01:00.0 Ethernet controller [0200]: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)
02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:002c] (rev 01)
```

---

### Post by CharlesA on 2010-06-16
Looks like it's a different chipset. Do you have any hardware drivers available?

---

### Post by meh_phistopheles on 2010-06-16
No. There's nothing in the hardware drivers screen.

---

### Post by CharlesA on 2010-06-17
Out of ideas, not sure what to tell which chipset the wireless is using without using lspci. :(

---

### Post by meh_phistopheles on 2010-06-17
It's cool. Thanks for the help though. I think I'm going to put this question on launchpad.

---

