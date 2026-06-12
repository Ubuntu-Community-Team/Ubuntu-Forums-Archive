---
title: "Photoshop 7 help."
date: 2009-08-23
forum: General Help
---

### Post by JJ1 on 2009-08-23
Hello all. Been a while since my last post, as most things are going well with the Xp to Ubuntu switch. The one thing I do not like about Ubuntu, is Gimp. I just cannot get used to using it, as an avid photoshop 7 user. So, I decided to install photoshop 7 using Wine. Everything went very smooth, and all work great. However, when I try to use the text tool, it displays an error stating that it cannot locate the defauly system font, and will not let me use the font tool. Any help is muchly appreciated.

---

### Post by sandyd on 2009-08-23
perhaps you need
```

sudo apt-get install cabextract
wget http://winezeug.googlecode.com/svn/trunk/winetricks
sudo mv winetricks /usr/bin/
sudo chmod 777 /usr/bin/winetrcks
winetricks allfonts fontfix

```

if that doesn't work, you **might** want to install one of the beta versions of wine.

---

### Post by JJ1 on 2009-08-23
> **carlee said:**
> perhaps you need
```

sudo apt-get install cabextract
wget http://winezeug.googlecode.com/svn/trunk/winetricks
sudo mv winetricks /usr/bin/
sudo chmod 777 /usr/bin/winetrcks
winetricks allfonts fontfix

```if that doesn't work, you **might** want to install one of the beta versions of wine.


Thanks. Did all, but these:

sudo mv winetricks /usr/bin/
sudo chmod 777 /usr/bin/winetrcks
winetricks allfonts fontfix
Did nothing, and still have the problem. I am supposed to enter each one by one into terminal right?

---

### Post by themarker0 on 2009-08-23
Yes one by one. I should work.

---

### Post by JJ1 on 2009-08-23
> **themarker0 said:**
> Yes one by one. I should work.


Got some errors while doing so, and it didn't work.

---

### Post by Seankn on 2009-08-23
Open your terminal and type "sudo apt-get install wine" then press enter and should install "wine" a ubuntu program that can run windows applications. Then install Photoshop...

:idea:Seankn:idea:

---

### Post by Bachstelze on 2009-08-23
Do you have [font=monospace]msttcorefonts[/font] installed? I don't remember having such an issue with Photoshop 7 in WINE.

---

### Post by JJ1 on 2009-08-23
> **HymnToLife said:**
> Do you have [FONT=monospace]msttcorefonts[/FONT] installed? I don't remember having such an issue with Photoshop 7 in WINE.

Seeing as I haven't heard of that, I am sure I do not. Mind pointing me in the direction to do so?

---

### Post by oboedad55 on 2009-08-23
> **JJ1 said:**
> Seeing as I haven't heard of that, I am sure I do not. Mind pointing me in the direction to do so?

Here you go:

sudo apt-get install msttcorefonts

That'll do it!

---

### Post by JJ1 on 2009-08-23
> **oboedad55 said:**
> Here you go:

sudo apt-get install msttcorefonts

That'll do it!

Thanks so much for all of your help everybody. My last Ubuntu issue thus far is now solved (=

---

