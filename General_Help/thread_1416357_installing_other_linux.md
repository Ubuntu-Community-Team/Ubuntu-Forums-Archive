---
title: "installing other linux"
date: 2010-02-26
forum: General Help
---

### Post by chriszatch on 2010-02-26
I am going to be installing Fedora and ubuntu is already installed. Will Fedora's boot loader try to run over ubuntu? I've never dual-booted two linux os's before that werent both ubuntu. Will i have to worry about restoring grub?

edit: its probably important to tell you that i am running Karmic Koala so i am using Grub 2

---

### Post by chriszatch on 2010-02-26
bump

---

### Post by r_s on 2010-02-26
Haven't used fedora, but for any other OS(linux not windows) it will automatically detect your ubuntu partition and make an appropriate entry for it in the grub file.Even if it doesn't you can do it manually.

---

### Post by JK3mp on 2010-02-26
It will/should ask you to either proceed installing grub or to keep original grub, or show an area where you can click to not install new grub. Either way if it reinstalls grub (since both ubuntu and fedora use grub) it should make an entry for your Ubuntu in the menu as long as you didn't overwrite the ubuntu partition when you install it. You should be fine either way.

---

