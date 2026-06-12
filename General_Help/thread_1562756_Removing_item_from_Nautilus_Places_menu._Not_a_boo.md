---
title: "Removing item from Nautilus Places menu. Not a bookmark."
date: 2010-08-28
forum: General Help
---

### Post by Rammatamago on 2010-08-28
I was trying to install Sim City 4 Deluxe when somehow through my mounting an un-mounting of the two ISO's nautilus decided to make an entry in the places menu.

I've searched through the forums and most of what I'm finding is how to remove things like the network and desktop items.

Here are three screenshots showing what I mean.


Number one shows the entry I am talking about, specifically the SC4DELUXE1 entry.

Number two shows that just right clicking and selecting remove like many threads suggest does not work here as it is grayed out.

Lastly number three, this is the error I'm given when I left click the entry.

Thank you for any help!

[SOLVED]

I finally figured out how to fix this. I simply went into the disk utility. Under peripheral devices the unwanted device was listed. Click the check file system button after selecting the device. It reports back that the file system is not clean and removes the device.

---

### Post by Rammatamago on 2010-08-28
Bump.

---

### Post by tomski on 2010-11-21
if you use the disk utility to 'label' your partitions when you mount them they will be listed by label within 'Places' inside nautilus

if a drive or partition does not have a label nautilus will use a unique attribute as a descriptor similar to size

---

