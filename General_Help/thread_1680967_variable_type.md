---
title: "variable type"
date: 2011-02-03
forum: General Help
---

### Post by ntesla123 on 2011-02-03
When I try to extract a string using curl and assign it to a variable, it doesn't behave like a string. E.g. it's not possible to concatenate it with another string. 

How do I make it behave like a string?

---

### Post by ntesla123 on 2011-02-03
If I e.g. have the variable sid, the command echo $sid returns

3a060fccf88b17a690dcfdf07a132dc8

If I type echo $sid"benjamin" , this returns:

benjaminf88b17a690dcfdf07a132dc8

and not 

3a060fccf88b17a690dcfdf07a132dc8benjamin

---

### Post by gmargo on 2011-02-03
```

$ sid=3a060fccf88b17a690dcfdf07a132dc8
$ echo $sid"benjamin"
3a060fccf88b17a690dcfdf07a132dc8benjamin
$ echo "${sid}benjamin"
3a060fccf88b17a690dcfdf07a132dc8benjamin

```It seems to work for me.  You might try the "${sid}" form.  You might also try echoing $sid through a hex dumper like **xxd(1)** just to see if you've got any funny characters in the string that may interfere (like a CR or NL).

---

### Post by ntesla123 on 2011-02-03
I found out it got like this because it's awk output.

awk '{print $0}'

But I still don't know how to make the awk output an ordinary string, that can be concatenated.

---

### Post by gmargo on 2011-02-04
You almost certainly have a carriage return in your string, especially if you were processing web pages, which are by default DOS formatted.  That's why I suggested running it through **xxd(1)**.

I was able to duplicate your results by starting with a DOS format file.  You'll have to take an extra step to remove that carriage return either from awk's input or awk's output (or alter awk's record separator to account for it.)

One way:
```

awk 'BEGIN {RS="\n|\r\n"} {print $0}'

```

---

