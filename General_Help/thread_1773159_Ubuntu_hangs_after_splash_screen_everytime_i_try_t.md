---
title: "Ubuntu hangs after splash screen everytime i try to install it"
date: 2011-06-01
forum: General Help
---

### Post by aswinfrancis on 2011-06-01
I need urgent help.I have been trying a lot.A LOT.to install 11.04 but it doesnt.I tried from CD and pendrive but same thing happens.
Everytime i choose the option 'Install' or Live after the ubuntu splash screen it hangs and shows this
[IMG]http://www.stooorage.com/show/883/2984745_img0050a.jpg[/IMG][http://www.stooorage.com/show/883/2984745_img0050a.jpg](http://www.stooorage.com/show/883/2984745_img0050a.jpg)
(image quality is bad because i couldnt find my camera and used my stupid phone )
I guess it it because of the grahic card.
I have an Asus ROG G60JX laptop with nvidia GTS360M.Previous version of ubuntu also has problems with my graphic card but they where fixed after updating.But this one i cannot even install to update it.
Can someone please tell me how to fix this. :(

Edit:
I checked the MD5 hash and its the same.Just now i tried installing again and the same thing happens.

---

### Post by aswinfrancis on 2011-06-01
I found a way myself.I just ticked all the option after pressing F6(other options) and it worked

---

### Post by scottstensland on 2011-06-01
to harden those F6 check boxes

sudo gedit /etc/default/grub

and put into the double quotes your kernel options
... try to eliminate the unnecessary ones as they disable 
nice things includingkeyboard Fn key combos
used to control volume etc ...

GRUB_CMDLINE_LINUX_DEFAULT="pci=noacpi nomodeset quiet splash"

run 'sudo update-grub' afterwards to update

---

