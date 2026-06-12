---
title: "Problem with burg after adding a new graphics card"
date: 2011-01-07
forum: General Help
---

### Post by greyradio on 2011-01-07
I installed burg on 10.10 and it worked perfectly until I upgraded from a Nvidia 8800 GT  to an Nvidia GTX 470 recently. I noticed that burg will no longer show resolutions higher than 1280 x 1024. I tried adding ```

GRUB_GFXMODE=1680x1050
GRUB_GFXPAYLOAD_LINUX=1680x1050
```to the configuration file hoping that it would manually set the resolution but it didn't work. I was hoping someone could help me resolve this problem. Thanks.

---

### Post by dcstar on 2011-01-08
> **greyradio said:**
> I installed burg on 10.10 and it worked perfectly until I upgraded from a Nvidia 8800 GT  to an Nvidia GTX 470 recently. I noticed that burg will no longer show resolutions higher than 1280 x 1024. I tried adding ```

GRUB_GFXMODE=1680x1050
GRUB_GFXPAYLOAD_LINUX=1680x1050
```


Those resolutions **must** be VESA resolutions supported by your video card, not graphics resolutions that are only available when the OS boots.

Also: [http://www.sourceslist.eu/blog/linux-blog/burg-manager-installing-and-configuring-burg-has-never-been-so-easy/](http://www.sourceslist.eu/blog/linux-blog/burg-manager-installing-and-configuring-burg-has-never-been-so-easy/)

---

### Post by greyradio on 2011-01-09
Thanks. I guess I have to stick with the lower resolutions.

---

