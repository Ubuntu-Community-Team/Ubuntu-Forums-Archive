---
title: "Calibre 0.7.10 unhandled exception error"
date: 2010-08-09
forum: General Help
---

### Post by borowitch on 2010-08-09
Hello,

I installed Calibre e-library software (0.7.10 ver.) on Ubuntu 10.04. When I start program I have an error message "unhandled exception" as following;

```
ERROR: ERROR: Unhandled exception: <b>TypeError</b>:arguments did not match any overloaded call:
  QDate(): too many arguments
  QDate(int, int, int): argument 1 has unexpected type 'unicode'
  QDate(QDate): argument 1 has unexpected type 'unicode'

Traceback (most recent call last):
  File "/home/kovid/build/calibre/src/calibre/gui2/library/models.py", line 657, in data
  File "/home/kovid/build/calibre/src/calibre/gui2/library/models.py", line 558, in datetime_type
TypeError: arguments did not match any overloaded call:
  QDate(): too many arguments
  QDate(int, int, int): argument 1 has unexpected type 'unicode'
  QDate(QDate): argument 1 has unexpected type 'unicode'

```

What's the problem? How can I solve it?

---

