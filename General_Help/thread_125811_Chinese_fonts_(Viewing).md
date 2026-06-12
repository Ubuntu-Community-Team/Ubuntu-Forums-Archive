---
title: "Chinese fonts (Viewing)"
date: 2006-02-04
forum: General Help
---

### Post by alvinblank on 2006-02-04
I'm having trouble viewing some chinese characters, some doesn't appear at all. Just showing a small black dot, I'm not sure why. I've followed UbuntuGuide to installing extra fonts, I know it's for gnome but I think it wouldn't matter. I've also follow some guides on SCIM that installs chinese fonts, just doing the fonts part but still not helping. Anyone has a apt-get command that installs all chinese fonts avaliable? or am I missing something here.

---

### Post by alvinblank on 2006-02-04
I've installed FireFly fonts, xfonts-intl-chinese, xfonts-intl-chinese-big, kde-i18n-zhcn but I still get square boxes. Is it anything to do with some other fonts that is taking over the display of chinese character than letter firefly do it?

---

### Post by aysiu on 2006-02-05
Open up Adept and do a filter for the phrase *tf*
Scroll down and look for stuff that has the word *Chinese* in it.

These are the ones that have worked for me.

---

### Post by alvinblank on 2006-02-05
I already have those installed. It seems you have Ubuntu running, I've no problems with Ubuntu but I recently decided to jump to Kubuntu and am having problems.

---

### Post by Single on 2006-02-05
Suse has a great guide for this. [http://www.suse.de/~mfabian/suse-cjk/kde-font-setup.html]("http://www.suse.de/~mfabian/suse-cjk/kde-font-setup.html")

You need to install qt3-qtconfig package.

In my case I still use Dejavu Sans as default font (cause I use English lang, so I want nice western font) . And in qtconfig, under the "Font substitution", I choose Dejavu Sans at "Select or Enter a Family: " and add AR ZenKai Uni, AR PL KaitiM GB and AR PL KaitiM Big5 as substitution families below.

---

### Post by alvinblank on 2006-02-05
Thanks Single! It work great, I select Dejavu Sans as the Family and installed Firefly chinese font as use it as the sub family.

---

### Post by my_wing on 2006-10-11
I also can see chinese fonts using kde

I have a newly installed ubuntu 6.06 and kubuntu alternative CD 6.06

This is how I install it

Install ubuntu
Install kde by kubuntu alternative CD using synaptic

Log on in kubuntu

Kmeun->Settings->Language support (Language support)-> select chinese
and my traditional chinese fonts appears on my filename appears

Good luck

---

