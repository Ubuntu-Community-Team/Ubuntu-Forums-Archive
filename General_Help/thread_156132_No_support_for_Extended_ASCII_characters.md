---
title: "No support for Extended ASCII characters?"
date: 2006-04-06
forum: General Help
---

### Post by blakemadden on 2006-04-06
Does Kubuntu support extended ASCII (non English) characters?  I have some simple UTF-8 text files that have French and Danish characters in them and when I open them in Kate or KDevelop or KWord they show these characters as garbage (little square characters).

My LANG variable is en_US.UTF-8.  Why can none of these text editors display simple Western European characters?  I seems like anything not in the range of 7-bit ASCII (1-127) can be displayed.  Is there some sort of package that you need to install?

Thanks,
Blake

---

### Post by ntrebing on 2006-04-09
I think I have a similar problem, and I'm really puzzled by it. However, I have no problems with French or Danish characters. The problem seems to be limited to some Chinese characters whose simplified version differs from the traditional version, to some Vietnamese letters and to Chinese pinyin letters with the third tone. The problem is still really annoying since it makes KDE unsuitable for working with Chinese text.

Of course, with GTK programs, everything gets displayed correctly. I have no idea why it doesn't work for me with KDE programs. Note that I have observed this problem on several Kubuntu systems, so it seems to not work by default. However, some people seem to be able to happily use it e.g. with Chinese text. But, for example, I tried to configure Konsole to properly display Chinese characters. I tried every single installed font, but that didn't change anything.

You can see from the screenshot what does and what doesn't work.

---

### Post by blakemadden on 2006-04-14
[QUOTE=ntrebing]I think I have a similar problem.[/QUOTE]

Good to see that others have a similar problem.  Weird, because I used KDE with the Mandrake distro a few years ago and it was fine.

---

