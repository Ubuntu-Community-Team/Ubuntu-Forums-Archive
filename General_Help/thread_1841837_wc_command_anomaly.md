---
title: "wc command anomaly"
date: 2011-09-10
forum: General Help
---

### Post by Trave11er on 2011-09-10
Have spotted that wc command gives different number of charachers of-m and wc -w give different output for the same text saved in gedit and openoffice. The value also differs from the one openoffice gives out when asked to count words and characters. Can anyone explain that plz? Thx.

---

### Post by sisco311 on 2011-09-10
Welcome to the forums!

wc -m prints the byte count. UTF-8 uses one byte for any ASCII characters, which have the same code values in both UTF-8 and ASCII encoding, and up to four bytes for other characters.

See: [http://en.wikipedia.org/wiki/Character_encoding](http://en.wikipedia.org/wiki/Character_encoding)
and
[http://en.wikipedia.org/wiki/Unicode](http://en.wikipedia.org/wiki/Unicode)

---

### Post by Trave11er on 2011-09-10
OK. Thank you very much!

---

### Post by sisco311 on 2011-09-10
You are welcome!

Don't forget to mark this thread as [SOLVED]. Use the Tread tools menu at the top of the page. Thanks.

---

