---
title: "[tcsh] Accessing variable named by the value of another variable"
date: 2011-10-19
forum: General Help
---

### Post by xqwzts on 2011-10-19
Hi,

The topic may sound complicated so I will try to explain it.

Let's say I have defined 3 variables:
```
set a = 1
set b = 2
set c = 3
```Now I would like to print their values in the loop:
```

foreach i ( a b c)
    # print value of the variable named by the value of $i
end.
```How can I do it? In bash it looks like this:

```
 for i in a b c
  do
      echo ${!i}
  done
```But doesn't work for tcsh.

I will be very grateful for any clues.

---

### Post by erind on 2011-10-19
Use *eval*:

```
foreach i ( a b c )
? eval echo \$$i
? end
1
2
3
```

Unless you have to, *csh *usage is not recommended.

[http://www.grymoire.com/Unix/CshTop10.txt](http://www.grymoire.com/Unix/CshTop10.txt)

---

### Post by xqwzts on 2011-10-19
Thanks a lot!

About using csh - university teacher wants us to write every script in both languages (bash and tcsh), so I have no choice.

---

### Post by xqwzts on 2011-10-19
One more question - how can I check if a variable with a name given by another variable is set? 

I mean something like:

```
foreach i ( a b c )
    eval if ( \?$$i )then
           echo "is set"
        else echo "not set"
        endif
 end.
```But  it doesn't work.

---

### Post by erind on 2011-10-19
You can do something along the lines of:

```
foreach i ( a b c )
 eval set x=\$$i
 if ($?x) then
   echo "is set"
 else echo "not set"
 endif
end
```As I said I don't use csh, so this is the best I had to come up with.

---

