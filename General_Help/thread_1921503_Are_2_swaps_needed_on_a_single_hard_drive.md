---
title: "Are 2 swaps needed on a single hard drive ?"
date: 2012-02-06
forum: General Help
---

### Post by Krishna Murthy on 2012-02-06
Hi 

I have Natty and Lisa on the same hard drive and both have created 2 GB swaps during installation.

Are both swaps needed ?
Is it safe to remove one and use that space ? If so, how do we go about it ?

Thank you.

---

### Post by 73ckn797 on 2012-02-06
I have used a dual boot with 10.04 and 11.10 on a single drive and only had a single swap partition. No noticeable issues.

I have installed a separate third hard drive on a desktop unit and dual boot 10.04 and 11.10, each on a separate drive. Each drive has its own swap. I may experiment with designating the third drive as swap for the second OS. If it works then I will setup 12.04 and use the other drive as a swap. It might create a little more speed since a drive will not be doing double duty between swapping and reading the OS and apps.

---

### Post by carl4926 on 2012-02-06
Only one swap is needed
Though removing the last one created may require you edit the files: fstab and device.map

It's not actually doing any harm, so it might be easier to just clean it up next time you do a installation (Over the install that created the last one)

---

### Post by 73ckn797 on 2012-02-06
Found this:
Optimizing Swap performance Because  swap space uses a disk device, this can cause performance issues in any  system that uses swap space significantly because the system itself may  also be using the same disk device at the same time that it is required  for swap operations. One way to reduce this problem is to have swap  space on a different physical drive so that the competition for that  resource is either reduced or eliminated.
 Link: [https://help.ubuntu.com/community/SwapFaq?action=show&redirect=SwapSpace](https://help.ubuntu.com/community/SwapFaq?action=show&redirect=SwapSpace)

---

### Post by sportfreak2020 on 2012-02-06
i was gonna paste the same link ... :D

---

### Post by ecopccare on 2012-02-07
> Found this:
Optimizing Swap performance Because swap space uses a disk device, this can cause performance issues in any system that uses swap space significantly because the system itself may also be using the same disk device at the same time that it is required for swap operations. One way to reduce this problem is to have swap space on a different physical drive so that the competition for that resource is either reduced or eliminated.
hey! that's what I always did intuitively, nice to see others concur.
I have a quadruple boot situation and all my linuxes use the same swap space

---

