---
title: "Can't open ubuntu after Windows format"
date: 2012-03-10
forum: General Help
---

### Post by harbimilan on 2012-03-10
Hi,
I had Windows 7 and Ubuntu 10.10 working in different partitions of my hard disk, but then I had to format the windows partititon and install a newer windows version.

I have done it but now when I open the computer, I do not see the GRUB bootloader screen or anywhere that I can choose to boot Ubuntu.

But I'm pretty sure that the ubuntu partition is unharmed, so how can I enable GRUB back?

Thanks for help!

---

### Post by kc1di on 2012-03-10
Windows has overwritten your Master Boot Record you'll need to reinstall grub Here's how to do it:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Here's another page:
[http://askubuntu.com/questions/83771/recovering-grub-after-installing-windows-7]("http://askubuntu.com/questions/83771/recovering-grub-after-installing-windows-7")

---

### Post by cycling-rod on 2012-03-10
Have a look through these websites on the subject of reinstalling Grub: [http://www.google.com/cse?cx=partner-pub-9300639326172081%3A5191442144&ie=UTF-8&sa=Search&q=reinstalling+Grub+Ubuntu&hl=en-gb#gsc.tab=0&gsc.q=reinstalling%20Grub%20Ubuntu&gsc.page=1](http://www.google.com/cse?cx=partner-pub-9300639326172081%3A5191442144&ie=UTF-8&sa=Search&q=reinstalling+Grub+Ubuntu&hl=en-gb#gsc.tab=0&gsc.q=reinstalling%20Grub%20Ubuntu&gsc.page=1)
Hope they will provide the answer you need!

---

### Post by harbimilan on 2012-03-10
> **kc1di said:**
> Windows has overwritten your Master Boot Record you'll need to reinstall grub Here's how to do it:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Here's another page:
[http://askubuntu.com/questions/83771/recovering-grub-after-installing-windows-7]("http://askubuntu.com/questions/83771/recovering-grub-after-installing-windows-7")

Hi,
thanks for reccomendations, I installed EasyBCD and created a new boot entry and succeeded to boot ubuntu, but now I have to pass 2 bootloader screens. How can I make GRUB the default bootloader and don't need EasyBCD's boot entry anymore?

---

### Post by Mark Phelps on 2012-03-11
> **harbimilan said:**
> Hi,
thanks for reccomendations, I installed EasyBCD and created a new boot entry and succeeded to boot ubuntu, but now I have to pass 2 bootloader screens. How can I make GRUB the default bootloader and don't need EasyBCD's boot entry anymore?

Go into Windows and use EasyBCD to remove the Ubuntu entry.

Then, use the info in the link about reinstalling GRUB after windows.

---

