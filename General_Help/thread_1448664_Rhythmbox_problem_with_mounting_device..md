---
title: "Rhythmbox problem with mounting device."
date: 2010-04-06
forum: General Help
---

### Post by maghoxfr on 2010-04-06
Recently I've resized my partitions with Gparted, since then every time I start session and open Rhythmbox I have to go to preferences and tell again to the program where is the folder with my music. 

The thing is that I store my music on a different partition than the one I have Ubuntu installed on. When I click on it to tell rhythmbox where the folder is the following notification pops up:
"Authentication is recquired to mount the device" and of course I have to write my password.

It's not really a problem but it's a bit annoying having to do that procedure everytime I turn on the pc.

Thanks

---

### Post by duanedesign on 2010-04-06
Add your new partition to your /etc/fstab so that it is mounted at boot.

There is a nice [page on the wiki]("https://help.ubuntu.com/community/Fstab") about adding fstab entries.

If you have any questions please post them and I, or someone else, will be more than happy to help with that.

best of luck,
duanedesign

---

### Post by maghoxfr on 2010-04-07
Thanks, I followed the link you gave me and under the section of [Automatically mount partitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") found out about [Pysdm]("http://pysdm.sourceforge.net/"). So far I'm doing well.

Beautiful community, thank you very much.

---

