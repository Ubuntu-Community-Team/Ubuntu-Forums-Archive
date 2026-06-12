---
title: "bashrc special characters"
date: 2011-10-27
forum: General Help
---

### Post by MaindotC on 2011-10-27
In someone's bashrc they have this entry which is causing a problem:
```
echo -e '\033%8'
```
I've googled that the \033 is an escape character.  What does the '%8' represent?

---

### Post by MaindotC on 2012-03-03
[SIZE="4"]What does the '%8' represent?[/SIZE]

---

### Post by Khayyam on 2012-03-03
psudocode ... it doesn't mean anything ... they may have been trying to turn the bell off as "8" is the ascii code for bell, who knows.

What you have is:

echo -e ....... interpret escapes
\33 .............. octal for escape
% ................ an escaped char
8 .................. the invisible man wearing spectacles

They may have wanted this (set bell off):

```
echo -e "\33[11;0]"
```best ... khay

---

