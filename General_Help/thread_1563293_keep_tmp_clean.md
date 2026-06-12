---
title: "keep tmp clean"
date: 2010-08-28
forum: General Help
---

### Post by ToranK on 2010-08-28
I have used SUse some time now, and I return now to Ubuntu.
In Yast cron jobs can be edited easily in order to keep the tmp-partition clean.
I would like to do the same in ubuntu, as I know a full tmp partition prevents the system from booting.

So, how to do it? I have tmpreaper installed, but this soft is not as handy as Yast.
Tmpreaper.conf can indeed be edited, but I have no idea how.
It is always "read only".

Can Midnight Commander bring solution here?

---

### Post by minigeek on 2010-08-28
> **ToranK said:**
> I have used SUse some time now, and I return now to Ubuntu.
In Yast cron jobs can be edited easily in order to keep the tmp-partition clean.
I would like to do the same in ubuntu, as I know a full tmp partition prevents the system from booting.

So, how to do it? I have tmpreaper installed, but this soft is not as handy as Yast.
Tmpreaper.conf can indeed be edited, but I have no idea how.
It is always "read only".

Can Midnight Commander bring solution here?

Hi

To edit the tmpreaper.conf do the following

```
sudo cp -v tmpreaper.conf orig.tmpreaper.conf
sudo vi tmpreaper.conf
```

This will allow you to edit the file.
:P

---

