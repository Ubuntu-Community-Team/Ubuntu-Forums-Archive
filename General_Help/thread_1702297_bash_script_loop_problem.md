---
title: "bash script loop problem"
date: 2011-03-07
forum: General Help
---

### Post by ianc1 on 2011-03-07
I have a bash script issue.  My script has a list of variables in it defined as VARIABLE="var1 var2 var3" etc.  var1, 2, 3.  The script is written as:

VARIABLE= "var1
var2
var3"

var1 contains spaces ie "var1a var1b"

Now when I run the script the first loop run with var1a the second run through the loop with var1b then the next loop on to var2.

How do I get it to treat var1a and var1b as a single variable?  I've tried escaping the space with \ and also using quotes '  ' around var1a and var1b.  Any ideas, I'm sure its dead simple?  I want to avoid replacing the space with _ or similar.

Cheers

---

### Post by AlphaLexman on 2011-03-07
> **ianc1 said:**
> VARIABLE="var1 var2 var3"
Should be:
```
VARIABLE="[COLOR="Red"]$[/COLOR]var1 [COLOR="red"]$[/COLOR]var2 [COLOR="red"]$[/COLOR]var3"
```
In bash, you set VARIABLE **without** a leading '$', but return the value **with** a leading '$', like this "$VARIABLE".

Now, if you were just being lazy, and truly have dollar signs preceeding your variable names, and just not typing the full variable substitution, shame on you! You will get better results if you post full information with no shortcuts! Otherwise, advise might be misguided or misdirected. 

Sorry for the rant, I am in a bit of lecture mood.

Although I know the solution, I will only guide you to look into array variables.

Good luck.

---

### Post by ianc1 on 2011-03-07
Excellent most helpful I now now a bit more bash on, slowly getting there.  Although I have to find out why the following works if I run "bash scriptname" but not if I run "sh scriptname"

#!/bin/bash
array=("one" "two" "three")
echo ${array[0]}

This gives "one" if I run with th bash command but unexpected "(" error if I run with sh command.

Thanks

---

### Post by ianc1 on 2011-03-07
Actually reading your post again has confused me.

> VARIABLE="[COLOR=Red]$[/COLOR]var1 [COLOR=red]$[/COLOR]var2 [COLOR=red]$[/COLOR]var3"

I thought the assignment should be VARIABLE="var1 var2 var3"

and in use I should employ $var1 etc ie the dollar sign, so to print on the screen i'd do echo $var1.

The array has got around my issue but this $ placement and the bash/sh is still nigling at me.  I've just found out sh is running dash - more reading.

Thanks again.

---

### Post by AlphaLexman on 2011-03-07
> **ianc1 said:**
> if I run "bash scriptname" but not if I run "sh scriptname"
You are invoking two different shells, **bash** and **sh** are not the same, try sourcing the file with dot '.' space ' ' /path/filename instead of invoking another shell, like this:
```
. ~/bin/scriptname
```
Sourcing will work even without a #! shebang at the beginning of the code.

---

### Post by tordeu on 2011-03-07
> **ianc1 said:**
> Actually reading your post again has confused me.


I think you confused him by naming your actual arguments var1, var2 and var3, so the though that var1-3 are in fact variables.

One thing you could do is just avoid using VARIABLE and put the list directly in the for loop:

```

for i in "var1" "var2" "var3"
do
  ...
done

```

---

### Post by ianc1 on 2011-03-09
Thanks all, great information and a great help as always.

---

