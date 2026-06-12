---
title: "Convert ascii to binary?"
date: 2012-09-17
forum: General Help
---

### Post by PDA1 on 2012-09-17
.

---

### Post by ranger1021994 on 2012-09-17
See if this helps

[http://manpages.ubuntu.com/manpages/gutsy/man1/ascii2binary.1.html](http://manpages.ubuntu.com/manpages/gutsy/man1/ascii2binary.1.html)

---

### Post by PDA1 on 2012-09-18
.

---

### Post by Wim Sturkenboom on 2012-09-18
xxd ?

```

wim@wim-desktop:~$ echo "UBUNTU" |xxd -p
5542554e54550a
wim@wim-desktop:~$ echo "UBUNTU" |xxd
0000000: 5542 554e 5455 0a                        UBUNTU.
wim@wim-desktop:~$ echo "UBUNTU" |xxd -g1
0000000: 55 42 55 4e 54 55 0a                             UBUNTU.
wim@wim-desktop:~$ echo "UBUNTU" |xxd -b
0000000: 01010101 01000010 01010101 01001110 01010100 01010101  UBUNTU
0000006: 00001010                                               .
wim@wim-desktop:~$ 

```

---

### Post by Dave_L on 2012-09-18
And you can use the -n option with 'echo' to suppress the linefeed character:

> $ echo -n Ubuntu |xxd -b
0000000: 01010101 01100010 01110101 01101110 01110100 01110101  Ubuntu

---

### Post by Vaphell on 2012-09-18
...or use printf which is 1 char shorter than echo -n! ;-)

---

### Post by PDA1 on 2012-09-18
Excellent!

Thank you all.

---

