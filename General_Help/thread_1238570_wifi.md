---
title: "wifi"
date: 2009-08-12
forum: General Help
---

### Post by davewickett on 2009-08-12
i have ubuntu & vista daul-boot on my laptop ive sorted out setting up my wifi on ubuntu i have a atheros ar5007 (ar424x) with madwifi-ng when i reinstalled ubuntu my wifi card was working on its own dont know why so i can just leave that now as ive installed backtrack 4 pre on my 8gb usb stick but dont know how to set up my wifi card on it so if there is someone who can give me some commands to set it up with madwifi & do i need to reboot to activate it as ive got it on usb i dont mind doing the commands to get it up & running each time if i know them i do know a way to make it save changes each time to partition the usb that i could try to do if i have to hope someone can help me thanks
dave

---

### Post by warp99 on 2009-08-12
If you're talking about getting wireless running on Backtrack 4 then you're on the wrong forums. You should be asking that question here:

[http://forums.remote-exploit.org/](http://forums.remote-exploit.org/)

Backtrack may be using a special kernel or modules that are different then the Ubuntu releases.

---

### Post by davewickett on 2009-08-12
ok i have been on there aswell but as i have ubuntu just thought ill see if anyone knows on here ive sorted my wifi working that card works out the box just need help with madwifi with it but ill sort it out thanks anyway

---

### Post by warp99 on 2009-08-12
With Ubuntu if you want to use the madwifi drivers you just install the ubuntu-restricted-modules package then un-blacklist the ath_pci module and blacklist the ath5k module. With Backtrack 4 your guess is as good as mine since it's a derivative distro. That's why it's best to ask on that board.

---

