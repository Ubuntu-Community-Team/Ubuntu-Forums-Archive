---
title: "problem: text characters replaced by little rectangles in openoffice"
date: 2010-02-25
forum: General Help
---

### Post by laerub18 on 2010-02-25
Hi,

i have a problem, when i open OO, the text of the menus is replaced by little rectangles.

For example, instead of:

_F_ile   _E_dit   _V_iew   etc..

i will have

                                 _&#58748;_&#58748;&#58748;&#58748;    _&#58748;_&#58748;&#58748;&#58748;     _&#58748;_&#58748;&#58748;&#58748;
 
(they look more like rectangles than squares) 
i also have this problem with drop down menus, font names, font styles and even with the numbers on the ruler.

what to do ?

Ubuntu 9.10, OO 3.1

---

### Post by laerub18 on 2010-02-25
the weird thing is that some of the words are normal. see attachment

---

### Post by wangsuda on 2010-02-25
You have, IMO, a shortage of fonts. When something is written in font "A" and you don't have font "A" then you get the rectangles. What you need are more fonts. To get a full range of fonts, open the terminal and type
```
sudo apt-get install ttf-mscorefonts-installer mplayer-fonts ttf-xfree86-nonfree xfs cabextract ttf-liberation ttf-mscorefonts-installer
```To add more and fancier fonts, enter ```
sudo apt-get install ttf-larabie-straight ttf-larabie-deco xfonts-terminus-dos xfonts-terminus xfonts-terminus-oblique xfonts-mona tv-fonts ttf-tuffy ttf-sjfonts ttf-georgewilliams ttf-fifthhorseman-dkg-handwriting ttf-essays1743 ttf-opensymbol ttf-mgopen ttf-freefont ttf-dustin ttf-dejavu-extra ttf-dejavu-core ttf-dejavu ttf-bpg-georgian-fonts equivs ttf-sil-gentium gnome-specimen bsd-mailx dctrl-tools devscripts diffstat dput libapt-pkg-perl libauthen-sasl-perl libdevel-symdump-perl libio-pty-perl libio-stringy-perl libipc-run-perl libparse-debcontrol-perl libpod-coverage-perl libterm-size-perl libtest-pod-perl lintian patchutils postfix wdiff
```That should solve your problem.

---

### Post by laerub18 on 2010-02-25
ok i typed the command (only the first) restarted, and the problem is still there..

did you see the attachment i uploaded ? it shows that under the same menu, some words will appear and others not. It's weird because they are supposed to have the same fonts.

---

### Post by Hagar Delest on 2010-02-26
See that one, several fixes (read until the end): [[Solved] No text in OpenOffice menus](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=10183).

---

### Post by laerub18 on 2010-02-26
Hey hagar, i tried that but it didn't work. however it gave me the idea to try something else, so  what i found is that the problem is due to the opensymbol font.

simply changing the font in system/appearance fixes the problem. 

but then what if i want to use the opensymbol font, how can i reinstall it ? i could find info on google about that.

---

### Post by wangsuda on 2010-02-26
> **laerub18 said:**
> Hey hagar, i tried that but it didn't work. however it gave me the idea to try something else, so  what i found is that the problem is due to the opensymbol font.

simply changing the font in system/appearance fixes the problem. 

but then what if i want to use the opensymbol font, how can i reinstall it ? i could find info on google about that.
You could try here [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=opensymbol+font](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=opensymbol+font) but I don't know if it's what you want.

---

### Post by Hagar Delest on 2010-02-27
> **laerub18 said:**
> the problem is due to the opensymbol font.

simply changing the font in system/appearance fixes the problem. 

but then what if i want to use the opensymbol font
I don't understand. Do you mean that you use the OpenSymbol font for your desktop (windows titles and so on)? Where do you use that font exactly?

Perhaps there is a problem with the font file on the system for OOo.

---

### Post by laerub18 on 2010-03-01
> I don't understand. Do you mean that you use the OpenSymbol font for your desktop (windows titles and so on)? Where do you use that font exactly?

Perhaps there is a problem with the font file on the system for OOo.

in System/Preferences/Appearance -> Fonts, i chose opensymbol for the applications font. It worked for all applications except OO, where little rectangles were displayed.

in Sys/Pref/Appearances, when i changed Opensymbol with something else, it fixed the problem in OO. 

I was just wondering how to reinstall the Opensymbol font package, since my OO only has a problem with this font. (It's just out of curiosity as i chose another font with works perfectly).

---

### Post by Hagar Delest on 2010-03-01
Try to download it from the web, Google should find some sites proposing that font file.

---

