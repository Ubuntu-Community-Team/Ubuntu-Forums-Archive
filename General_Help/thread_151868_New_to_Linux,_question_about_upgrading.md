---
title: "New to Linux, question about upgrading"
date: 2006-03-28
forum: General Help
---

### Post by AmonSacha on 2006-03-28
So I decided to install ubuntu from some cds that I had and lo and behold, it was hoary instead of breezy. Is there anyway I can upgrade from one to the other without burning the ISO onto a cd (no cd burner available)

Thank you in advance.
Ian

---

### Post by taurus on 2006-03-28
Edit /etc/apt/sources.list and replace the word hoary with breezy in there.  Then upgrade it as
```

sudo gedit /etc/apt/sources.list
(make changes and save it...)
sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by AmonSacha on 2006-03-28
Thank you very much

I would like to compliment the entire ubuntu support board for being one of the best I've ever used

Thanks again
Ian

---

### Post by taurus on 2006-03-28
You're welcome and hope you enjoy your Ubuntu for a long time...  :)

---

