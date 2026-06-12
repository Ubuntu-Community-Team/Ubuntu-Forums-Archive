---
title: "Installing Windows .fon fonts in Kubuntu"
date: 2006-04-20
forum: General Help
---

### Post by CapKrugers on 2006-04-20
I've looked at a few guides, and I've tried to convert the .fon files I copied from my Windows partition to my Kubuntu filesystem to .bdf files and .pcf files using fnt2bdf and bdftopcf and fontforge, but these don't seem to work. I've also played around with the encoding (Latin1, or whatever, instead of Windows ANSI). The KDE Font Installer then does not allow me to install these font files, saying that they are not fonts at all! 

How can I install my Windows .fon fonts (such as Fixedsys, MS Sans Serif, etc.) in KDE? If there are any versions for Linux so I don't have to convert, I'd like to know, but please don't try to tell me how they are bad fonts which I shouldn't use. I want to get them working. Thanks!

---

### Post by Rog131 on 2006-04-20
Have you tried Unofficial Ubuntu 5.10 (Breezy Badger) Starter Guide:
[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

# 7.49 How to install Extra Fonts
[http://easylinux.info/wiki/Ubuntu#How_to_install_Extra_Fonts](http://easylinux.info/wiki/Ubuntu#How_to_install_Extra_Fonts)

msttcorefonts (Microsoft's TrueType core fonts)

sudo apt-get install msttcorefonts
sudo fc-cache -f -v

---

### Post by CapKrugers on 2006-04-21
I am not sure if I made it clear in my first post, but the fonts I wish to install are bitmap fonts (.fon) instead of TrueType fonts (.ttf, which are included in msttcorefonts). So, this guide does not help me at all.

---

### Post by goonies on 2007-02-20
id like to know how to do this too, i use ubuntu edgy

---

