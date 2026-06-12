---
title: "gqview not geeqie"
date: 2010-12-14
forum: General Help
---

### Post by RichLouth on 2010-12-14
I've installed gqview 2.0.4-5 using an old deb file.

[http:://archive.ubuntu.com/ubuntu/pool/universe/g/gqview/gqview_2.0.4-5_amd64.deb]("http:://archive.ubuntu.com/ubuntu/pool/universe/g/gqview/gqview_2.0.4-5_amd64.deb")

It worked ok but the remote command doesn't work. e.g.

gqview -r file:"filename.jpg"

The window opens and then immediately closes. There is no error output from the command line. I had no issue with this in 9.04.

p.s.

I don't want to use geeqie because it is very slow loading a folder with 100's of files. Presumably preloading all of the images in a folder before displaying the one I've requested. I want the image I've requested to load quickly which geeqie is apparently incapable of.

If anyone has any suggestions for another image viewer that allows remote opening of file quickly that'd be great.

Thanks

---

### Post by TeoBigusGeekus on 2010-12-14
I use Mirage which is quite lightweight and it also loads the thumbnails of a folder full of images in a reasonable time.
For something ultra light, I recommend feh, which I use in extreme situations (HUGE number of pics).

---

### Post by RichLouth on 2010-12-14
Thanks for the suggestions TeoBigusGeekus,

Neither Mirage or feh seem to support remote opening like gqview and geeqie do though. i.e. opening an image in an already open window so there's only one instance of the window.

There's a new option in Geeqie I hadn't noticed:

General > Image loading and caching > Decoded image cache size

Setting this to zero seems to speed things up enough for me.

---

