---
title: "lib*.so numbers"
date: 2006-01-26
forum: General Help
---

### Post by mvaniersel on 2006-01-26
This is a very general question: why do many libraries carry a series of numbers after their name? For example: /usr/lib/libodbc.so.1.0.0. If you do ls /usr/lib/lib* you see lots of examples.

I ask this, because recently I installed a program (unixodbc), it came with libodbc.so.1.0.0. Then I tried installing another program (the perl DBD::ODBC module if you must know) which didn't work at first because it was looking for libodbc.so (without the trailing numbers). It took me ages to find out that this was the problem, but when I created a link from libodbc.so to libodbc.so.1.0.0 the problem was solved.

I'm wondering if that is the proper solution, though. So that's why I ask, what do those trailing numbers mean?

---

### Post by public_void on 2006-01-26
The trailing numbers are versions of the software. It so it is easier to kept track of the different versions. It would be hard to distinguish between two packages with the same name, but one had been updated, you wouldn't know which one. The higher the numbers the more recent the software will be.

---

### Post by mvaniersel on 2006-01-27
So creating a link from libodbc.so to libodbc.so.1.0.0 was the right solution? Or is it a bug that there wasn't a link in the first place? Or is it a bug of DBD::ODBC to expect libodbc.so to be there?

---

