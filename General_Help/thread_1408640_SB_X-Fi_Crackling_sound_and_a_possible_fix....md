---
title: "SB X-Fi Crackling sound and a possible fix?..."
date: 2010-02-16
forum: General Help
---

### Post by jblaven on 2010-02-16
I read that I could do the following:

You probably have a HDA audio card. If so then those clicks is caused by the power saving option introduced in karmic. You can solve this problem by commenting out the last line in the /etc/modprobe.d/alsa-base.conf

Problem is, I was going to do it from the gui and it said I didn't have permission to edit that file.  How do I get permission to save the change?

Thanks,

Joe

---

### Post by Greenwidth on 2010-02-16
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

---

