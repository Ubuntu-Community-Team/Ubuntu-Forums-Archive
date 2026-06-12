---
title: "Reset to default font rendering?"
date: 2012-04-10
forum: General Help
---

### Post by Mokura on 2012-04-10
Like the topic says.  I compiled/installed a freetype font patch from Infinality ([http://www.infinality.net/blog/infinality-freetype-patches/](http://www.infinality.net/blog/infinality-freetype-patches/)) using these directions ([http://www.infinality.net/forum/viewtopic.php?f=2&t=77#p794](http://www.infinality.net/forum/viewtopic.php?f=2&t=77#p794)) and after a good deal of tinkering around with the overrides myself, I'd like to get back to the default freetype rendering method, if that's possible.  (I was just using the font configuration file from the Fonts page on the wiki, and I was okay with that.)  Any help on this would be appreciated.

---

### Post by kiirokurisu on 2012-04-10
You could start by reinstalling all the packages that you replaced during experimenting, e.g.

```
sudo apt-get --reinstall install fontconfig-config
```

I'm guessing you will also need to reinstall some pango and libfreetype packages.

---

### Post by Mokura on 2012-04-10
[FONT=Verdana]Solved, uh, somehow.  Deleted "/usr/lib/freetype-infinality" and all of infinality's configs in "/etc/fonts" and it went back to using the settings in my home .fonts.config.  Either I did what I was supposed to without knowing so, or Xubuntu is a lot more resistant to newbie tinkering than I suspected.  Thanks for the help, though!
[/FONT]

---

