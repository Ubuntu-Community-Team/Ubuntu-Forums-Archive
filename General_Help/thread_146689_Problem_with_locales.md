---
title: "Problem with locales"
date: 2006-03-18
forum: General Help
---

### Post by Jonas_Henricsson on 2006-03-18
I have used Ubuntu for a very short period of time. I have a problem with local letters  (å, ä, ö) when I send e-mails. The letters are replaced by nonsense symbols. 

I also get the following problem when I tried to run monadjust:

jonas@ubuntu:~/Desktop/test/philmon_v0.2$ ./monadjust
Qt: Locales not supported on X server
qstring_to_xtp result code -2
Segmentation fault

Does anyone have any ideas on how to solve these problems?

Thank you for your reply!

/Jonas

---

### Post by adamkane on 2006-03-18
You need to state which encoding, UTF-8 or ISO-8859-1, that your system is using, and then state which applications aren't displaying correctly.

If you haven't made any changes, then you are using UTF-8.

---

### Post by Jonas_Henricsson on 2006-03-19
I use this:

ISO language, territory, currency  codes and their translations
This package provides the ISO-639 Language code list, the
 ISO-4217 currency list, the ISO-3166 Territory code list,
and ISO-3166-2 sub-territory lists.

Should I get the other one?

/Jonas

---

