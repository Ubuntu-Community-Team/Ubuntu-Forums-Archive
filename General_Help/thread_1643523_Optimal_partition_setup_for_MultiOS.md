---
title: "Optimal partition setup for MultiOS"
date: 2010-12-12
forum: General Help
---

### Post by FreezWay on 2010-12-12
Ok, I'm thinking about installing Arch soon, but I was wondering what the optimal partition setup would be. Bhalash on #ubuntu recomended:

boot as sda1
swap as sda2
personal data (not config) as sda3 **
the extended partition as sda4 which would include
-Ubuntu
-Arch

** This would not be a home folder, it would just be for person files like pictures or music. The OS's would have their own /home which would contain symlinks to this partition.

Does anyone see anything wrong with this setup or have a better idea?

Currently on my setup:
sda1 is a broken ubuntu 10.10
sda2 is extended
sda5 is swap for broken install
sda6 is my working install
sda7 is swap for working install

So keep in mind how easy it would be to move the partitions around in your response. I haven't found a way to move something out of extended without frying the data.

---

### Post by DeMus on 2010-12-12
I would use SDA3 as home partition so you have all your data in one partition. Easy when you need to re-install.
Using your way you will have /home as part of /, and other data like pictures and music separately. It makes it harder to re-install.

---

### Post by FreezWay on 2010-12-12
The problem I see with that is that I'd have to have a separate /home partition for each OS, because they all want to write there .XXXX files there.

---

