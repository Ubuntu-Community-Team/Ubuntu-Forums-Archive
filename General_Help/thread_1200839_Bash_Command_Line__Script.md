---
title: "Bash Command Line / Script"
date: 2009-06-30
forum: General Help
---

### Post by josgau33 on 2009-06-30
Hello all,

This is my first post on the forum, so please be forgiving :-)

I am having difficulty figuring out what combination of commands I can use to extract data I need from a file. So far, I have used

    grep **RPF** *filename* 

to display all of the lines that have the information I need in them. The result looks like this:

Output tags RPF
RPF  8 1417  86400.000  1         0.000000         0.000000         0.000000       0.000000     0.000000   0.0 10 0.00e+00  -1  -3  -9 -11 -14 -18 -19 -22  28 (-3) NV
RPF  1 1417  86430.000  8  **-2296299.350487**  **-1484805.375196**   **5743082.756986**  128930.745748     0.725932   5.5 6 2.55e-09  -1   3   9  11  14  18  19  22  28 (0) V
RPF  1 1417  86460.000  8  **-2296300.521381**  **-1484804.643129**   **5743085.493687**  128932.398723     0.644512   5.4 6 4.45e-09  -1   3   9  11  14  18  19  22  28 (0) V
RPF  1 1417  86490.000  8  **-2296299.720055**  **-1484805.209491**   **5743083.925224**  128931.601327     0.859086   5.4 6 1.12e-08  -1   3   9  11  14  18  19  22  28 (0) V
RPF  1 1417  86520.000  8  **-2296298.711626**  **-1484805.536968**   **5743082.779245**  128930.690659     0.934328   5.3 6 3.93e-09  -1   3   9  11  14  18  19  22  28 (0) V

[the output goes on like this for a long time]

where the first RPF is the first line, the second RPF the second line, the third RPF the third line, etc.

I have made the data I want to extract bold above. As you can see, each data point is clustered around the same point, and I do not expect it to deviate more than 10000 units from the average of the bold points. I was thinking that I might be able to use 'awk' or 'sed', but I cannot seem to figure out what command I should use.

It seems to me that since all the data points are clustered around the average, I should be able to test for the values that meet this condition, and extract those values accordingly.

Does anybody have any ideas?

Thanks!

---

### Post by decoherence on 2009-06-30
you're right... awk is the one to use. try this

```
grep **RPF** *filename* | awk '{print $6" "$7" "$8}'
```

$6 refers to the sixth field, where any whitespace (spaces, tabs, newlines) is the field delimiter. awk is very literal minded, hence the need to specify spaces (in quotes) otherwise you'd get each field strung together with no spaces.

hope that helps!

PS Welcome! :D

---

### Post by asmoore82 on 2009-06-30
another option is `cut`
```
grep ^RPF *filename* | cut -d" " -f6-8
```
the '^' tells `grep` to only match at the beginning of each line,
the '-d" "' tells `cut` to use a space as the field delimiter,
the '-f6-8' tells `cut` to show fields 6 *through* 8

`cut` has a very useful sister command `paste` that doesn't do what you might expect:

`cut` could make a text file out of each field like this:
```
grep ^RPF *filename* | cut -d" " -f6 > 6.txt
grep ^RPF *filename* | cut -d" " -f7 > 7.txt
grep ^RPF *filename* | cut -d" " -f8 > 8.txt
```

and then `paste` could make a csv out of them like this:
```
paste -d, 6.txt 7.txt 8.txt > rpf.csv
```

^it's sort of like distributing a database across multiple text files -
and `paste` is the glue that can relate the *nth* line of each file together.

Note: `cut` and `paste` will both default to TAB characters as the delimiter.

---

### Post by decoherence on 2009-06-30
i knew about cut but not about paste! Very handy; thanks!

---

### Post by kaibob on 2009-06-30
> **decoherence said:**
> you're right... awk is the one to use. try this

```
grep **RPF** *filename* | awk '{print $6" "$7" "$8}'
```

$6 refers to the sixth field, where any whitespace (spaces, tabs, newlines) is the field delimiter. awk is very literal minded, hence the need to specify spaces (in quotes) otherwise you'd get each field strung together with no spaces.

hope that helps!

PS Welcome! :D

With awk, you may want to consider eliminating grep:

```
awk '/RPF/ { print $6" "$7" "$8 }' file
```

---

### Post by Slim Odds on 2009-06-30
Getting to know the multitude of *nix command to use for scripting is very nice.

If my script starts to get a little complicated, I quickly just switch to writing a Ruby "script". Ruby is extremely handy for stuff like this.

---

### Post by t4thfavor on 2009-06-30
I helped someone with something like this usong sed yesterday, the results were satisfactory.

I will look for the thread, and report back.

EDIT:
There it is
[http://ubuntuforums.org/showthread.php?t=1200034](http://ubuntuforums.org/showthread.php?t=1200034)

On second visit, the above way seems more practical. and easier. I wish I had grown up in the era of these tools so that I could have a better understanding of them.

---

### Post by josgau33 on 2009-07-01
Thanks guys!

All of your suggestions were great. I tried them all out and I have a better understanding of all of these tools now. I appreciate your help!

---

