---
title: "LibreOffice doesn't see installed font"
date: 2012-02-27
forum: General Help
---

### Post by jejones3141 on 2012-02-27
There's a font I have installed, Day Roman from the Apostrophic Laboratories fonts, that I've used in the past with no trouble--but recently I wanted to use it, and found that LibreOffice does not list it.

Font Manager sees it, and will display it--but its name in the list of fonts is not shown in boldface as the others are, and the font name is shown overstruck, again unlike the others. I would think this reflects whatever situation is causing LibreOffice not to show the font as a choice, but I've not found anything in Font Manager help that says what that might indicate. The .ttf file is world-readable, so it's not file permission (besides, Font Manager can display it).

If someone has seen this kind of problem in the past and solved it, I'd very much like to hear how you did it. I am running 64-bit Oneiric Ocelot, with libfreetype6 version 2.4.4-2ubuntu1.1, the latest version in the repositories as far as I know.

---

### Post by forrestcupp on 2012-02-27
Where did you install the font. If you haven't already done it, try making a folder called **.font** in your /home folder, and copy the ttf files there.

---

### Post by jejones3141 on 2012-02-27
> **forrestcupp said:**
> Where did you install the font. If you haven't already done it, try making a folder called **.font** in your /home folder, and copy the ttf files there.

It's in /usr/share/fonts/truetype/apostrophic/DAYROM__.ttf; I copied it to ~/.fonts (all the references I've seen to putting fonts where an individual user can see them give that path, not ~/.font), but that made no difference. If it's some error in the .ttf file, of course, it would be present in the copy, too... but OTOH, if that were the problem, why can Font Manager display it?

---

### Post by Laobi on 2012-02-27
Have you updated your font cache?

```
sudo fc-cache -fv
```

---

### Post by jejones3141 on 2012-02-27
> **Laobi said:**
> Have you updated your font cache?

```
sudo fc-cache -fv
```

It's been some time since I actually installed Day Roman and the other Apostrophic Labs fonts, but I tried it--thanks for the suggestion (no sarcasm intended, despite the next sentence). It did have an effect: now neither LibreOffice nor font manager sees Day Roman. (Fontmatrix does, though, and shows that it sees both the file in /usr/share/fonts/truetype/apostrophic and in ~/.fonts.)

OTOH, fc-cache output did include

/usr/share/fonts/truetype/apostrophic: caching, new cache contents: 226 fonts, 0 dirs

which surprised me--though it's hard for me to reconcile the font now being cached with font manager no longer being able to see it.

---

### Post by HarryG123 on 2012-04-12
I had the same problem in xubuntu 11.10. With the tips i got here I was able to fix it. To recap my problem: fonts placed in ~./font/ were invisible to the system. And I had run sudo fc-cache -f.   Then I installed the same fonts in /usr/share/fonts and /usr/local/share/fonts, not forgetting to sudo chown the font files to root, and running fc-cache -f -v 
---  The ttf fonts still didn't show up in Libreoffice, nor in gucharmap.  

Following the directions here, I deleted the duplicate font directories under /usr, then used the Ubuntu Software Center to install Font Manager.  After it was installed, I played around with the buttons on the lower left side of the Font Manager window to set the FM preferences and install the fonts in the default ~./fonts directory.

Now they are visible in gucharmap and fontmanager and Libreoffice.


What does Font Manager got that my terminal entries hasn't got?  --aaaahh! Who cares? It's working now. ;)

---

