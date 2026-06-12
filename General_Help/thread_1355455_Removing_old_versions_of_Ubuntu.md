---
title: "Removing old versions of Ubuntu"
date: 2009-12-14
forum: General Help
---

### Post by tom.swartz07 on 2009-12-14
Hi all, 

I've a really simple question. 

When I installed 9.10 on my system, I installed separate from my previous 9.04 installation, so that if something went wrong, or I needed previous files, I could still use the system.

Now that 9.10 is up and golden, what do I need to do to remove the previous partition?

I believe that what I need to do is;
1) livecd- gparted. remove the old partition, and expand into the open space.
2) grub update to update the bootloader.

is that all that is needed? I would rather know what i need to do before I start in at it. haha

Thanks,

---

### Post by Yvan300 on 2009-12-14
Yeah that seems like the most straightforward route. But i think after you resized and delete the partitions, you would have to update fstab. Not sure how to do that but someone could help.

---

### Post by tom.swartz07 on 2009-12-14
> **Yvan300 said:**
>  But i think after you resized and delete the partitions, you would have to update fstab. Not sure how to do that but someone could help.

Any ideas?
Why would you need to update fstab?

---

### Post by Yvan300 on 2009-12-15
I think that it is because each partition is labelled in fstab and if it starts and they are suddenly gone, then heck knows what may happen. Experienced this when i resized my swap partition and it failed to mount. Wait for someone who knows about fstab to explain furthur or you could join #ubuntu-beginners on irc.freenode.net for additional help.

---

### Post by ST3ALTHPSYCH0 on 2009-12-15
You could also just reformat the partition and use it as storage or leave it empty soas to do the same thing when 10.04 comes out.

---

