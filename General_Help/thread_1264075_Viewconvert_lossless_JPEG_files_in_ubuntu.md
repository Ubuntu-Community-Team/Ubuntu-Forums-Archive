---
title: "View/convert lossless JPEG files in ubuntu"
date: 2009-09-11
forum: General Help
---

### Post by arkticcool on 2009-09-11
I cannot seem to view lossless jpeg files under ubuntu, and I cannot convert them to a more opensource friendly format with image magick.

Does anyone know how I would be able to view/convert lossless JPEG files under ubuntu?

When I open the files, image viewer states the following:

```

Could not load image 'Page 000 0.jpg'.
Error interpreting JPEG image file
(Unsupported JPEG process: SOF type 0xc3)

```

And when I try to convert from the command line I get this:
```
home@home-desktop:~/Lossless$ convert *.jpg *.png
convert: Unsupported JPEG process: SOF type 0xc3 `Page 000 0.jpg' @ coders/jpeg.c/EmitMessage/231.

```

---

### Post by StuartN on 2009-09-11
Apparently Gimp can read a JPEG2000 file, but will write it as a JPEG. DigiKam can read and write back as JPEG2000. ImageMagick claims to both read and write, but is reported to write a JPEG. I guess there are patent issues that limit the use of JPEG2000, especially when writing.

So you can view and convert with Gimp or DigiKam.

Edit: Gimp via plugin [http://registry.gimp.org/node/9899](http://registry.gimp.org/node/9899)

---

### Post by arkticcool on 2009-09-13
I cannot get the gimp plugin to compile, and I can neither get digicam to install, it stops with the following error message:
```

Could not mark all packages for installation or upgrade
The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.
digikam:
 Depends: libqt4-sql-sqlite but it is not going to be installed

```

Checked my repo's they are, multiverse, and all others are enabled.

 Digikam has on-the-fly jpeg 2000 support according to its makers ([http://www.digikam.org/drupal/node/362]("http://www.digikam.org/drupal/node/362")), so I assume it works, to be confirmed if someone knows how to resolve this dependency error?

---

