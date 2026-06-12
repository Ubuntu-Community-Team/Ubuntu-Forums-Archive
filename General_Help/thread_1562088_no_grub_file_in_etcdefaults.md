---
title: "no grub file in etc/defaults?"
date: 2010-08-27
forum: General Help
---

### Post by The End of The World on 2010-08-27
Hey
Trying to speed up booting with profiling and such, i do:

```
sudo gedit /etc/defaults/grub
```But the file it opens is empty? I searched for it manually and found nothing, either
I should add that i'm dual booting with Windows 7, and have another partition in ntfs format just for my files =]
Thanks,

---

### Post by wojox on 2010-08-27
Try

```
gksudo gedit /etc/default/grub
```

---

### Post by The End of The World on 2010-08-27
Still nothing, WOW at the quick reply, ty but nah it didnt work, it just came up with a blank grub file o.0
Forgot to say, when i do normal sudo gedit etc/default/grub it says:

```
(gedit:2927): GLib-CRITICAL **: g_bookmark_file_load_from_data: assertion `length != 0' failed
```

---

