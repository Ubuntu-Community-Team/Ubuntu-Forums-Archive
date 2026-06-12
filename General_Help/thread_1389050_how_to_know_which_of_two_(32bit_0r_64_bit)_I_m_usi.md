---
title: "how to know which of two (32bit 0r 64 bit) I m using"
date: 2010-01-23
forum: General Help
---

### Post by sushilkumar on 2010-01-23
[COLOR=Blue][B][SIZE=4]I am not Computer literate. I have installed Ubuntu on my home PC as it will avoid any virus. 

[COLOR=Red]Please tell me how to know which of two (32bit 0r 64 bit) I m using.[/COLOR]

( I have tried to find answer in this forum and else where but could not find)

Thnx in advance[/SIZE][/B][/COLOR]

---

### Post by cenzorrll on 2010-01-23
open a terminal and type:

```
uname -a
```

if you see x86_64 you're using 64bit

if it's i686 then you're 32bit.

oh, and the giant text and different colors are really annoying, you're more likely to get better help if you just use the default text.

---

### Post by sushilkumar on 2010-01-23
> **cenzorrll said:**
> open a terminal and type:

```
uname -a
```

if you see x86_64 you're using 64bit

if it's i686 then you're 32bit.

oh, and the giant text and different colors are really annoying, you're more likely to get better help if you just use the default text.
thnx. this is what i did

sushil@sushil-desktop:~$ uname -a
Linux sushil-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

it looks i am on 32 bit.
right?

---

### Post by sushilkumar on 2010-01-23
please tell how to use 64 bit in ubuntu.

---

### Post by oldos2er on 2010-01-23
Go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) , click 'Alternative download options...' 64-bit version.

---

