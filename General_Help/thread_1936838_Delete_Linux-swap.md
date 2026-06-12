---
title: "Delete Linux-swap"
date: 2012-03-06
forum: General Help
---

### Post by j814wong on 2012-03-06
I have two hard drives on my computer and I want to clear both of them.  However, on both of them, I can't delete the Linux-swap on each.  

I'm formatting both of them to make way for Ubuntu 12.04 beta and using one of teh other HDDs as a extra storage drive eventually.

Here is an image of m y situation where there is a key on the left of the linux-swap word

---

### Post by winh8r on 2012-03-06
You should be aware that running the beta version as your main OS is not recommended. Wait until the official release in April to ensure that all bugs and issues have been addressed before relying on 12.04 as your only Operating System.

As far as deleting the swap partition goes, you will not have to worry about it as the installer on the 12,04 live cd will allow you to select "erase and use entire device" which will erase everything on the drive and re-format it with the necessary partitions for a full clean install of 12.04.

Hope this helps you.

---

### Post by lindsay7 on 2012-03-06
using Gparted. look under partition in the menu and click on "swap Off", you should be able to delete that partition after that.

---

### Post by j814wong on 2012-03-06
> **winh8r said:**
> You should be aware that running the beta version as your main OS is not recommended. Wait until the official release in April to ensure that all bugs and issues have been addressed before relying on 12.04 as your only Operating System.

As far as deleting the swap partition goes, you will not have to worry about it as the installer on the 12,04 live cd will allow you to select "erase and use entire device" which will erase everything on the drive and re-format it with the necessary partitions for a full clean install of 12.04.

Hope this helps you.
I know its not recommended but I really don't mind all too much.  

I know the installer can erase the entire drive but I ahve two drives that both have Linux-swaps.  One was for Linux Mint 12 and the other was for Oneiric

---

### Post by j814wong on 2012-03-06
> **lindsay7 said:**
> using Gparted. look under partition in the menu and click on "swap Off", you should be able to delete that partition after that.
Thanks it worked =)

---

