---
title: "Skipping the authentication when accessing and HDD"
date: 2011-08-07
forum: General Help
---

### Post by Nithogger on 2011-08-07
Hiya folks.

On a laptop I have Windows 7 installed, and ubuntu 11.04. Now. A while ago the HDD died and I replaced it. with some data loss but nothing much to worry. Now I thought that it would be useful if I somehow could manage to direct the Documents, Music etc. etc. folders located /home/[user] to somewhere on a different partition HDD. I managed to make new folders on the partition and link them with the documents and music folders etc..  the problem now is is that you have to unlock it every time by either opening the partition and insert your password. I know that the password problem can be evaded by simply changing some settings, but. I want to evade the whole process of clicking on the partition. It is for security reasons that that have to sort of activate the partition, but I find it becoming a bit annoying. 

So, has anyone a clue of how to activate the driver right at the start? something automatic stuff. Or does someone know how to disable this ?

Cheers.

---

### Post by garvinrick4 on 2011-08-07
sudo gedit /etc/fstab
Add your lines and save.

If you mean to automount use fstab: Here is a ext4 and a ntfs. UUID in sudo blkid.
# /dev/sda7
UUID=0f7c5de9-c3b4-4c50-b288-d34e9ef6e119 /media/home      ext4   defaults    0
# /dev/sda8
UUID=1927A02F2C3A884A /media/data  ntfs-3g defaults,local=en_US.utf8 0 0


##Do not know if that is what you wanted was to automount partitions at boot but here
it is anywhich way.

---

