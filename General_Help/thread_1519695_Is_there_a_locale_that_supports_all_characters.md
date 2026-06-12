---
title: "Is there a locale that supports all characters?"
date: 2010-06-28
forum: General Help
---

### Post by ownaginatious on 2010-06-28
I sometimes have files and things with characters from different languages (i.e. Chinese, German, French.etc) on my system, and I get annoyed that I can't read any of it through the terminal (my locale is currently en_CA.utf-8 ).

Is there some kind of "English international" locale or something that I can set that just supports all unicode characters?

Thanks.

---

### Post by Bachstelze on 2010-06-28
Any UTF-8 locale should support all (UTF-8) characters. For exammple my locale is en_GB.UTF-8, and I have no problems with Japanese or Arabic characters. Your problem is probably your font: if you don't have a font that includes a given character, then it can't be displayed, regardless of the locale.

---

### Post by ownaginatious on 2010-06-28
Hmm, that might be the problem. I tried changing the terminal font to courier on the system I'm using SSH from, and still I am unable to display characters.

It's weird, like I can create a file called "Ü", and it will display properly when I use ls, but when I try and paste an u-umlaut into nano, it shows up at a black diamond with a question mark on the inside.

---

### Post by Bachstelze on 2010-06-28
> **ownaginatious said:**
> Hmm, that might be the problem. I tried changing the terminal font to courier on the system I'm using SSH from, and still I am unable to display characters.

It's weird, like I can create a file called "Ü", and it will display properly when I use ls, but when I try and paste an u-umlaut into nano, it shows up at a black diamond with a question mark on the inside.

Check that your terminal emulator is also using utf-8 encoding. I also recomment DejaVu Sans Mono as a temrinal font, is supports much more characters than the default Monospace or Courier.

---

