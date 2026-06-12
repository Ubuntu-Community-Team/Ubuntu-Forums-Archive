---
title: "Reading sinhala Fonts"
date: 2010-08-28
forum: General Help
---

### Post by jayaboy123 on 2010-08-28
Hi, I am a sri lankan. I can't read sinhala news papers in obuntu o/s.How i solve this problem?

---

### Post by madhawa_ on 2011-04-18
> Tested on Ubuntu 10.10

1. Open a new Terminal

```
sudo apt-get install ttf-sinhala-lklug ibus im-switch ibus-m17n m17n-db m17n-contrib language-pack-si-base
```


```
rm -f ~/.xinput.d/* ; im-switch -z all_ALL -s ibus
```

2. **System > Preferences > Keyboard Input Methods**

Select "Yes" to start **iBus daemon**. Go to "iBus Preferences" then "Input Method" tab. Scroll through the list and choose **Sinhala; Sinhalease > wijesekara-preedit (m17n)**.

3. **System > Administration > Language Supprt**

Set "Keyboard input method system" as **ibus**.

4. Download "Malithi" or any other font according to your choice from [here]("http://www.locallanguages.lk/sinhala_unicode_converters").

Press **Alt + F2** and run **gksu nautilus**. Locate **/usr/share/fonts/truetype** then clear the **freefont** directory in it.

5. Open the Terminal again.

```
sudo fc-cache -f -v

```

---

