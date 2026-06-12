---
title: "I only boot in Ubuntu"
date: 2009-11-27
forum: General Help
---

### Post by sergio_team on 2009-11-27
Hi, im new in ubuntu i have installed ubuntu 9.10 i have created a partition for the ubuntu, but i can't boot into my windows vista, any idea?

When i see the information of the HDD i see: The sectors are very bad (11 sectors), and i can't boot to my windows vista.


Any idea? Im spanish

---

### Post by oldfred on 2009-11-27
Some early versions of Karmic over reported on Disk errors. You should make sure you have backups of any important data on any partition on your drive. Are the errors from the Ubuntu partition?

I would download smartmontools - lists harddrive detail info
smartctl and smartd. This tells a lot about your drives.

To get windows working the first thing to try is to run:
sudo update-grub

If that does not work we will need a lot more info but lets cross that bridge after your try the update.

---

