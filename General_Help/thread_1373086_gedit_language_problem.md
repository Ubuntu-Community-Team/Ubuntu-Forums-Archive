---
title: "gedit language problem"
date: 2010-01-05
forum: General Help
---

### Post by evilman on 2010-01-05
Hello, i'am just started to use ubuntu 9.10, iam really new in linux i have problem when i open file with gedit wich includes some russian language, i just can't see russian language, what i see is just some hearoglifs, ty for help and sorry for my bad english :)

---

### Post by Vaphell on 2010-01-05
in the 'open file' window try to select proper character encoding, in your case probably cyrillic iso-8859-5 or cyrillic win-1251. If i am not mistaken, by default gedit tries to use utf-8 coding and there can be differences in character mapping if the text file was created using other coding.

---

### Post by evilman on 2010-01-05
> **Vaphell said:**
> in the 'open file' window try to select proper character encoding, in your case probably cyrillic iso-8859-5 or cyrillic win-1251. If i am not mistaken, by default gedit tries to use utf-8 coding and there can be differences in character mapping if the text file was created using other coding.

no its not helping.

---

### Post by Vaphell on 2010-01-05
does open office open it properly?
maybe you can upload an example file somewhere? or maybe at least screenshot?

---

### Post by evilman on 2010-01-05
> **Vaphell said:**
> does open office open it properly?
maybe you can upload an example file somewhere? or maybe at least screenshot?

no i try all codings in open ofice still same where is atachment: [ATTACH]142573[/ATTACH]

---

### Post by Leppie on 2010-01-05
did you install the Cyrillic fonts?
try installing the Cyrillic xfonts:
```
$sudo apt-get instell xfonts-cyrillic
```

---

### Post by Vaphell on 2010-01-05
i took your file and managed to open it properly with win-1251 coding, though for unknown reason i failed first time (probably having it opened already and trying to open again with encoding chosen does nothing). OO.writer opens the file properly too when using win1251

> 
<td style="padding:2px;"><a href="{$link_favorites}">&#1052;&#1086;&#1080; &#1079;&#1072;&#1082;&#1083;&#1072;&#1076;&#1082;&#1080;</a></td>


if you want to open text files using win1251 char map by default you need to switch the order of encodings gedit tries to use to load file.

gconf-editor
goto apps/gedit-2/preferences/encodings

---

