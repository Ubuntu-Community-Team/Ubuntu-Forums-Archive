---
title: "partition help?"
date: 2009-09-13
forum: General Help
---

### Post by loosie on 2009-09-13
Hi,

I installed Ubuntu on this machine, side by side with Windows after Windows crashed & refused to boot up. Was advised to keep Windows for the time being. But I found that Win was taking up so much disk space, there was little room for Ubuntu & it wasn't working well. So I ditched Windows. 

But Ubuntu was still in a small partition. Couldn't work out how to change that & since it was very new, no settings to lose, I just reinstalled Ubuntu into the big Windows partition. So Ubuntu is generally working well now, but I have one unnecessary copy on the machine, taking up space. I also have 3 'swap' partitions. In Partition Editor I can't add anything to the big Ubuntu partition, even from 'empty' sections, can't delete the other sections...

Can someone tell me how to change all this, to clean it all up, make it run the best it can?

---

### Post by rob-ward on 2009-09-13
You should be able to resize your partitions by using a ubuntu live cd and then using gparted. However you need to be careful which ones you move/lose, at least on of your swap partitions will be in use so you will need to keep or recreate one of them.

Before you resize your drive make sure you backup and data you want as thinks can go wrong, the load up ubuntu and paste the output of the following commands

mount

sudo fdisk -l

cat /etc/fstab

if you paste the output of them 3 commands here we should be able to tell you which partitions you can remove or you need to keep/recreate.

---

