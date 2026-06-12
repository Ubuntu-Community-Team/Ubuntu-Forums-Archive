---
title: "Shell Command Help"
date: 2011-01-11
forum: General Help
---

### Post by scottmchi on 2011-01-11
Is There Anyway To Rename .txt Files That Have Been Named In Epoch Time To Real Time Say 1292659969.txt To 121820101542.txt Through A Shell Command? I Have Over 500 Of These Files And They Are A Mess To Organise, So Could The Command Search For All Epoch Time Files In The Current Directory?

---

### Post by hawkmage on 2011-01-11
Try something like this:
```
 for f in 1?????????.txt; do mv ${f} `date -d @${f%.txt} +"%Y%m%d%H%M%S"`.txt;done
```

---

### Post by scottmchi on 2011-01-11
Ok That Works. Will This Work Will Cron Jobs For CPanel.

---

### Post by pqwoerituytrueiwoq on 2011-01-11
i would make an sh file and cron the  script with sh
ex:
sh /path/to/myScript.sh
```
#!/bin/bash
 for f in 1?????????.txt; do mv ${f} `date -d @${f%.txt} +"%Y%m%d%H%M%S"`.txt;done
```

---

### Post by scottmchi on 2011-01-11
Thanks That Worked, But The Files Are In The Wrong Format How Can I Convert Them From "%Y%m%d%H%M%S" To "%m%d%Y%H%m" And Exclude Seconds

---

### Post by hawkmage on 2011-01-11
In general when having a time/date stamp as part of a file name I like to have it Year, Month, Day, Hour, Minute, second so that they will sort in date order.  

I assume that you have already renamed a bunch of files with my previous command that you want to rename to the MMDDYYYYHHmm.txt format.  You can do that with the following:
```
for f in 2?????????????.txt; do mv ${f} `echo ${f} | sed 's/^\(....\)\(..\)\(..\)\(..\)\(..\)\(..\)/\2\3\1\4\5/'`;done
```

---

### Post by scottmchi on 2011-01-11
Ok Thanks For All The Help.

---

### Post by scottmchi on 2011-01-12
One More Thing Ive Been Thinking About That Would Make It A Lot Easier Could You Tell Me A Command To Go From MMDDYYYYHHmm.txt To YYYY_MM_DD_HHmm.txt And One From Epoch.txt To YYYY_MM_DD_HHmm.txt

---

### Post by Smart Viking on 2011-01-12
> **scottmchi said:**
> One More Thing Ive Been Thinking About That Would Make It A Lot Easier Could You Tell Me A Command To Go From MMDDYYYYHHmm.txt To YYYY_MM_DD_HHmm.txt And One From Epoch.txt To YYYY_MM_DD_HHmm.txt

```
echo 555555555555.txt | sed 's/\(..\)\(..\)\(....\)/\3_\1_\2_/'
```
Wow, that was really frustrating, that i didn't figure it out myself. O.o

I eventually gave up myself and asked in #sed on freenode where "vkues" kindly saved me from my brain exploding.. :P

---

### Post by scottmchi on 2011-01-12
Im Using:

echo ????????????.txt | sed 's/^\(..\)\(..\)\(....\)\(..\)\(..\)\/\3_\1_\2_\4_\5/'

And Am Getting This Error.
sed: -e expression #1, char 52: unterminated `s' command

---

### Post by scottmchi on 2011-01-12
Working

---

### Post by hawkmage on 2011-01-12
Try this:
```
for f in ????????????.txt; do mv ${f} `echo ${f} | sed 's/^\(..\)\(..\)\(....\)\(..\)\(..\)/\3_\1_\2_\4_\5/'`;done
```

You had "\)\/\3" where is should have been "\)/\3".  You do not escape the "/"

---

