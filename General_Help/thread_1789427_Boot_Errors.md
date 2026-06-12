---
title: "Boot Errors"
date: 2011-06-23
forum: General Help
---

### Post by ltchronic302 on 2011-06-23
I have an old compaq pesario 2538cl laptop that's been running really slow lately with the stock drive so I decided to upgrade to a bigger one(I previously had ubuntu 9.10). After I installed the new hard drive I put in a ubuntu 11.4 live cd and installed it to the hard drive. When I was told to reboot the machine I did so but could never get linux to boot, it would say something like drive not found and send me to the boot loader screen(which would just loop the error message and the boot screen if I chose anything). I then decided to install windows xp and then ubuntu 11.4 overwritting it which seemed to work, however now whenever the machine boots it gives me the following errors, "error out of disk, error no suitable mode found, error no video mode activated" Can anyone help me with this? Ubuntu will still boot fine I just get those errors and I'm wondering what they are.

---

### Post by oldfred on 2011-06-23
How old is computer and how large was old drive and new drive.

Older computers had a 137GB boot limit and often had smaller drives, so it did not matter. But if you install a larger hard drive then all the boot files have to be in a partition that is inside the 137GB limit. You can then use a separate /boot or just make  / (root) 20GB and keep it inside the 137GB and use the rest of the drive as /home.

What video do you have. Usually it finds an old driver for most old systems. The standard install has something like 30 old video drivers that cover most systems.

---

