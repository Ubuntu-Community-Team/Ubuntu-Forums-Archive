---
title: ": libreoffice"
date: 2011-02-18
forum: General Help
---

### Post by David_P_Morse on 2011-02-18
How to install : libreoffice  on Ubuntu 10.10

Tried Ubuntu Software Center & Synaptic Manager

Thank you

---

### Post by I&#9829;HTML5 on 2011-02-18
From [http://drupal.txwikinger.me.uk/content/libreoffice-now-available-ppa-ubuntu-1010-and-1004](http://drupal.txwikinger.me.uk/content/libreoffice-now-available-ppa-ubuntu-1010-and-1004):
> The LibreOffice ppa can be added on Ubuntu 10.10 and 10.04 with

```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
```

Libreoffice can then be installed with

```
sudo apt-get install libreoffice
```

Depending on the Desktop that is (Gnome or KDE), the following command is necessary:

For KDE:

```
sudo apt-get install libreoffice-kde
```

For Gnome:

```
sudo apt-get install libreoffice-gnome
```

As explained in a comment below, in order to install the spellchecker the following line needs to be used (with adjustment of the locale (the example uses English-US):

```
sudo apt-get install aspell aspell-en dictionaries-common hunspell-en-us myspell-en-us
```

---

### Post by artsim2011 on 2011-02-18
thanks for that I've been meaning to install this.

---

### Post by David_P_Morse on 2011-02-19
Thank you for your help I&#9829;HTML5  this is most useful.

---

### Post by I&#9829;HTML5 on 2011-02-19
Glad I could help! Happy Ubuntuing!

---

### Post by emarkay on 2011-02-21
FWIW, here is the "official" LO support forums:
[http://nabble.documentfoundation.org/LibreOffice-f1639495.html](http://nabble.documentfoundation.org/LibreOffice-f1639495.html)

They recommend Ubuntu users use the Ubuntu forums and Bug tracking, but there is a lot of cross-platform and other info on there.

Also, you should remove OO first, too.

---

