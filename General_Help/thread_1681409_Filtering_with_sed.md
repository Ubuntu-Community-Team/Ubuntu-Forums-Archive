---
title: "Filtering with sed"
date: 2011-02-04
forum: General Help
---

### Post by x5x_tim on 2011-02-04
I've got a large file with the following markup:
typenumber<tab>- ##x<tab>($$x)

I wanna print out a list of lines where ## does not match $$.
Preferrably with a distinction between ##>$$ and $$>##

I think I need to use sed for this, but I am a complete newbie with sed.

Thanks in advance,

Tim

---

### Post by DaithiF on 2011-02-04
Hi,
sed probably isn't the right tool for the job here, though you could use it at a pinch

e.g. for a testfile containing:
```
$ cat testfile
ab000   -50x    (50x)
ab100   -50.0x  (50x)
ab200   -20x    (25x)
ab300   -15x    (15x)
ab400   -1.00x  (10x)
ab500   -75x    (500x)

```

this sed command will delete lines where the figures in parentheses match
```
$ sed '/^.*\t-\([0-9.]\+\)x\t(\1x)/d' testfile
ab100   -50.0x  (50x)
ab200   -20x    (25x)
ab400   -1.00x  (10x)
ab500   -75x    (500x)

```

but note that this is a naive text match, so that 50.0 does not match with 50.  Maybe thats not a problem for you.

Slightly better, though still a little awkward in this case, is awk.  This allows you to do numeric rather than string comparisons (ie. so that 50.0 is matched with 50), and allows you to differentiate in the output where field1 > field2 or vice versa.
create filter.awk something like this:
```
function f1(val)
{
        r = gensub(/-([0-9.]+)x/, "\\1", "g", val);
        return strtonum(r)
}
function f2(val)
{
        r = gensub(/\(([0-9.]+)x\)/, "\\1", "g", val);
        return strtonum(r)
}
{
        val1=f1($2);
        val2=f2($3);
        if(val1 > val2)
                printf "%s > %s: %s\n", val1, val2, $0;
        else if( val1 < val2 )
                printf "%s < %s: %s\n", val1, val2, $0;
}

```

then awk -f filter.awk testfile gives:
```
20 < 25: ab200  -20x    (25x)
1 < 10: ab400   -1.00x  (10x)
75 < 500: ab500 -75x    (500x)
```

But maybe best of all would be to do it in a higher level scripting language like python or perl.

---

