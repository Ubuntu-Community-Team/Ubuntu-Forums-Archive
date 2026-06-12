---
title: "question about spin down"
date: 2011-08-12
forum: General Help
---

### Post by Keypel on 2011-08-12
Can I have sdb spin down and sda not?

I was looking at hdparm.conf and I saw

```
#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}
```

So, I did a test, I went System->Preferences->Power Management and made a few changes. Then I went back to the hdparm.conf but I didn't see where any changes were made and everything still looks committed out. Is hdparm.conf even being used?

---

