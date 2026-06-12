---
title: "Increase swap size"
date: 2011-12-18
forum: General Help
---

### Post by vat with tux on 2011-12-18
I have installed ubuntu using wubi installer. So having default swap size only 256MB. My RAM is 1GB so many time system stars crying demanding more swap....:) I have read [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) . But not still not sure about how to increase swap size when ubuntu is installed using wubi. 

So kindly help me out ... Thanking in advance...:)

---

### Post by Elfy on 2011-12-18
[https://wiki.ubuntu.com/WubiGuide#How_do_I_increase_my_swap_space.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_increase_my_swap_space.3F)

You might be able to use a swap file instead of increasing the existing swap - in the swap faq you reference look for > Four-step Process to Add Swap File

---

### Post by BC59 on 2011-12-18
From the Wiki guide:

How do I increase my swap space?

The following will increase your swap to 2 GB. Replace count= with the number of kilobytes you want for your swap file.

sudo su
swapoff -a
cd /host/ubuntu/disks/
mv swap.disk swap.disk.bak
dd if=/dev/zero of=swap.disk bs=1024 count=2097152
mkswap swap.disk
swapon -a
free -m
The final free statement will verify that your new swap file has the correct space. If everything worked, issue the following command and you are done. If it didn't work, then remove swap.disk and move swap.disk.bak back to swap.disk and try again.

rm swap.disk.bak

---

### Post by HermanAB on 2011-12-18
It is all described in the swapon man page:
$ man swapon

Totally illogical, but the man page, once discovered, is actually very good.

---

