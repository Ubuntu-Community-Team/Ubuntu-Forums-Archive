---
title: "simple language problem"
date: 2010-02-14
forum: General Help
---

### Post by nkbatsi on 2010-02-14
hello,
i have two language layouts enabled in my pc, english and greek, my os is in  english.
 i can read greek text files in openoffice but i can not read greek subtitles
 in order to edit them neither in gedit nor in subtitle editor. 
can anybody please tell me what am i doing wrong?

thanks!

---

### Post by StuartN on 2010-02-14
You probably have Greek subtitles in ISO8859-7 encoding. You can convert a subtitle file.srt to unicode with:

```
iconv -f iso8859-7 -t utf-8 file.srt > file2.srt
```

See [http://ubuntuforums.org/archive/index.php/t-335839.html](http://ubuntuforums.org/archive/index.php/t-335839.html) for more suggestions.

---

### Post by nkbatsi on 2010-02-15
thanks for the answer,
worked fine!!!

---

