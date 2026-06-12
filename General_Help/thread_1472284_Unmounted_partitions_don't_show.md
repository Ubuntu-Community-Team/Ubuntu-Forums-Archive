---
title: "Unmounted partitions don't show"
date: 2010-05-04
forum: General Help
---

### Post by illingd on 2010-05-04
I just upgraded from Karmic to Lucid and have the following problems:

(1) My unmounted partitions used to be visible in "Places" on the left of Nautilus, so I could mount them when needed, but now they are not there. Also,they do not show in "Computer" view

(2) When I open Disk Utility from System/Administration, there is nothing at all showing - it takes quite a while to start up, but when finally the window opens, no devices or partitions are shown.

---

### Post by dino99 on 2010-05-04
> **illingd said:**
> I just upgraded from Karmic to Lucid and have the following problems:

(1) My unmounted partitions used to be visible in "Places" on the left of Nautilus, so I could mount them when needed, but now they are not there. Also,they do not show in "Computer" view
[COLOR="Blue"]on top menu, second choice (shortcuts or so), you should see "removable devices" or so[/COLOR]


(2) When I open Disk Utility from System/Administration, there is nothing at all showing - it takes quite a while to start up, but when finally the window opens, no devices or partitions are shown.

[COLOR="Blue"]no problem on my end, try with MountManager (need to install it)[/COLOR]

sudo dpkg --configure -a
sudo apt-get update && install -f

---

### Post by illingd on 2010-05-04
> **dino99 said:**
> on top menu, second choice (shortcuts or so), you should see "removable devices" or so[COLOR=Blue]
[/COLOR]I don't have "Removable Devices" on the "Places" dropdown from top menu  either!

[COLOR=Blue]> no problem on my end, try with MountManager (need to install it)[/COLOR]
That might be a workaround, but I'd really like to have the functionality that I used to have (and which I assume still should have?)

Thanks for your response.

*Dave*

---

### Post by illingd on 2010-05-04
It gets worse! ...

When I plug in a usb device, that doesn't mount or show up anywhere.

Think I'm going to be reverting to Karmic pretty sharpish, until the new version is a bit less trouble :-(

---

### Post by dino99 on 2010-05-04
> **illingd said:**
> [COLOR=Blue]
[/COLOR]I don't have "Removable Devices" on the "Places" dropdown from top menu  either!

[COLOR=Blue][/COLOR]
That might be a workaround, but I'd really like to have the functionality that I used to have (and which I assume still should have?)

Thanks for your response.

*Dave*

my menu is not in English so i dont know the exact names, search a little :(

---

