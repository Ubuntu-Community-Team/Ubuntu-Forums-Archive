---
title: "delete hard returns with sed???"
date: 2011-04-20
forum: General Help
---

### Post by jedson3 on 2011-04-20
I would like to be able to get rid of hard returns when they show up in files (like ocr files). Is sed the best way to do this? If so, exactly what script do I use. How do I indicate the hard returns? Tried sed s/^M// source.txt >output.txt and that doesn't seem to do it.  

jedson

---

### Post by lloyd_b on 2011-04-20
> **jedson3 said:**
> I would like to be able to get rid of hard returns when they show up in files (like ocr files). Is sed the best way to do this? If so, exactly what script do I use. How do I indicate the hard returns? Tried sed s/^M// source.txt >output.txt and that doesn't seem to do it.  

jedson

(FYI - Unix-type systems like Linux don't use the CR (carriage return) character to indicate the end of a line.  Instead, they use a "newline" character ('^J').  But I'd recommend using '\n', as that's the standard escape sequence for a newline.  In the event you want to search for actual CR characters, then '\r' works in place of '^M'.)

It can be done with sed, but it's not straightforward - sed normally processes text a line at a time, and never really sees the newline.

I'd suggest 'tr' ```
cat source.txt | tr -d '\n' > output.txt
``` 'tr' normally converts one character to another.  But when the -d option is supplied, it searches for instances of the specified character, and deletes them instead.

Lloyd B.

---

### Post by jedson3 on 2011-04-20
Thanks very much for this very helpful information. 

Jim

---

### Post by jedson3 on 2011-04-20
PS -- I love your signiture

---

