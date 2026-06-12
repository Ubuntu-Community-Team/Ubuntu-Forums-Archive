---
title: "Won't connect to my WiFi network!"
date: 2011-05-14
forum: General Help
---

### Post by Cam! on 2011-05-14
I'm a long-time Ubuntu user, and setting up my connection was as easy as putting in my WEP key, and that was it!

I installed Kubuntu 11.04, and it's really difficult. I located my wireless network, and after putting in my WEP key, it just says " Setting Network Address", while prompting me to re-enter my WEP/Hex key. After repeatedly entering the password, I get a red circle/slash icon in lieu of the network icon.

---

### Post by TBABill on 2011-05-14
Did you enable the KDE Wallet? I had to do so in order to get the system to permit use of my wireless.

---

### Post by Cam! on 2011-05-14
I permitted KWallet numerous times, to no avail.

---

### Post by linuxuser12345 on 2011-05-14
OMG, CAM! I LOVE YOUR PROFILE PICTURE!!!! :D
Daft Punk is da $h1ttttttt!!!!!! :P

---

### Post by Cam! on 2011-05-14
......Can I get some HELP? -_-

---

### Post by enimeizoo on 2011-05-15
Did you try different key types? The auto-selected one is sometimes wrong, you should try others. (hex/ascii or passphrase)

If that doesn't work, and if you are more concerned about connecting than fixing your network manager, try installing wicd. It is another network manager that worked fine with me when knetworkmanager failed.

I hope it helped
(edit) Do you have a wired connetion?

---

### Post by Cam! on 2011-05-15
I don't use a wired connection. Just to make sure, I re-installed Ubuntu, and everything seems to be normal.

....But I still have that KDE problem!

---

### Post by Cam! on 2011-05-15
Update. No matter what I do, it still won't connect at all. I've tried switching between using my conventional password with the hexadecimal one, but nothing changes.

---

### Post by enimeizoo on 2011-05-15
Did you try that?
[Manual network configuration]("http://ubuntuforums.org/showthread.php?t=571188")

knetworkmanager does have troubles sometimes. After you get acces to the internet, consider installing another network manager, like wicd.

---

