---
title: "kswapd0 freezes Ubuntu11.11 on Netbook"
date: 2011-05-17
forum: General Help
---

### Post by snowyandrain on 2011-05-17
Hi all,
I am using Ubuntu11.11 on my Samsung netbook. Since my installation, I am meeting a problem from time to time that the process kswapd0 leads to high data exchange of my solid-state hard-disk, and freezes the entire system which forces me to restart my computer. This problem occurs even though kswapd0 occupies only 28% CPU resource.

Can anyone give me a clue how to deal with such problem?

Thanks

Kv

---

### Post by CoolJohnB on 2011-05-17
Being as 11.11 is alpha or even earlier suggest you try 11.04

---

### Post by songrit on 2011-05-21
Confirm this happen on Ubuntu Natty 11.04 netbook Lenovo s10-3t every time I played video using vlc for about 3-5 minutes then it freeze, kswapd0 is topped. Surprisingly after the things is done, sub sequence play of the same video has no problem.

This behavior did not exist at all in Ubuntu 10.10 UNE It's a new bug introduced in 11.04 (which discard netbook edition) my guess is that the netbook memory is limited to 2GB cause system to go swapped.

--edited
somebody said it's a pulseaudio issue, it's supposed to be fixed in vlc 1.2 but in repo the latest is only 1.1.9

[http://forum.videolan.org/viewtopic.php?f=13&t=89621](http://forum.videolan.org/viewtopic.php?f=13&t=89621)

---

### Post by snowyandrain on 2011-06-05
Well, songrit is probably right. I tried using a USB MEM stick functioning as a swap partition and no freezing happens any more. I think it might be the problem that swap on solid-hard-disk goes not well.
But this cost me a usb mem stick...Leider.
Commands,
$sudo swapoff /dev/sda5
$sudo swapon /dev/sdb1

---

