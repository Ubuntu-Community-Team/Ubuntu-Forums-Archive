---
title: "Swap Drive"
date: 2009-11-28
forum: General Help
---

### Post by IamGibby on 2009-11-28
K I was just curious if I really need this Swap drive for Ubuntu to run properly. I have just over 6GB of RAM which really rarely all of it is ever used. I was wondering because I'd like to free up the partition for a home media partition since With W7 and my W7 Recovery partitions Ubuntu and it's swap partition takes up my last 2 available partitions. Thanks anyone.

Chris

---

### Post by NoaHall on 2009-11-28
No, you don't need swap. I have 16 GB of RAM, even when I use it all, swap isn't used.

---

### Post by shaggy999 on 2009-11-28
As long as you don't plan on hibernating you don't need a swap partition.

---

### Post by IamGibby on 2009-11-29
What is the easiest way to delete the Swap Partition? (I know how to add that 3gb worth of space back to my original partition and make a new one for Media from there), just don't know the best way to delete it and stop Ubuntu from wanting it to exist (unless ubuntu doesn't actually look for it)

Thanks

Chris

---

### Post by Sin@Sin-Sacrifice on 2009-11-29
> **NoaHall said:**
> No, you don't need swap. I have 16 GB of RAM, even when I use it all, swap isn't used.

You use 16 GB RAM??? I have a hard time using 4...

[QUOTE=IamGibby]
What is the easiest way to delete the Swap Partition? (I know how to add that 3gb worth of space back to my original partition and make a new one for Media from there), just don't know the best way to delete it and stop Ubuntu from wanting it to exist (unless ubuntu doesn't actually look for it)

Thanks

Chris[/QUOTE]

You can delete it using gparted. Not sure but I think you may need to do it with a live cd.

---

### Post by garvinrick4 on 2009-11-29
I understand it was a valuable when cpu's had 250 meg of ram
or so and it needed the virtual memory to get on with its self.
Now with huge amounts of ram it is kind of just habit for people
to have a swap partition. They still say in older articles to double the size of your ram for the partition. You would have a
32 gig swap for virtual memory. Could be an overkill.

---

### Post by NoaHall on 2009-11-29
After deleting it, you may need to edit fstab and remove the line which mounts it.

---

### Post by hexanol on 2009-11-29
If you want to delete your swap partition, first swap off your swap partition with the "swapoff" command. You'll then be able to do whatever you want with the partition. And then, don't forget to edit /etc/fstab as to remove the line which is "mounting" your swap partition.

So, if your swap partition is "/dev/sda5", you'll have to (as root)
[LIST]
[*]swapoff /dev/sda5
[*]sed -i -e '/swap/d' /etc/fstab
[*]Do whatever you want with the left swap partition
[/LIST]

The sed command remove all lines with the 'swap' word in the file /etc/fstab, and it's normally safe to use.

Also, you can use a file on a standard filesystem as a 'swap'. This is slower than using a swap partition, but you don't need to have a separate partition this way.

---

