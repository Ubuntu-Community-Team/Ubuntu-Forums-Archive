---
title: "Partitioning Help"
date: 2011-06-04
forum: General Help
---

### Post by paaitken on 2011-06-04
Here’s the situation.


[IMG]https://lh5.googleusercontent.com/-w3RKK3hxXWI/Tem8Bpy9CEI/AAAAAAAAAm8/x5nVBNyGnVg/s640/Screenshot--dev-sda%252520-%252520GParted.png[/IMG]

 

 The Windows installation on sda1 won't boot. There is an entry in Grub, but when I select it, I either get a blinking cursor on a blank screen, or it loops back to the OS selection screen. Ubuntu 11.04 boots fine.
 

 Since 11.04 is working just perfectly on my Thinkpad X61, I’m done with Windows. I’d like to do the following:
  
[LIST=1]
[*]Format sda1, deleting everything 	on it.  	
[*]Place my existing configured 	ubuntu installation on the first partition in the disk, making it 	around 12GB.
[*]Resize the swap to around 4GB.
[*]Fill the remaining space with 	sda2, the “Data” partition
 	
[/LIST]
 Eessentially, I’d like a ~12GB ext4 ubuntu partition, a ~210GB ntfs data partition, and a ~4GB swap partition.
 

 What would be the best way to achieve this?
 

 Thanks in advance!

---

