---
title: "Enabling dead keys on the keyboard"
date: 2010-08-28
forum: General Help
---

### Post by ryu kun on 2010-08-28
I could not find any way to enable dead keys on my keyboard on Lubuntu 10.04 via gui.

I created xorg.conf by using X -configure command and tried to add followings into /etc/X11/xorg.conf but it did not work.

```

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
        Option		"XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "tr"
        Option          "XkbVariant"    "intl"
        Option          "XkbOptions"    "compose:rwin"
EndSection

```

Now I cannot type any characters with accent. ALT-GR key is not working.

My keyboard layout selected as Turkey-Q during installation.

Any help will be appreciated.

---

### Post by luigi_mb on 2010-08-28
Click on System > Preferences > Keyboard . Select the Layout tab. Then click on Add, and select Laanguage (English) and Variant (USA International (with dead keys)). After you finish, there will be a new icon, "USA", on the top panel. It's a toggle which allows you to switch between the default and the variant. The variant is indicated by USA<sub>2</sub>.

/luigi

---

### Post by ryu kun on 2010-08-29
Thank you for your answer. I am using Lubuntu, not Ubuntu. There is not such option in Lubuntu.

I've found a solution for this and explained [here]("http://forum.lxde.org/viewtopic.php?f=8&t=1721&p=4950#p4950"). For explanation in Turkish click [here]("http://www.ertpresso.info/2010/08/28/lubuntuda-sapkali-harfler-ve-diger-aksanli-karakterler/").

---

