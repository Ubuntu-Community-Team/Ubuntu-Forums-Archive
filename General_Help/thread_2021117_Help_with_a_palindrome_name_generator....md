---
title: "Help with a palindrome name generator..."
date: 2012-07-08
forum: General Help
---

### Post by hopelessone on 2012-07-08
Hi,

Anyone made a palindrome alphabet sequence generator?

I can find palindrome generators, but none with an alphabet sequence generator.

e.g.
select 2 alphabet letters
aa
ab
ac
.....
yz
zz

Output looks like:
aaa
aba
ac
yzy
zzz

e.g. select 3 alphabet letters
aaa
aab
.....
yzz
zzz

Output looks like:
aaaaa
aabaa
...
yzzzy
zzzzz

Anyone made one? ideas?
Thanks

---

### Post by Vaphell on 2012-07-09
it's trivial

```
#!/usr/bin/env python

import itertools
import sys

if __name__ == '__main__':

  l = int( sys.argv[1] )
  if len(sys.argv) > 2:
    a = sys.argv[2]
  else:
    a = 'abcdefghijklmnopqrstuvwxyz' 
  
  print "alphabet:", a
  print "length: %d (%d)" % ( l, l*2-1 ) 

  for i in itertools.product(a,repeat=l):
    s = "".join(i)
    print s+s[-2::-1]
```

usage:
```
./palindrome.py 2
```
or
```
./palindrome.py 2 abc
```
to define set of chars

---

