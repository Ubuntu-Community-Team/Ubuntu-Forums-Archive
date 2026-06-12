---
title: "Removing unnecessary fonts without ubuntu-desktop meta-package"
date: 2006-06-26
forum: General Help
---

### Post by flabbah on 2006-06-26
Is there any way to remove all the unnecessary fonts (fonts not related to your native language) without also removing the ubuntu-desktop meta-package?

For example, if I am using English fonts, how can I remove all the things like
ttf-thai-tlwg, etc.

Thanks!

---

### Post by aysiu on 2006-06-26
What's wrong with removing the *ubuntu-desktop* metapackage?

---

### Post by flabbah on 2006-06-26
[QUOTE=aysiu]What's wrong with removing the *ubuntu-desktop* metapackage?[/QUOTE]

Someone mentioned that removing ubuntu-desktop could subsequently cause certain packages to not get updated  ... is this true?

---

### Post by aysiu on 2006-06-26
[QUOTE=flabbah]Someone mentioned that removing ubuntu-desktop could subsequently cause certain packages to not get updated  ... is this true?[/QUOTE]
Before you do a dist-upgrade (from Breezy to Dapper or from Dapper to Edgy), you should always install the appropriate metapackage (*ubuntu-desktop*, *kubuntu-desktop*, *edubuntu-desktop*), but after the release date, it's pretty safe to remove.

---

### Post by fdimmling on 2006-06-26
What's wrong with just deleting the .ttf files and directories from /usr/share/fonts/truetype or /usr/share/fonts/type1. The font lists are updateted when Xorg is starting AFAIK. Anyway i did it in Breezy and in Dapper and nothing happened except that my OO font list is not cluttered anymore and the Chinese characters are all taken from the same font, which was the main reason for doing it.

Friedrich

---

### Post by flabbah on 2006-06-27
[QUOTE=aysiu]Before you do a dist-upgrade (from Breezy to Dapper or from Dapper to Edgy), you should always install the appropriate metapackage (*ubuntu-desktop*, *kubuntu-desktop*, *edubuntu-desktop*), but after the release date, it's pretty safe to remove.[/QUOTE]

I was looking at the Debian Policy manual, and section 7.4 talks about Virtual Packages, and 7.5.2 talks about "Replaces with forced removal"

I'd like to create a virtual package "non-required-fonts" which virtually "provides" the unneeded stuff from all the other font packages ... are there any basic tutorials that would show me how to do create such a package ? I doubt I would find the exact same thing, but something along those lines.

Thanks a lot.

---

### Post by flabbah on 2006-06-27
[QUOTE=fdimmling]What's wrong with just deleting the .ttf files and directories from /usr/share/fonts/truetype or /usr/share/fonts/type1. The font lists are updateted when Xorg is starting AFAIK. Anyway i did it in Breezy and in Dapper and nothing happened except that my OO font list is not cluttered anymore and the Chinese characters are all taken from the same font, which was the main reason for doing it.

Friedrich[/QUOTE]

I guess that would work ... who needs that stinkin package manager anyway! But seriously, the Debian Policy guide has a section "11.8.5 Packages providing fonts" which details all the hard work font packages have to do. I'd rather cleanly install / remove them, rather then start deleting stuff.

---

### Post by fdimmling on 2006-06-28
[QUOTE=flabbah]I guess that would work ... who needs that stinkin package manager anyway! But seriously, the Debian Policy guide has a section "11.8.5 Packages providing fonts" which details all the hard work font packages have to do. I'd rather cleanly install / remove them, rather then start deleting stuff.[/QUOTE]

You are certainly right. I had  by mistake deleted a font containing the phonetic alphabet needed by an encylopedia, and you can easily run into problems with fonts that are needed by TeX or any other program. I have seen that at least part of the fonts are contained in extra packages. Therefore I really agree with you: use the package manager!

Friedrich

---

