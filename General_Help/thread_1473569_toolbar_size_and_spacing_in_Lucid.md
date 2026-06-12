---
title: "toolbar size and spacing in Lucid"
date: 2010-05-05
forum: General Help
---

### Post by snivek on 2010-05-05
I upgraded to Lucid today and noticed that toolbar spacing/sizing is HUGE.  In eclipse it is making my once single line toolbar wrap down to too.  There is a ton of waisted space here.  Any way I can adjust this?

---

### Post by dino99 on 2010-05-05
metacity --replace

---

### Post by snivek on 2010-05-05
Did not help.  Attached is another screenshot with the vertical spacers turned off (locked the toolbar) and you can really see the waisted space.

---

### Post by PowerKiKi on 2010-06-02
I got same issue here. Wish there was a way to make all icons small, including the one in eclipse.

Could it be JRE related ? when I installed a JRE, I noticed the default-jre and open-6-jre... I believe I installed defaut-jre, which one did you take ?

---

### Post by s_baramov on 2010-06-02
Well, it appears that it is a Gnome/GTK configuration issue. I have found two solutions:

1. Get a monitor with a really high resolution (like 1980x1028 ). That solves the issue.

2. Reconfigure the GTK library. 

On my part, I could not get the new monitor, so I went with #2. Here is a good way to start [http://tiny.cc/flbqx]("http://tiny.cc/flbqx"). Following these instructions I have ended up with this .gtkrc-2.0  file:

```
style "gtkcompact" {
    font_name="Sans 9"
    GtkToolbar::internal-padding=0
    GtkToolbar::space-size=0
}

class "GtkWidget" style "gtkcompact"

```

Hope it helps,
Stefan

---

### Post by PowerKiKi on 2010-06-03
Somehow I couldn't make it work. So I ended up using the Rio517's theme available on github:
[http://github.com/Rio517/AmbianceCompact](http://github.com/Rio517/AmbianceCompact)

It's the default Lucid Lynx theme but much more compact (no padding wihtin toolbar/menu)

---

