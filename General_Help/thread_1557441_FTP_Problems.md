---
title: "FTP Problems"
date: 2010-08-20
forum: General Help
---

### Post by Wipster on 2010-08-20
Hey all,

I have been having problems with ftp in linux for some time now and I'm finally going to try and fix this. This issue first raised its head in the last LTS I believe and has been here ever since, and is apparent in Backtrack so isn't Distro specific it seems. Also apparent on other computers so possibly not a driver fault.

So I mess around with OpenWRT allot on my router which means frequent re-flashes with the bootloader's FTP server and I have verified its not the router as ftp transactions work flawlessly on XP.

The issue is when I try and transfer a file to the router it stops on the first hash mark when in debug hash mode, and the only way to get it to send the entire file is to reboot the machine and try again straight away without connecting anything. sudo ifconfig eth0 down and up doesn't solve it, apparently it needs to be powered down.

Thanks for reading, sleep time :)

Edit: 
I have tried ifdown --force eth0 and ifup again to no avail.
I have also tried /etc/init.d/./networking force-restart and nada.

---

### Post by Wipster on 2010-08-24
This forum moves very fast, does anyone know of anything I can try or has experienced anything like this?

---

### Post by Wipster on 2010-09-01
Really? No other person has seen this behaviour or has any idea on how to debug it, am I stuck using windows to flash?

---

