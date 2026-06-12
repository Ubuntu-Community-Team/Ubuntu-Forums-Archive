---
title: "Ubuntu full installation, now windows 7 install???"
date: 2011-05-02
forum: General Help
---

### Post by SENTINEL5000 on 2011-05-02
Hi to all. Ok I have a gateway laptop on which I installed Ubuntu 10.10 in the entire drive (used entire disc option). Id like to install windows 7 on it to dual boot but when I put in the disc it says I cant install on the partition since its not NTFS format. How can I create an NTFS partition so I can install 7 in it? Thanks in advance!

---

### Post by SkyNet2029 on 2011-05-02
The usual order of operations is to install Windows first, then install Ubuntu.
The Windows boot loader won't load a linux partition. The Ubuntu loader will give you a choice of booting into Ubuntu or Windows.
So, Install Windows, then install Ubuntu to have proper boot loader operations.
Sorry to be the bearer of bad news.

---

### Post by SENTINEL5000 on 2011-05-03
Ok, so um, since its not letting me install 7 over Ubuntu, how can I erase Ubuntu so I can install first 7 and then Ubuntu?

---

### Post by Rubi1200 on 2011-05-03
> **SENTINEL5000 said:**
> Ok, so um, since its not letting me install 7 over Ubuntu, how can I erase Ubuntu so I can install first 7 and then Ubuntu?

Contrary to the advice you received from the previous poster you do NOT have to erase Ubuntu to install Windows.

Yes, Windows will take control of the MBR again, but with 2 commands from the LiveCD and 1 more back in Ubuntu you will be happily dual-booting.

to help us figure out why you received that error, go into Ubuntu and post the output from the following command:

```
sudo parted -l
```
(lowercase L not 1)

Thanks.

---

### Post by HermanAB on 2011-05-03
Howdy,

The easier and more flexible solution is to install Virtualbox and then install Windows as a virtual machine.  You can then run Windows in a window, where it belongs and use Windows applications concurrently with Linux applications.

---

