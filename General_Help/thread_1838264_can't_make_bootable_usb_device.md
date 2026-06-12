---
title: "can't make bootable usb device"
date: 2011-09-03
forum: General Help
---

### Post by moonpoppy on 2011-09-03
hi. 

i formatted a tiny tuff usb stick and it has this SecureDigital drive (generic xD/SD/M.S.) protection on it. i formatted it to make a liveusb. part of the usb stick reformatted but it would not become a bootable usb. and now no matter what usb stick i use i can't make a liveusb because that SecureDigital  thing is somehow haunting me in /dev and disk utility/gparted.

i can't format or unmount SecureDigital thing-o in disk utility (in disk utility it has a square with an eject button as its icon in faenza iconography - i have no idea what that icon means) or gparted and i can't erase SecureDigiital drive (generic xD/SD/M.S.) in dev/sdb by 

sudo -rm -f /dev/sdb
sudo shred -/f /dev/sbd

i keep getting the error
shred: /dev/sdb: failed to open for writing: no device found

or by the mdmad method of

mdadm --manage /dev/sdb --fail /dev/sdb
mdadm --manage /dev/sdb --remove /dev/sdb
mdadm --manage --stop /dev/sdb

i have no idea what to do.

thank you.

---

### Post by moonpoppy on 2011-09-03
i also tried to reformat the tiny tuff stick in widows. it completely destroyed windows as well. stay away from verbatim tiny tuff usb sticks!!!!!!! 

i put another connected another usb stick into the same ubuntu partiton as the tiny tuff stick and it corrupted that usb stick. 

i erased my entire harddrive. i didnt lose anything. it's all backed up previous  to using the tiny tuff usb stick. but now i can't put an os on it. I DON'T HAVE PERMISSION ON AN EMPTY HARDRIVE?! 

can someone please help?  this is crazy....

---

