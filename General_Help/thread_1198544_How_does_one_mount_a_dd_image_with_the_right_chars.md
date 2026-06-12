---
title: "How does one mount a dd image with the right charset?"
date: 2009-06-27
forum: General Help
---

### Post by Redsandro on 2009-06-27
I have a dd image from a European (Dutch) hard drive. Sometimes we like to use characters like äëü, and that's why there's the iso8859-1 character set.

But although the *manpage* for **mount** clearly states that > iocharset=value
	Character set to use for converting between 8 bit characters and
	16 bit Unicode characters. **The default is iso8859-1.**  Long file&#8208;
	names are stored on disk in Unicode format.forcing it by specifying the option or not doesn't matter.

```
mount /media/mega/200812.img /mnt/img -o loop,ro,iocharset=iso8859-1
```

Whenever I encounter a file or folder in nautilus named for example *ideeën.odf* or *für elise remix.it*, they show up like *idee&#65533;n.odf* or *f&#65533;r elise remix.it* making the file or folder uncopyable. (update: in a terminal there's a ? in stead of a &#65533;.)

How do I make this work?

---

### Post by DGortze380 on 2009-06-27
> **Redsandro said:**
> I have a dd image from a European (Dutch) hard drive. Sometimes we like to use characters like äëü, and that's why there's the iso8859-1 character set.

But although the *manpage* for **mount** clearly states that forcing it by specifying the option or not doesn't matter.

```
mount /media/mega/200812.img /mnt/img -o loop,ro,iocharset=iso8859-1
```

Whenever I encounter a file or folder in nautilus named for example *ideeën.odf* or *für elise remix.it*, they show up like *idee&#65533;n.odf* or *f&#65533;r elise remix.it* making the file or folder uncopyable. (update: in a terminal there's a ? in stead of a &#65533;.)

How do I make this work?

I don't think it has anything to do with your mount command. You likely just need to install the fonts on your machine.

---

### Post by Redsandro on 2009-06-27
No I have the fonts. I can type just like that in any application, or here on the forum.

Like I said, the files or folders refuse to copy in nautilus, I get the error message "invalid encoding". In a terminal, it does copy but including the ? characters.

---

### Post by strixx on 2009-10-19
I have the exact same problem when mounting a TrueCrypt volume on a USB drive.

Have any one solved the problem? When i'm mounting normal USB drives Ubuntu mounts it with the correct charset.

---

### Post by Redsandro on 2009-10-19
Unfortunately I still have this problem with dd mounts. Didn't try truecrypt, but if anyone knows a solution, I too am still interested.

---

### Post by strixx on 2009-10-20
I solved my problem by adding the following items to file system options (/o)

```
iocharset=iso8859-1,shortname=mixed,utf8
```So try mounting with that option!! :P It wasn't enough with just iocharset=iso8859-1 as option...

---

### Post by Redsandro on 2009-10-20
Hey thanks! I will try that on the next snapshot mount!

Strange though that a raw image of a drive that mounts correctly doesn't mount the same as the drive itself.

---

