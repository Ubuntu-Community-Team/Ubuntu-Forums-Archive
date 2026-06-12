---
title: "Timestamps"
date: 2012-08-26
forum: General Help
---

### Post by nato85 on 2012-08-26
Hey Guys

Got an easy one for you pro's


What is the command I type into Ubuntu's command line to bring up file information....

Such as when a file was last modified

---

### Post by Vaphell on 2012-08-26
```
stat filename
```
if you are interested only in modification time
```
stat -c %y filename
```

---

### Post by nato85 on 2012-08-26
thank you

i knew it be something easy, couldnt find any documentation on it.

This thread can be closed by admin if needed.

Cheers

---

### Post by Vaphell on 2012-08-26
how about you mark it as [solved] in thread tools menu? that's what it's for ;-)

---

