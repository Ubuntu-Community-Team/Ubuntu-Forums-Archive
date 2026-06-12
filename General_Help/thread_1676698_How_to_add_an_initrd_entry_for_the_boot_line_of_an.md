---
title: "How to add an initrd entry for the boot line of another Linux"
date: 2011-01-27
forum: General Help
---

### Post by bobnutfield on 2011-01-27
Hello Everyone,

I have long been avoiding Grub2, but it got installed without my permission when I upgraded to Maverick.  I was using the legacy Grub from Fedora and was quite happy, but after partitioning Ubuntu did not give me the choice of not installing Grub2.

Anyway, I can live with it if I can learn it well enough to edit it as easily as I did legacy grub. My problem is that although Fedora boots fine,  grub did not add the initrd entry to boot the Slackware kernel Which of course it requires.)

I edited /boot/grub/grub.cfg and manually added, but as soon as I ran "update-grub" it removed it again.

Does anyone know how to permenently add this line to the kernel line in Grub2 for Slackware.

Any help appreciated.

Bob

---

### Post by towheedm on 2011-01-27
Actually, grub.cfg is created by update-grub.  It is not recommended to directly edit this file.  However if you do, do not run update-grub.

If you manually edit this file, any grub updates will overwrite your changes.

To maually add a menu entry, edit the [COLOR=Blue]/etc/grub.d/40_custom[/COLOR] and add it there.  Then run
```

sudo update-grub
```

---

### Post by coffeecat on 2011-01-27
> **towheedm said:**
> To maually add a menu entry, edit the [COLOR=Blue]/etc/grub.d/40_custom[/COLOR] and add it there.  Then run
```

sudo update-grub
```

You also need to make 40_custom executable otherwise update-grub will ignore it.

---

### Post by towheedm on 2011-01-27
> **coffeecat said:**
> You also need to make 40_custom executable otherwise update-grub will ignore it.

It's executable by default on my system (Karmic) using 1.98-1ubuntu6.

---

### Post by coffeecat on 2011-01-27
> **towheedm said:**
> It's executable by default on my system (Karmic) using 1.98-1ubuntu6.

Yes, you're quite right. I've just checked in Natty and 40_custom is executable by default in Natty too.

I was remembering some of the early instructions for grub2 where you were told to make 40_custom executable if you wanted update-grub to take notice of it. Either the instructions were superfluous or there was some fine-tuning of the default settings during the development stage of Karmic when grub2 was still new.

---

### Post by towheedm on 2011-01-27
Yes, that's correct.  Also, the highest version of grub in the Karmic repos is 1.97~Beta4.  I installed 1.98-1ubuntu6 from the Lucid repos.  This was so that I could customize grub using the gfxmenu.

My next upgrade will be 1-ubuntu9.  From there it's on to Maverick grub releases once the gfxmenu still works fine.

---

