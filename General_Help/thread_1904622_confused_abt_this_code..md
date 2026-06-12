---
title: "confused abt this code."
date: 2012-01-05
forum: General Help
---

### Post by arun_nr on 2012-01-05
DDRB |= (1 << 0)



can any one help me out with this.im newbie to coding.:confused:

---

### Post by Vaphell on 2012-01-05
[http://h30097.www3.hp.com/docs/base_doc/DOCUMENTATION/V40F_HTML/AQTLTBTE/DOCU_059.HTM](http://h30097.www3.hp.com/docs/base_doc/DOCUMENTATION/V40F_HTML/AQTLTBTE/DOCU_059.HTM)

it performs bitwise OR (1 in any argument sets 1 in the result) of DDRB and 1 ( 1 shifted to the left by 0 bits is still 1) and assigns the result to DDRB

```
00**1**0**1**0**1**0
**11**000**1**00
--------- OR
11101110

3 << 2
3: 00000011
   00001100 = 12

```
left-shifting is pretty much equivalent to multiplying by 2^n (there are overflows but whatever)

in general it returns DDRB if DDRB is odd and DDRB+1 if DDRB is even

---

