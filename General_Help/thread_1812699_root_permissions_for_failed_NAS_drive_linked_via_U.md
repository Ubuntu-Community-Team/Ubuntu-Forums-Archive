---
title: "root permissions for failed NAS drive linked via USB and live CD"
date: 2011-07-26
forum: General Help
---

### Post by tommason on 2011-07-26
Hi,

I'm having some difficulties : ( 
I own a Lacie Network Space (1) which has recently given up the ghost - I looked into getting data recovered from it and it turns out it would cost around 500quid!! After doing some research I've found out that the drive runs linux - SO, I have bought myself a HDD cradle, Downloaded an Ubuntu Live CD, taken the drive out of the network space and mounted it in Ubuntu via USB. All good up til now, I've managed to get the majority of my data off except one folder - my music folder. It has quite a deep file structure (which maybe the issue) but essentially the permissions for the top folder have a padlock and a small cross - this doesn't allow me to even read the files to copy them off. I've now tried the 'chown' command:
sudo chown ubuntu /media/999GBfilessystem/openshare/audio
But I'm getting the reply: 
"no such file or directory"
Any help would be much appreciated : )

Cheers!

Tom

---

### Post by tommason on 2011-07-26
ok - my filepath wasn't quite right, I eventually managed to chown it - the real deal was reading another post on here - and trying:
sudo chmod 755 /path/of/file -R
Which worked a treat : ) now I just have to figure a way of juggling the files back onto my imac....

---

