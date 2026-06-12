---
title: "Displaying Letter-only files from /usr/bin file"
date: 2009-09-27
forum: General Help
---

### Post by shutchis on 2009-09-27
I'm exploring the Ubuntu terminal commands and I was wondering how to get an output of the /usr/bin files that don't contain any digits in the file name.

---

### Post by StuartN on 2009-09-27
> **shutchis said:**
> I'm exploring the Ubuntu terminal commands and I was wondering how to get an output of the /usr/bin files that don't contain any digits in the file name.

You can use **ls +([[:alpha:]])** or **ls +([a-z])** which means print any file with at least one, and with any additional number of, the alphabetic characters ([:alpha:]) or any character in the ranges a-z or A-Z (a-z is expanded to a-z and A-Z according to locale).

Other options are: alnum   alpha   ascii   blank   cntrl   digit   graph   lower print   punct   space   upper   xdigit

So you could also use **ls +([!0-9])** or **ls +([![:digit])**.

---

