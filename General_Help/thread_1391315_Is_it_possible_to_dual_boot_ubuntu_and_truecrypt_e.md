---
title: "Is it possible to dual boot ubuntu and truecrypt encrypted windows?"
date: 2010-01-26
forum: General Help
---

### Post by joemn on 2010-01-26
I am trying to setup a dual boot system with windows and ubuntu where the windows patition is encrypted using truecrypt. The trouble is getting the dual boot working with ubuntu, because truecrypt has its own MBR and boot loader. Most of the docs out there are old and are only for legacy grub, not grub2, which ubuntu 9.10 uses. Also, I have read people here complaining that they couldn't get the truecrypt dual boot to work with grub2.

Does anyone know (or know where I can find out) how to setup a truecrypt dual boot where the linux portion uses grub2?

---

### Post by joemn on 2010-01-26
For example, this: [http://grub.enbug.org/TrueCrypt](http://grub.enbug.org/TrueCrypt) says that if you install truecrypt and overwrite grub's MBR, just pushing escape at the password prompt will bring up grub, however that was not true when I tried it. It said there was no bootable partition. Maybe that was because I hadn't created a separate (primary) boot partition and just had linux using a single (logical) root partition with a (logical) swap partition. I don't know.

---

### Post by relaxmosphere on 2010-02-01
working the issue, trying to find the answer. Truecrypt's documentation states that it can only modify/boot from the windows boot loader. I am looking now for directions to change from grub back to the windows bootloader. If I can keep that from screwing up, then I should be able to use truecrypt to do what you are also trying to do.

---

