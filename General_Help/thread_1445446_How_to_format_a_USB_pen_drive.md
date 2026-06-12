---
title: "How to format a USB pen drive?"
date: 2010-04-02
forum: General Help
---

### Post by arnab_das on 2010-04-02
How do I format a USB pen drive? It would be great if there was a GUI solution and not a CLI one. thanks.

---

### Post by oldfred on 2010-04-02
I just formated with gparted. Normal installs do not have gparted since you can only use it on umounted partitions. 

Install gparted.
plug in USB device, and then unmount it.
start gparted in system, administration
choose usb device and right click to choose type of format.

---

### Post by arnab_das on 2010-04-02
> **oldfred said:**
> I just formated with gparted. Normal installs do not have gparted since you can only use it on umounted partitions. 

Install gparted.
plug in USB device, and then unmount it.
start gparted in system, administration
choose usb device and right click to choose type of format.

thanks.

i can see the partition but only when the usb drive is mounted. once i unmount it, all i can see are the hard drive partitions. should i format the usb drive while its mounted?

---

### Post by coffeecat on 2010-04-02
> **arnab_das said:**
> thanks.

i can see the partition but only when the usb drive is mounted. once i unmount it, all i can see are the hard drive partitions. should i format the usb drive while its mounted?

No, you can't format a mounted partition. I don't understand what you mean by not being able to see it when it's unmounted. Gparted will show all partitions, mounted or unmounted. You can unmount a mounted partition in Gparted by right-clicking on it.

By the way, there is a simpler inbuilt GUI app which can format USB drives. Look in System > Administration > Disk Utility.

---

### Post by arnab_das on 2010-04-03
okaey dokey. thanks.

actually what i was doing was 'safely remove drive' instead of unmount. :)

---

### Post by TheNerdAL on 2010-04-03
Mark [SOLVED] if solved. :)

---

