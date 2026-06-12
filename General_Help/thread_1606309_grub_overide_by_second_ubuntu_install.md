---
title: "grub overide by second ubuntu install"
date: 2010-10-26
forum: General Help
---

### Post by gwu777 on 2010-10-26
Hi there, so I have a second ubuntu install for testing purpose. It has been like that for a while and usually grub2 plays fine. When the second grub got updated, I used to go to my main install and run an update-grub and everything was back to normal with the setting defined in my good install.

However since I have updated my testing install with maverick, I cannot overide my second grub with the original. I go to my main install, ru the update-grub, it goes ok however when I restart I have the testing grub.

I realise that the story might be confusing and I should not have 2 grubs working that way, but right now, I am stuck with a grub I don't want.

Following a few search, I have come to realise that I should have some kind of chainloader, I will do this promise as soon as I get my hand back on my original grub.

---

### Post by oldfred on 2010-10-26
sudo update-grub will add the new system to the grub menu, but not install grub to the MBR. You have to decide which system you want in the MBR and that then is the one that boots first.

You can boot into either install and install that systems grub into the MBR and it will boot that first.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by gwu777 on 2010-10-31
Thank you for that. I did try this, but as it happened, my disk had errors. Wich is quite weird. I had to reinstall everything and now my grub is working and I am setting up new grub chain loader.

---

