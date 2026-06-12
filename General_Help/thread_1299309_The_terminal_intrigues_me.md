---
title: "The terminal intrigues me"
date: 2009-10-23
forum: General Help
---

### Post by Wander_Free_Forever on 2009-10-23
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

To state that obvious, I have been using the terminal, a necessity to fix
problems and compile and reconfigure software. However there is one aspect
that has caught my attention. As a user, regardless of privilege level, I
cannot change directory (‘cd’) to a folder with a space in it. I am
curious as to why that is? An internal system limitation or have I missed
something obvious? An inquiring mind must know.

-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFK4joAzH0f+AFrIBkRCE79AP9d/pqdC2vy4S+KBxe72Uuudw5WtdPwE7FS
Htr3VvnfugEA4dv5H6xNXpAI8TVV1nFcGPmlSMGFrYCn/7pbQe6fNbc=
=UEdY
-----END PGP SIGNATURE-----

---

### Post by iKonaK on 2009-10-23
```
cd /path/to/"fol der"
```or
```
cd "/path/to/fol der"
```...assuming you were referring at this thing :)

---

### Post by sisco311 on 2009-10-23
space is a field separator, you have to quote it:
```
cd "path to dir"
cd path\ to\ dir
```

```
man bash | less --pattern\="QUOTING"
```

---

### Post by iKonaK on 2009-10-23
**Wander_Free_Forever**, you might wanna take a look on "[Put Yourself In Command]("http://en.flossmanuals.net/gnulinux")" ;)

---

### Post by absolutezero1287 on 2009-10-27
Spaces aren't allowed without escape characters or quoting. Personally, I always replace spaces with underscores.

---

### Post by JeSTeR7 on 2009-10-28
I learned about using the slashes by using the tab-complete feature.  Just type the first few characters of the folder and hit tab and it should complete it for you.

---

