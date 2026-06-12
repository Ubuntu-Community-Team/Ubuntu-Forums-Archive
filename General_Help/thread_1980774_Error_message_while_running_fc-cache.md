---
title: "Error message while running fc-cache"
date: 2012-05-15
forum: General Help
---

### Post by Senior_Buckethead on 2012-05-15
Hi All
I had installed some fonts and ran fc-cache:

```

glenn@acer:/usr/share/fonts$ sudo fc-cache -fv
/usr/share/fonts: caching, new cache contents: 0 fonts, 6 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 4 dirs
....

/home/glenn/.fonts: caching, new cache contents: 0 fonts, 1 dirs
/home/glenn/.fonts/Library: caching, new cache contents: 0 fonts, 0 dirs
/var/cache/fontconfig: cleaning cache directory
/home/glenn/.fontconfig: cleaning cache directory
/home/glenn/.fontconfig: invalid cache file: 7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
/home/glenn/.fontconfig: invalid cache file: d69c7f22caf0697490c4d47e6ef04d17-le32d4.cache-3
fc-cache: succeeded
glenn@acer:/usr/share/fonts

```

Can someone please tell my why fc-cache threw up the error message at the end of its process?

---

### Post by Senior_Buckethead on 2012-05-17
Bump...

---

