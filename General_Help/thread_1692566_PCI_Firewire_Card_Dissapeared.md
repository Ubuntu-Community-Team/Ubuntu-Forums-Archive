---
title: "PCI Firewire Card Dissapeared ???"
date: 2011-02-21
forum: General Help
---

### Post by FranklinFick on 2011-02-21
i am using ubuntu 10.04 64bit

earlier today i went to edit some video with Kino
and the capture function was not working
 it gave me the error that the dev/raw1394 kernel was not loaded or did not have the read/write permissions

I have not gotten this error since I first downloaded Kino some years ago and fixed this issue

i always load Kino as root and have no problems
(sudo open kino from terminal)

lspci was showing that the card was detected
but grep 1394 /var/log/kern.log
was showing that the kernel was not loading
(i think it was showing a timeout error but can't recall with confidence)

i searched around and tried some fixes 
like 'gksu gedit /etc/modprobe.d/blacklist-firewire.conf'.
and chmod the dev/raw1394 which came back as the file is not found

this only made it worse
now the lspci is no longer showing the firewire card at all

no idea what I did or how to fix it

and its pretty important- need the firewire working for my work


also have no idea why all of a sudden kino and the firewire were not working (used it about a week ago and everything was fine)

the only thing that i changed on the system since then was i download blogilo and to get it to work properly i had to install kdebase-workspace


if anyone could help that would be great

thanks

franklin

---

