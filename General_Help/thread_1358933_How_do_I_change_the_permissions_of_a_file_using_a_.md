---
title: "How do I change the permissions of a file using a terminal?"
date: 2009-12-19
forum: General Help
---

### Post by Kevlamin on 2009-12-19
Hi im using ubuntu on my Toshiba TE2100 (laptop) and i need to change the permissions on the file /etc/X11/xorg.conf so i can disable my nvidia graphics card, so that xwindows doesn't crash every time it loads. Help would be appreciated

---

### Post by BenAshton24 on 2009-12-19
Don't change the permissions! Use sudo...

```
sudo nano /etc/X11/xorg.conf
```

If you really want to know about permissions then you want to be using chmod & chown, you can google or look at the man pages:

```
man chmod
man chown
```

Hope this helps
Ben.

---

### Post by Ordes on 2009-12-19
i wouldnt do that... try with sudo first and change the settings...

not so sure about your tech level... but u want to change sth system wide.. and dont know the chown chmod command? i suggest u try other methods first....

anyways, if u wanna go for it...

sudo chown -R user:user [folder]   (-R is for recursive, dont need that for a file)
sudo chmod -R XYZ [folder]

XYZ
User, Group, Others,

-read 4
-write 2
-execute 1

e,g 644, rw / r / r

---

