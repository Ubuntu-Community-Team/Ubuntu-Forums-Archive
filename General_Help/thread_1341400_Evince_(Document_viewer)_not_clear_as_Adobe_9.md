---
title: "Evince (Document viewer) not clear as Adobe 9"
date: 2009-11-29
forum: General Help
---

### Post by donniezazen on 2009-11-29
Hi Guys,

As the title says the same pdf file is more clearer in Adobe 9 then in Evince. I really like simple and sleek Evince. Is their any way i can make Evince more clearer?

I am posting two pictures to show what i mean.

Thanks,
SK.

---

### Post by XCan on 2009-11-30
It would indeed be interesting to find a solution for this. But it seems to be tied with evince's rendering engine. Other pdf readers, such as okular seems to render stuff on par with Adobe Reader.

---

### Post by hugmenot on 2009-11-30
It&#8217;s not the same zoom level.

What type of bitmap did you scan this in? Is it bilevel monochrome or grayscale?

The best thing would be to report this at the Poppler mailing list, because subsampling of images is done by Poppler and Cairo. They rely on people reporting problematic files.

---

### Post by donniezazen on 2009-12-01
> **XCan said:**
> It would indeed be interesting to find a solution for this. But it seems to be tied with evince's rendering engine. Other pdf readers, such as okular seems to render stuff on par with Adobe Reader.

Thanks Okular works great. I don't really like KDE apps but it's really fast.

> **hugmenot said:**
> It’s not the same zoom level.

What type of bitmap did you scan this in? Is it bilevel monochrome or grayscale?

The best thing would be to report this at the Poppler mailing list, because subsampling of images is done by Poppler and Cairo. They rely on people reporting problematic files.

Thanks, Yeah it may be different zoom level but you really can't see anything on any zoom level. I am not really sure type of bitmap scan it is.

---

### Post by hugmenot on 2009-12-01
I think this is your bug:
[https://bugs.freedesktop.org/show_bug.cgi?id=5589](https://bugs.freedesktop.org/show_bug.cgi?id=5589)

It&#8217;s really old, but apparently it is being worked on. Okular is not affected because it doesn&#8217;t use Cairo.

---

### Post by donniezazen on 2009-12-01
> **hugmenot said:**
> I think this is your bug:
[https://bugs.freedesktop.org/show_bug.cgi?id=5589](https://bugs.freedesktop.org/show_bug.cgi?id=5589)

It’s really old, but apparently it is being worked on. Okular is not affected because it doesn’t use Cairo.

Okular works for me; specially when i am scrolling a large document i do not have to wait for it to load.

Thanks.

---

