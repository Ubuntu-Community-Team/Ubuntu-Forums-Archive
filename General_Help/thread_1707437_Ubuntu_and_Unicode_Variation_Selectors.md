---
title: "Ubuntu and Unicode Variation Selectors"
date: 2011-03-15
forum: General Help
---

### Post by dukerussian on 2011-03-15
Hello folks,

I'm using Ubuntu 10.10 and GNOME and I'm trying to typeset some texts in ancient Mongolian and Phags-pa, both of which have been included in Unicode. For Mongolian, I've installed the ttf-manchufont package. For Phags-pa, I've used the font available here: [http://babelstone.blogspot.com/2006/12/phags-pa-shaping-behaviour.html](http://babelstone.blogspot.com/2006/12/phags-pa-shaping-behaviour.html)

Both languages use the Unicode Variation Selectors. In a nutshell, the combination character + variation selector should change the representation of the character to a different variant. This is similar to GSUB in OpenType. To see what I'm talking about, you can look at the table of standardized Unicode variants here: [http://www.unicode.org/Public/UNIDATA/StandardizedVariants.html](http://www.unicode.org/Public/UNIDATA/StandardizedVariants.html)

Unfortunately, this feature does not work in Ubuntu 10.10, in any of the software packages that I have attempted to use: OpenOffice, GIMP or gedit. It does work in Windows 7, using the same fonts, so the issue is not with the fonts, but with Ubuntu (or GNOME?) typesetting.

I don't know enough about how Unicode typesetting works in Ubuntu to know where to post a bug report / feature request. Any pointers would be appreciated.

As Unicode is planning on releasing a large number of CJK variants using the Variation Selector methodology in the near future, it would be important to get this feature supported in Ubuntu.

CJK after all would be more widely used than something like Phags-pa.

---

