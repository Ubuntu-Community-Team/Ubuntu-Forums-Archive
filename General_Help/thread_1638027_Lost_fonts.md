---
title: "Lost fonts"
date: 2010-12-05
forum: General Help
---

### Post by motorcity909 on 2010-12-05
Hi all

This morning after booting up, update manager ran automatically and I clicked install.  One of the updates came up with a Microsoft EULA to agree to.

I didn't really think about what it was for and closed it rather than agree to the EULA.

Only afterwards did I realise it was for the MS fonts I'd got installed like Arial and Verdana etc.

I now can't see those fonts in, say, Open Office.  The msttcorefonts package doesn't appear in Synaptic.  I've also tried it in a terminal - 

```
sudo apt-get install msttcorefonts
```and get this back

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'ttf-mscorefonts-installer' instead of 'msttcorefonts'
ttf-mscorefonts-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  python-evince python-gnomedesktop python-metacity python-mediaprofiles
  python-bugbuddy python-totem-plparser python-gtop
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

```Which to me kind of implies it is still installed.

Also, if I open a file in Open Office that was originally done in Arial, that font is there but if I start a new document, it's not.

Any idea on how I get these fonts back?

Help much appreciated as always.

Dave

---

### Post by TeoBigusGeekus on 2010-12-05
Try
```
sudo apt-get install --reinstall msttcorefonts
```

---

### Post by motorcity909 on 2010-12-05
Oh that rocks.  Thank you so much.

Cheers
Dave

---

### Post by Handssolow on 2010-12-07
My wife's PC must have had this happen to her PC in the last few weeks, namely OpenOffice was missing Arial and Times New Roman fonts on a new document but older existing documents written with Times New Roman can still be displayed. When I re-install the microsoft compatible fonts for her there wasn't a EULA. She's not installed the new update so I expect the EULA will appear or more than likely we'll remove some commercial fonts.

---

### Post by Handssolow on 2010-12-08
Come to think of it, in Synaptic the package ttf-mscorefonts-installer has this note?

NOTE: the package ttf-liberation contains free variants of the Times,
Arial and Courier fonts. It's better to use those instead unless you
specifically need one of the other fonts from this package.

Why then are you required to agree to a microsoft EULA before you can install these free fonts? So are they free or not? Apparently these fonts aren't free, they come with strings attached, a microsoft EULA.

Incidentally, there's always the Liberation fonts as alternatives.

---

