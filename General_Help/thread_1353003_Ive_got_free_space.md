---
title: "Ive got free space"
date: 2009-12-12
forum: General Help
---

### Post by HomoGleek on 2009-12-12
I have free space on my SSD (I deleted XP :)) and I want too allocate it too Ubuntu, how?

I've got my Minty LiveCD in atm, for GParted. See screenshot for info :)

---

### Post by Ylon on 2009-12-12
> **DarrenTod said:**
> I have free space on my SSD (I deleted XP :)) and I want too allocate it too Ubuntu, how?

I've got my Minty LiveCD in atm, for GParted. See screenshot for info :)

Looks like you had to erase your sda1 and extend backward your sda5. But this option is:
1. Slow
2. Not secure (backup is required)


Also, where's located GRUB? If is on sda1 you had to [recover](https://wiki.ubuntu.com/Grub2) it after.



As other option there's alwasy... global erasing and reinstalling the whole system with just sda1/sda2(swap). Is unpractical but more satisfactory  :popcorn:

---

### Post by HomoGleek on 2009-12-12
> **Ylon said:**
> Looks like you had to erase your sda1 and extend backward your sda5. But this option is:
1. Slow
2. Not secure (backup is required)


Also, where's located GRUB? If is on sda1 you had to [recover](https://wiki.ubuntu.com/Grub2) it after.



As other option there's alwasy... global erasing and reinstalling the whole system with just sda1/sda2(swap). Is unpractical but more satisfactory  :popcorn:
I don't have any backup means, although if I compress my important documents, put them in Ubuntu One then its just a case of reinstalling everything.

If I install another copy of ubuntu on the free space (SDA1), then move any documents, is it easier too:
-Move important files 
-Delete SDA5 (current install)
-Resize SDA1 too fill empty space

---

### Post by SuperSonic4 on 2009-12-12
> **Ylon said:**
> Looks like you had to erase your sda1 and extend backward your sda5. But this option is:
1. Slow
2. Not secure (backup is required) [COLOR="Red"]**SS4: It's always good practice to back up anyway ;)**[/COLOR]


Also, where's located GRUB? If is on sda1 you had to [recover](https://wiki.ubuntu.com/Grub2) it after.



As other option there's alwasy... global erasing and reinstalling the whole system with just sda1/sda2(swap). Is unpractical but more satisfactory  :popcorn:

In concur. Backup any data anyway, preferably to an external source.

A complete re-installation will be easier and let you tweak with partitions. Also you should look into journaling off for an SSD to reduce wear on the drive

edit: 
> If I install another copy of ubuntu on the free space (SDA1), then move any documents, is it easier too:
-Move important files
-Delete SDA5 (current install)
-Resize SDA1 too fill empty space

That seems more like a logical progression than options and would be the method I'd use

---

### Post by HomoGleek on 2009-12-12
> **SuperSonic4 said:**
> In concur. Backup any data anyway, preferably to an external source.

A complete re-installation will be easier and let you tweak with partitions. Also you should look into journaling off for an SSD to reduce wear on the drive

edit: 


That seems more like a logical progression than options and would be the method I'd use

Re-installation it is, found a blank DVD too back up too.

Can you point me too were I can read about joutnaling, google only seems too have info on Mac OSX

Thanks

---

### Post by HomoGleek on 2009-12-28
> **SuperSonic4 said:**
> 
A complete re-installation will be easier and let you tweak with partitions. Also you should look into journaling off for an SSD to reduce wear on the drive


Im still looking for info on the journaling business :D

---

