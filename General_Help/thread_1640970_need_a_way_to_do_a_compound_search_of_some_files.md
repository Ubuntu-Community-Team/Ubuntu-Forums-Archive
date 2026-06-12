---
title: "need a way to do a compound search of some files"
date: 2010-12-08
forum: General Help
---

### Post by PaulHuffman on 2010-12-08
I'm trying to look through a big folder of air photos to see if there are some world files that have duplicate coordinates.  I want to find *.jgw files that have 123 in line 5 and 456 in line 6.  I first thought grep could do this for me but grep 123 *.jgw|grep 456 finds only files where 123 and 456 are on the same line.  Is there a sed trick for this?

---

### Post by KeyserSoze93 on 2010-12-08
```

for i in *; do perl -lane '$m = 1 if $. == 4 && m/236/;print "$ARGV" if $m && $. == 5 && m/512/;' $i; done

```

---

### Post by PaulHuffman on 2010-12-08
Interesting idea, dropping into perl. This worked for me after changing the line number to look in. I used 
```
for i in *.jgw; do perl -lane '$m = 1 if $. == 5 && m/1585152/;print "$ARGV" if $m && $. == 6 && m/516095/;' $i; done
```

which yielded 00084_00072_m.jgw, contents of which are 
 ```
                  1.50000000000000 
                   0.00000000000000 
                   0.00000000000000 
                  -1.50000000000000 
             1585152.75000000023283 
              516095.24999999953433 

```

But unfortunately, I didn't find a file with the same coordinates, so I have to keep looking for an explanation of why a photo is getting positioned in the wrong place.

---

