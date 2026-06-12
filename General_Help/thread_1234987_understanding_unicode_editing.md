---
title: "understanding unicode editing"
date: 2009-08-08
forum: General Help
---

### Post by krishna1650 on 2009-08-08
hello all,
using scim i wrote a file in bengali(indian language). now i want to know whether it is saved in unicode or any other way? what should i do?

my aim is to write a file in bengali in unicode.

thank you.

---

### Post by SPr on 2009-08-08
```

file my_file

```
Does that work?

---

### Post by krishna1650 on 2009-08-09
> **SPr said:**
> ```

file my_file

```
Does that work?

thank you for reply. i want to know more, i want to see what exact( instead of bengali characters, the unicode representing the bengali characters)  is written there.

so can you give some more depth information.

---

### Post by SPr on 2009-08-09
I don't understand what you want but you can get a hexdump using:
```

hd -C my_file|more

```
look at man hd for more options.

---

