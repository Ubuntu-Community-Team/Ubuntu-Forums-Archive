---
title: "Adjust .po file using gettext or poeditor"
date: 2010-07-13
forum: General Help
---

### Post by Stoneface on 2010-07-13
I have a .po and .mo file. I need to add several lines . I would like to edit the .po file. With Poedit I do not seem to be able to add lines to the .po file. I believe I need the .pot file for this. How can I create a .pot file from a .po file so I can adjust details and create the .po and .mo anew?

---

### Post by Stoneface on 2010-07-13
I do know now the difference between pot-files and po-files is that pot-file are po-files which contain empty msgstr (msgstr "") and that I have to use a command like ```
msgfilter -i file -o file filter sed -e d | sed -e '/^# /d'
``` to convert the .po to a .pot file, but can anyone give me the correct/complete command? The one mentioned here:[http://doc.mpv.ru/gettext/gettext_7.html](http://doc.mpv.ru/gettext/gettext_7.html) which I adjusted slightly and pasted here above causes this error:```
msgfilter: filter subprocess failed
```

---

### Post by Stoneface on 2010-07-13
Think I got it: ```
msgfilter -i inputfile -o outputfile sed -e d | sed -e '/^# /d'
```

---

### Post by Stoneface on 2010-07-13
[s]Hmm, cannot open the .pot file in Poeditor now. I wonder what went wrong. Maybe it got corrupted? I do no the .pot misses a msgstr. How to fix this?[/s] I can open it now and I do not believe the empty msgstr is an issue as othe r.pot files have the same issue. Only this .pot has lost all translation strings now. So I will use the .po or .mo and manipulate that and add the lines I need. For anyone interested, use```
msgunfmt [path_to_file.mo] > [path_to_file.po]
``` to convert .mos to .pos

---

