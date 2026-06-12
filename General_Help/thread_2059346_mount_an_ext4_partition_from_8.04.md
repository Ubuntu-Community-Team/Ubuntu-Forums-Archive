---
title: "mount an ext4 partition from 8.04?"
date: 2012-09-17
forum: General Help
---

### Post by rawlins02 on 2012-09-17
I'm trying to mount an ext4 partition on my drive while booted into Hardy Heron 8.04. Need that version on occasion because of issues with my old video card.  I'm getting unknown filesystem type while trying to mount partition. Tried:

```

~> sudo tune2fs -E test_fs /dev/sda5
tune2fs 1.40.8 (13-Mar-2008)
Setting test filesystem flag

```

but then got

```

~> sudo mount -t ext4 /dev/sda5 /mnt/temp
mount: unknown filesystem type 'ext4'

```

Any chance this can be done?

---

### Post by LewisTM on 2012-09-17
Ubuntu 8.04 did not support ext4, only ext3. You will need a more recent version (at least 9.04) or a patched version with a recent kernel and fstools.

Cheers!

---

### Post by rawlins02 on 2012-09-17
That's what I thought. Oh well...

---

