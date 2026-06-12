---
title: "HOW to patch my kernel"
date: 2012-08-26
forum: General Help
---

### Post by SuperMiguel on 2012-08-26
Hey guys i need to run do this: [https://bugs.freedesktop.org/show_bug.cgi?id=41265](https://bugs.freedesktop.org/show_bug.cgi?id=41265) 

Basically just trying to patch my kernel.

I made a copy of my kernel /usr/src/linux-source-3.2.0, name the copy miguel-kernel..

Then i cd into miguel-kernel and ran this command:

```
sudo patch -p1 < /home/miguel/Downloads/0001-drm-radeon-implement-ACPI-VFCT-vbios-fetch-v3.patch
```

result:
```
patching file drivers/gpu/drm/radeon/radeon_bios.c
```

Then i ran:
```
sudo patch -p1 < /home/miguel/Downloads/Kernel\ Patch/0002-drm-radeon-split-ATRM-support-out-from-the-ATPX-hand.patch 
```

Result:
```
patching file drivers/gpu/drm/radeon/radeon.h
Hunk #1 succeeded at 123 with fuzz 1 (offset -19 lines).
patching file drivers/gpu/drm/radeon/radeon_atpx_handler.c
Hunk #1 FAILED at 30.
Hunk #2 succeeded at 197 (offset -1 lines).
Hunk #3 succeeded at 208 (offset -1 lines).
1 out of 3 hunks FAILED -- saving rejects to file drivers/gpu/drm/radeon/radeon_atpx_handler.c.rej
patching file drivers/gpu/drm/radeon/radeon_bios.c
Hunk #1 succeeded at 98 (offset -1 lines).
Hunk #2 FAILED at 183.
Hunk #3 succeeded at 195 (offset -1 lines).
1 out of 3 hunks FAILED -- saving rejects to file drivers/gpu/drm/radeon/radeon_bios.c.rej
```


Any idea on what i need to do??

---

### Post by Doug S on 2012-08-26
Someone else might know better, but I seem to always have to resort to applying the patch manually. I suggest that you always save the original file first. You shouldn't have to actually re-type everything, just copy and paste it from the patch diff listings, then delete the "+" sign and the space. It is tedious.

---

### Post by Rexilion on 2012-08-27
You use kernel 3.2 to patch.

However, the last patch you mentioned (also [here]("http://cgit.freedesktop.org/~agd5f/linux/patch/?id=6c0775d89cf6a39f4d155c8ad53067a0768e31e0")) is based on 3.6-rc1 (look [here]("http://cgit.freedesktop.org/~agd5f/linux/log/?h=acpi_patches&ofs=50")). So in the meantime, between 3.2 and 3.6-rc1 *a lot* changes. 

Especially in gpu/drm/gem (everything with video cards). Since Linux is finally playing catch up with video drivers.

You have to use a 3.6-rc1 kernel (at least!, any rc higher will probably do to). To apply this specific patch.

---

### Post by Doug S on 2012-08-27
I didn't look into the changes between 3.2 and 3.6 for this case. Often it isn't too difficult to figure out how to backwards apply the patch manually. If the changes are major, as Rexilion says, then yes it might just be too difficult to figure out how to backport the changes.

---

### Post by Rexilion on 2012-08-27
> **Doug S said:**
> I didn't look into the changes between 3.2 and 3.6 for this case. Often it isn't too difficult to figure out how to backwards apply the patch manually. If the changes are major, as Rexilion says, then yes it might just be too difficult to figure out how to backport the changes.

Completely true, but I think the best/safest/efficiënt/logical way is to upgrade to 3.6-rc1 (or higher :)). Unless you have a very good (technical) reason not to do so.

---

