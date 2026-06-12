---
title: "Browse to a directory (or) Use USB Drive."
date: 2010-01-21
forum: General Help
---

### Post by Merp123 on 2010-01-21
Hi,

I installed Ubuntu 9.10 as Guest OS with Windows XP as Host using Virtual Box. I have also installed the VirtualBox Guest Additions. Now I want to connect to the internet using my modem.

[https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)

From the above link, I downloaded the scanModem file from the Host XP. I don't know how to copy that file to the Guest Ubuntu OS.

[http://132.68.73.235/linmodems/first.html](http://132.68.73.235/linmodems/first.html)

I couldn't find the _/mnt/msdos_ directory - only _/mnt_ (no files inside that directory). Also, don't know how to paste from the USB drive.

Plz. tell me how to do this.

Thank you,
prem.

---

### Post by fsando on 2010-01-26
I'm not familiar with virtualbox under windows but I will try anyway.
The instructions you are referring to appear to be for an actual installed linux not one in virtualbox. Virtualbox must be able to communicate directly with windows xp in some way and I'm sure it is.

There should be an option in virtualbox to add or enable networking and usually you have the options: 'bridged' 'nat' and 'host only' or something very similar. Ideally you would use the 'bridged' option but there may be reasons this will not work so try out the other options.

To enable to transfer files between the two you would start by making a folder sharable in the host (right click on folder and choose 'sharing'). Then in the guest you will look for shared network resources (in ubuntu: places > network) and hopefully the shared folder will show up.

If sharing for some reason does not work and you need to transfer files between the two you can use an USB key. Virtualbox should be able to see it

Btw. this about the folder '/mnt/msdos' is specific to a dualboot situation. And if you dualboot with ubuntu/windows the folder would be '/media/' not '/mnt/'.

---

