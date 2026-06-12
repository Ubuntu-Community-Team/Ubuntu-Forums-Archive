---
title: "in vi, how to replace h-1 to h_{-1}"
date: 2012-02-17
forum: General Help
---

### Post by mike_kzc on 2012-02-17
Dear all,

Basically, I am trying replace h-1 to h_{-1} in vi. but if i use :

:1,$/h-1/h_{-1}/g

it gives this:

E481: No range allowed 

Please help.

thanks in advance.

Mike

---

### Post by wolfen69 on 2012-02-17
[http://www.kingcomputerservices.com/unix_101/search_and_replace_with_vi_part_1.htm](http://www.kingcomputerservices.com/unix_101/search_and_replace_with_vi_part_1.htm)

---

### Post by papibe on 2012-02-17
You had the range and the patterns correct, but you were missing the actual command. Try this:
```
:1,$**[COLOR="Red"]s[/COLOR]**/h-1/h_{-1}/g
```
Alternately, you can use '%' instead of 1,$
```
:%**[COLOR="Red"]s[/COLOR]**/h-1/h_{-1}/g
```
Hope it helps.
Regards.

---

### Post by mike_kzc on 2012-02-17
> **wolfen69 said:**
> [http://www.kingcomputerservices.com/unix_101/search_and_replace_with_vi_part_1.htm](http://www.kingcomputerservices.com/unix_101/search_and_replace_with_vi_part_1.htm)


Thanks, it works. I am using:
:%s/h-1/h$_{-1}$/

---

### Post by mike_kzc on 2012-02-17
> **papibe said:**
> You had the range and the patterns correct, but you were missing the actual command. Try this:
```
:1,$**[COLOR=Red]s[/COLOR]**/h-1/h_{-1}/g
```Alternately, you can use '%' instead of 1,$
```
:%**[COLOR=Red]s[/COLOR]**/h-1/h_{-1}/g
```Hope it helps.
Regards.

thanks, it works.

---

