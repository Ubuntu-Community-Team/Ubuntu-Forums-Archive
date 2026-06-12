---
title: "weird extension in mounted iso"
date: 2009-11-18
forum: General Help
---

### Post by rahilm on 2009-11-18
Hi..I have ubuntu 9.04 installed. I have a very weird problem. All iso files i mount , there appears ;1 extension after every file.

Is there any way to correct this??

---

### Post by Giblet5 on 2009-11-18
That's a file version indicator. The latest file can be opened by referencing its name w/o the trailing semicolon and version.

Lots of systems support file versions. It's a great way to save computer systems from their users.

---

### Post by rahilm on 2009-11-18
but i can't watch dvds because of it. plus all game cd's have it, so i can't installed from the iso, i have to extract it or burn it

---

### Post by Giblet5 on 2009-11-18
How are you mounting the iso's?

---

### Post by rahilm on 2009-11-18
> **Giblet5 said:**
> How are you mounting the iso's?

archive mounter
but
sudo mount -o loop ...
gives the same result

---

### Post by Giblet5 on 2009-11-18
There's a simpler way.

```
sudo apt-get install gmountiso
```

It's tiny python applet that shows up in Applications -> System -> Gmountiso

If that yields the same versioning info on your iso, then that iso was probably created on an OpenVMS box and you'll just have to get a working iso image (one that wasn't created on a system that insists on plugging version info on its files).

I just did a sudo mount -o loop on three CD and one DVD images. No versioning info.

---

### Post by rahilm on 2009-11-19
yes
it seems to be working. a bad iso i think. archive  mounter does not mount properly but it does not mount as root which makes handling it easier

---

