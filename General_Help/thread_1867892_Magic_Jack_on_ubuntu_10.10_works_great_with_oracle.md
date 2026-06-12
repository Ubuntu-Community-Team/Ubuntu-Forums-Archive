---
title: "Magic Jack on ubuntu 10.10 works great with oracle VM"
date: 2011-10-23
forum: General Help
---

### Post by taoist33 on 2011-10-23
I've been running Ubuntu 10.10 my preference and needed to get the magic jack installed and running. Ran through a lot of different solutions and found an excellent article which in the end got it all up and running .  Able to receive and send calls no problem now.

here is the URL [http://oracology.net/2011/07/magicjack-ubuntu-lucid-lynx-vmware-guide-and-a-rant/](http://oracology.net/2011/07/magicjack-ubuntu-lucid-lynx-vmware-guide-and-a-rant/)

Basically you install oracle VM & guest additions

than install your windows OS of choice in the VM I'm using XP

make sure to add your user name into the vboxusers group under admin/users & groups

Once your in the oracle VM be sure to go to settings usb and add the appropiate usb devices .  My magic jack has a tiger internet phone device and generic mass storage device for both

In order to recieve calls you will have to goto settings in the Virtual machine and under network change the setting from "NAT" to "Bridged" and under advanced network settings change the mode to "allow all".

Now the magic jack works like a charm and I've kicked my t-mobile cell phone to the curb. Their bills are grand larceny lol.

---

### Post by Mchswn on 2011-10-29
I managed to find a way to make magic jack work in Ubuntu 11.10 Oneric Ocelot without the use of guest additions. Please follow the link for instructions.

[Magic Jack inst..odt]("http://ubuntuforums.org/attachment.php?attachmentid=205797&stc=1&d=1319914834")

---

