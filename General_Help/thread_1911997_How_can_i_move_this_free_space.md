---
title: "How can i move this free space?"
date: 2012-01-19
forum: General Help
---

### Post by Educ on 2012-01-19
Hello.
First of all an image to guide: [http://img849.imageshack.us/img849/9969/particiones.jpg](http://img849.imageshack.us/img849/9969/particiones.jpg)

Well my idea is to add those 5.05 Gb in the partition "sda6" which has 3.89 Gb (Ubuntu was installed there)

The problem is that I can't do it directly, according to what I understand I have to "move" that free space.

My idea: I booted with Ubuntu LiveCd and open GParted, with all the partitions unmounted, I tried to put all in the swap because then I wanted to reduce swap so i could have the free space above. But here comes other problem, I couldn't modify the swap partition. (I'm not allowed)

I don't know why but that free space I can add it in the partition "sda3"

Some idea to solve the problem and increase "sda6"? I don't want to reinstall :P
Is there any risk to do this kind of things? I mean resize / move partition.


Thanks and sorry for my english, it's a bit rusty jaja.

---

### Post by Bobhuber on 2012-01-19
You should be able to delete the swap partition (sda7) making it unallocated along with what is already there , expand sda6 leaving enough left over to recreate sda7 as swap after you are done with sda6.
I would highly suggest you back up any important data first.

---

### Post by Educ on 2012-01-19
Thanks [Bobhuber]("http://ubuntuforums.org/member.php?u=945841"), I thought that but here comes my question: Why doing that would allow me to expand sda6? For example now I can't expand the swap, I don't have that option.

---

### Post by grahammechanical on 2012-01-19
You cannot move, resize the swap partition while it is active. You need to set it from swap on to swap off.

May I suggest that you move sda3 to the right that will move the 2.9Mib unallocated space to the left of sda3.

Then move the swap partition to the right so that all the unallocated space is now on the left of the swap partition.

Finally, re-size sda6 to take up all the unallocated space.

But do this one operation at a time. This site has some pictures about swap on - swap off

[http://techie-buzz.com/foss/ubuntu-enable-disable-swap-partition.html]("http://techie-buzz.com/foss/ubuntu-enable-disable-swap-partition.html")

Regards.

---

### Post by xyzzyman on 2012-01-19
I don't think grammarmechanical noticed but you can't expand or move the swap as it's outside of sda2, which is the extended partition. Gparted visualizes it for you up above (The light blue surrounds sda5,6,7). You can expand sda2, move or delete sda7, and then resize sda6.

Moving sda3 is going to take an extremely long time as it's going to rewrite all 183GB's over just 2.5MB's. PITA. And once it's started you can't stop it. If that 2.5MB's at the end bothers you then just resize sd3 to overtake it.

My recommendation is:

1.) Backup anything important on ANY partition. 
2.) Expand sda2 to fill in the 5.50GB gap. Apply. (You may have to click on sda7 and 'swap off')
3.) Move sda7 to the far right of sda2 or delete and recreate a new swap partition. As it's so small I'd probably just move it so that way you don't have to edit your fstab file with the new UUID. Apply.
4.) Resize sda6. This shouldn't take too long as you're not moving it backwards at all, just adding blank space at the end. Apply.
5.) Reboot

---

### Post by Educ on 2012-01-20
Thanks!!! I did what [xyzzyman]("http://ubuntuforums.org/member.php?u=44719") said and problem solved :)

---

