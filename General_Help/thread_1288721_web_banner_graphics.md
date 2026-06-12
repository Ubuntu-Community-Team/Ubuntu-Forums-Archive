---
title: "web banner graphics?"
date: 2009-10-11
forum: General Help
---

### Post by fcuk112 on 2009-10-11
what's the best tool to use to create a simple web banner graphic in ubuntu?  should i use GIMP?

thanks.

---

### Post by OpenGuard on 2009-10-11
IMO, [Inkscape]("http://www.inkscape.org/") :)

---

### Post by fcuk112 on 2009-10-11
ok when i download and do ./configure i get this:

```

...
checking for INKSCAPE... configure: error: Package requirements (gdkmm-2.4  glibmm-2.4  gtkmm-2.4 >= 2.10.0  gtk+-2.0  libxml-2.0 >= 2.6.11  libxslt >= 1.0.15  cairo  sigc++-2.0 >= 2.0.12    gthread-2.0 >= 2.0 libpng >= 1.2) were not met:

No package 'gdkmm-2.4' found
No package 'glibmm-2.4' found
No package 'gtkmm-2.4' found
No package 'libxslt' found
No package 'sigc++-2.0' found

```

any idea how i can install these dependencies?

---

### Post by wojox on 2009-10-11
Just download it from the repo's. 

I like Gimp personally.

Even has a template for different web banners.

---

### Post by KlinerDraken on 2009-10-11
this command should install the software and any dependencies needed 

sudo apt-get install inkscape

---

### Post by NinjaNumberNine on 2009-10-11
This is my favorite banner maker![[IMG]http://www.bannerfans.com/images/bannerfans.gif[/IMG]]("http://www.bannerfans.com/banner_maker.php")
Totally online and totally free, after you design the banner it lets you download it.
Hope this helps!

BTW be sure to check out the extremely large selection of fonts available.

---

### Post by OpenGuard on 2009-10-11
It would be easier to install it from repositories, tough, it's definitely an older version than if you download from their website.

Anyway, this one should solve your problem:
```
sudo apt-get install gdkmm-2.4 glibmm-2.4 gtkmm-2.4 libxslt sigc++-2.0
```

---

### Post by fcuk112 on 2009-10-11
thanks ninja, exactly something i was looking for... :)

---

### Post by NinjaNumberNine on 2009-10-12
> **fcuk112 said:**
> thanks ninja, exactly something i was looking for... :)
You're welcome. Here's another great site I use to get the banner backgrounds- the blue one on BannerFans is boring;  just use the "upload you own image" option to use one of these after you download it. BTW all of these are free of copyright and meant for public use. Have fun! :)
[URL="http://www.specialweb.com/original/banners1.html"]
The Link[/URL]

NinjaNumberNine


EDIT: Don't overlook that there are several pages of them, almost missed the >  [ 1 ]("http://www.specialweb.com/original/banners1.html") | [ 2 ]("http://www.specialweb.com/original/banners2.html") | [ 3 ]("http://www.specialweb.com/original/banners3.html") | [ 4 ]("http://www.specialweb.com/original/banners4.html") | [ 5 ]("http://www.specialweb.com/original/banners5.html") | [ 6 ]("http://www.specialweb.com/original/banners6.html") | [ 7 ]("http://www.specialweb.com/original/banners7.html") | [ 8 ]("http://www.specialweb.com/original/banners8.html") | [ 9 ]("http://www.specialweb.com/original/banners9.html") | [ 10 ]("http://www.specialweb.com/original/banners10.html") | [ 11 ]("http://www.specialweb.com/original/banners11.html") | [ 12 ]("http://www.specialweb.com/original/banners12.html") | [ 13 ]("http://www.specialweb.com/original/banners13.html") | [ 14 ]("http://www.specialweb.com/original/banners14.html") | [ 15 ]("http://www.specialweb.com/original/banners15.html") | [ 16 ]("http://www.specialweb.com/original/banners16.html") | [ 17 ]("http://www.specialweb.com/original/banners17.html") at the bottom myself.

---

