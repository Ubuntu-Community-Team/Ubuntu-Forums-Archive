---
title: "Removing auto-mounted partitions"
date: 2012-08-07
forum: General Help
---

### Post by manuleka on 2012-08-07
i've just installed Xubuntu 12.04 and by default it automatically loads partitions and make them available... i have used Linux before but fallen back to Windows so I'm giving it another this time...

can someone tell me or show me how to remove some of these partitions from automounting?

cheers for any help...

---

### Post by coffeecat on 2012-08-07
Unless you've set up /etc/fstab to mount all your partitions during bootup, they have not been automounted. It is a feature of Xubuntu 12.04 that it will put icons for each available partition on the desktop, but they are not yet mounted. To automount one, you need either to double-click on the icon, or open the file manager (Thunar) and click on the partition in the left pane that you want mounted. The difference between the intensity of greyness of the icon for mounted and not-mounted partitions in the left Pane of Thunar is subtle, but you should be able to see the difference.

I can see how a number of icons on the desktop gives the impression that they are mounted, but they are not by default. You can prevent partition icons from being displayed on the desktop by right-clicking on the desktop -> Desktop Setting -> Icons tab -> untick Removable Devices. Unfortunately, this has the effect of preventing icons for mounted USB drives from appearing on the desktop, although the USB drives will still appear in the file manager.

---

