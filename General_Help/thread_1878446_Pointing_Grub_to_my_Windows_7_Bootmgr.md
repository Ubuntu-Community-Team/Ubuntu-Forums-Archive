---
title: "Pointing Grub to my Windows 7 Bootmgr"
date: 2011-11-09
forum: General Help
---

### Post by aedmark on 2011-11-09
Hello there.

I did some dumb things with my partitions one night, and for a while I wasn't able to do anything to boot into Windows again. I tried the recovery disk methods, testdisk repairs, the works.

Finally, I downloaded the hiren bootCD and used an option in there that pointed to the bootmgr. This finally worked! I'd like to replicate what it was doing, but in the GRUB bootloader (that successfully points to Ubuntu, at least).

The action used on the BootCD is this:

```
find --set-root --ignore-floppies --ignore-cd /bootmgr
map () (hd0)
map (hd0) ()
map --rehook
find --set-root --ignore-floppies --ignore-cd /bootmgr
chainloader /bootmgr
```

However I'm not sure what syntax that is and I definitely don't know how to translate it into syntax that GRUB understands.

Can anyone shed some light on this?

---

### Post by aedmark on 2011-11-21
No one can help me? If no one has an answer here, perhaps I can kindly be pointed to the right place?

---

### Post by sgage on 2011-11-21
> **aedmark said:**
> Hello there.

I did some dumb things with my partitions one night, and for a while I wasn't able to do anything to boot into Windows again. I tried the recovery disk methods, testdisk repairs, the works.

Finally, I downloaded the hiren bootCD and used an option in there that pointed to the bootmgr. This finally worked! I'd like to replicate what it was doing, but in the GRUB bootloader (that successfully points to Ubuntu, at least).

The action used on the BootCD is this:

```
find --set-root --ignore-floppies --ignore-cd /bootmgr
map () (hd0)
map (hd0) ()
map --rehook
find --set-root --ignore-floppies --ignore-cd /bootmgr
chainloader /bootmgr
```

However I'm not sure what syntax that is and I definitely don't know how to translate it into syntax that GRUB understands.

Can anyone shed some light on this?

I'm not exactly clear about what you want. If a grub menu comes up at boot, but doesn't have a Windows option on it, you can try 

```
sudo update-grub
```

That has always picked up the Win7 loader for me.

An alternative is to reinstall the Win7 MBR, and give it an entry for your Ubuntu. I always use EasyBCD to do this. EasyBCD can also do the Win7 MBR installation.

---

### Post by buckeyered80 on 2011-11-21
Right. I had this issue just recently. As mentioned above, boot into your Ubuntu partition, jump into the terminal and run a sudo update-grub. That will find all of your partitions and update grub.cfg.

---

