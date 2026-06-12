---
title: "Bash script help - for loop - replacing strings"
date: 2011-08-16
forum: General Help
---

### Post by rkillcrazy on 2011-08-16
I'm not overly great with bash scripting.  I do more batch file stuff for Windows than anything else but I'm trying to branch out a bit.  (Frankly, I'd love to do this in Ruby but I'm not there yet...)  Maybe I'm not using the correct terminology and that's why my searches are coming up useless...

Anyway, I have a script that does some work with HandBrake.  Although it deals with HandBrake, I think the issue is not with HandBrake itself.

The issue:
I had a simpler script which worked fine but it would give me an MP4 with a file name of: **Some Movie Name.iso.mp4** and it would still play but I wanted to get rid of the **.iso** in the file name.  I also wanted to drop it into another directory during the encoding.  That's why you see a **$source** & a **$destination** variable.

**handbrake.sh**
```

#!/bin/bash

source=/media/data/movies
destination=/media/data/movies/mp4s

for file in $source/*; do
        [COLOR="Red"]mp4file = ${file/$source/$destination};
        mp4file = ${mp4file/.iso/.mp4};[/COLOR]
        HandBrakeCLI --preset="High Profile" --subtitle scan --subtitle-forced --input "$file" --output "$mp4file";
done

```

Again, I'm not great with this stuff so be gentle. :)  I think my issue lies inside the red area I've highlighted but I could be totally wrong.

---

### Post by Vaphell on 2011-08-16
variable expansion won't work there ($source, $destination), bash built-in substitution works with fixed strings and patterns, not variables.
simply extract the file name alone and glue it together with $source/destination outside the braces

```

a=/a/b/c/d.e
dest=/some/destination/

$ echo ${a##*/}
d.e
$ echo "$dest${a##*/}"
/some/destination/d.e

```

---

### Post by AlphaLexman on 2011-08-16
> **rkillcrazy said:**
> **handbrake.sh**
```

#!/bin/bash

source=/media/data/movies
destination=/media/data/movies/mp4s

for file in $source/*; do
        [COLOR=Red]mp4file = ${file/$source/$destination};
        mp4file = ${mp4file/.iso/.mp4};[/COLOR]
        HandBrakeCLI --preset="High Profile" --subtitle scan --subtitle-forced --input "$file" --output "$mp4file";
done

```
You are correct about the text in [COLOR=Red]red[/COLOR]. The most obvious error is the **whitespace** around the eqaul signs!
EDIT: Deleted bad code
Beat by Vaphell. I also missed the variable expansion error. Although the whitespace I pointed out is still valid.

---

### Post by Vaphell on 2011-08-16
lol, i didn't notice the whitespaces :D

---

### Post by rkillcrazy on 2011-08-16
> **AlphaLexman said:**
> You are correct about the text in red. The most obvious error is the whitespace around the eqaul signs!
Try...

Beat by Vaphell. I also missed the variable expansion error. Although the whitespace I pointed out is still valid.

I read Vaphell's response and then yours.  Just for grins, I removed the whitespace and reran the script.  I figured that was the easiest change to make and I just was curious of what kind of error I'd get - hoping to better understand the whole expansion idea...  It's going through the motions right so it looks like that worked!  Was there a code change that makes the expansion of variables possible now?

---

### Post by Vaphell on 2011-08-16
i was wrong and that's all there is to it :) i always assumed that variable identifier is expanded but the rest of stuff in braces is not. Good to know :)

---

### Post by rkillcrazy on 2011-08-16
It's okay; I've been wrong once or twice in my life too. ;)

---

### Post by AlphaLexman on 2011-08-16
@Vaphell: FWIW, our error stated as ''variable expansion' was actually 'pattern substitution' ...from the bash man-page...

```
       ${parameter/pattern/string}
              Pattern  substitution.   The  pattern  is  expanded to produce a pattern just as in pathname expansion.
              Parameter is expanded and the longest match of pattern against its value is replaced with  string.   If
              pattern  begins with /, all matches of pattern are replaced with string.  Normally only the first match
              is replaced.  If pattern begins with #, it must match at the beginning of the expanded value of parame&#8208;
              ter.  If pattern begins with %, it must match at the end of the expanded value of parameter.  If string
              is null, matches of pattern are deleted and the / following pattern may be omitted.  If parameter is  @
              or  *, the substitution operation is applied to each positional parameter in turn, and the expansion is
              the resultant list.  If parameter is an array variable subscripted with @ or *, the substitution opera&#8208;
              tion is applied to each member of the array in turn, and the expansion is the resultant list.

```Actually I was partially wrong too!! 

Learned.

---

