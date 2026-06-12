---
title: "Gparted help needed"
date: 2012-03-02
forum: General Help
---

### Post by olwe on 2012-03-02
I just did a clone from a smaller disk to a larger. Some 90 gb remain unallocated after the clone. Below is a screenshot:

[IMG]http://hercynia.net/images/Screenshot.png[/IMG]

I tried to follow some instructions, but I'm afraid it didn't take. Now I've got something called "extended" AND unallocated both at 90 gb. What I want is to simply expand the linux partition out to take up the 90 gb of unallocated.

---

### Post by critin on 2012-03-02
You can delete the extended partition then resize partition 1 to fill the whole disk.
Don't forget to run    sudo update-grub  afterwards.
I've done mine and had no problems.

You may have to unswap the swap partition, then reset it again when finished.  It will alert you if it's necessary.

---

### Post by olwe on 2012-03-03
Gparted gives no specific "delete" opportunity, only "manage flags". I can "swapoff" /dev/sda5 linux-swap, then /dev/sda2 extended can be "resize/move"-ed. Please advise. . .

---

### Post by critin on 2012-03-03
> **olwe said:**
> Gparted gives no specific "delete" opportunity, only "manage flags". I can "swapoff" /dev/sda5 linux-swap, then /dev/sda2 extended can be "resize/move"-ed. Please advise. . .

You can't resize sda/1 while you're using the disk, (mounted) use the live CD or flash.  Gparted should then let you delete the extended and resize sda/1 to fit whole drive.

You're working with a clone and I don't know if there are special requirements in resizing those.  I've not tried it with a clone.

You can install another version of linux into the unallocated for fun and experience if you felt like it.  It's good practice.  lol

---

