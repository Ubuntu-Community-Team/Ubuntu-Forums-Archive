---
title: "Ubuntu 8.04 (qt4.3) and Ubuntu 9.04 (qt4.5) - Same font looks different?"
date: 2009-10-02
forum: General Help
---

### Post by jasmine55 on 2009-10-02
Hi!

with different versions of ubuntu (and therefore qt) I have a very annoying problem regarding the font size in qt apps.

It seems, that since qt 4.4 the font size is generally larger than before.
I use the same settings with qtconfig. Also the settings of fontconfig are the same (antialias, hinting etc.). Changing the xvt.dpi xrdb setting has no effect as well as changing the xserver dpi setting (xrandr --dpi) does not affect the font appearance
(Please see attachment: left side qt 4.3, right side qt 4.5).

E.g.  if I design a GUI with some fixed-width (pixels) elements and place some text on it, then with qt 4.3 it fits, but it fits not with later qt/ubuntu versions.

I recognized that there where some changes regarding the font rendering of qt (it seems to use freetype now?) but can this affect the GUI that much, that the font size is different now? I don't believe it...

Does anyone have an idea, why the font looks different and how to fix it?

Thank you very much:)
jasmine

---

### Post by Giblet5 on 2009-10-02
Qt's font handling is the only gripe I've ever had with Qt.

It's safe to say that the newer Qt is doing it "more right".

Are you writing Qt4 code and trying to gain consistency, or are you an end user wondering why there's no consistency?

---

### Post by sedawk on 2009-10-02
Hello!

Every QWidget has a method called fontInfo that returns
a QFontInfo structure/class.
Have you checked if the data differs or if the data is
equal despite the different look?

If there is a difference you might be able to
solve the problem with QApplication.setFont.

One of the few functions of X11 programming I still
remember is XTextWidth(font,string, strlen). So you are confronted
with a very old problem when it comes to GUI programming ;-)

---

### Post by Giblet5 on 2009-10-02
> **sedawk said:**
> One of the few functions of X11 programming I still remember is XTextWidth(font,string, strlen). So you are confronted with a very old problem when it comes to GUI programming ;-)

+1^10

It's not the #1 headache, but it might be #2.

(#1 is reserved for the marketing department)

---

### Post by jasmine55 on 2009-10-03
thank you for your ideas.

I checked the fontInfo() result of the QWidgets and noticed, that the system simply uses different fonts.

So I googled a little bit and found that:

[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/209358](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/209358)

> It seems that this Qt version has hardcoded the generic type "Helvetica" as "Sans Serif". Helvetica is defined at /etc/fonts/conf.d/30-metric-aliases.conf as "Nimbus Sans L"
 You can change it there or add to your ~/.fonts.conf the following stanzas:
         <alias binding="same">
          <family>Helvetica</family>
          <accept>
          <family>Arial</family>
          </accept>
        </alias>
[http://launchpadlibrarian.net/12981562/qt3-qt4.png](http://launchpadlibrarian.net/12981562/qt3-qt4.png)

Changing the default font for QT in qtconfig to a direct font name (not Sans, Serif etc.) solved the problem for qt4.3 (workaround)... :)

---

