---
title: "Need regular expression help to match * up to newline and special sequence"
date: 2009-11-15
forum: General Help
---

### Post by MountainX on 2009-11-15
I have a python script with the following regex:

```
regExpression = r'(?P<comment>[^<]*)'
```

It is used to parse text like this:
```
testing blah blah blah can include anything such as < or , or 123, etc.
<CR>
```

It has 2 problems:
1. If the comment contains "<" it doesn't work correctly.
2. The comment includes the trailing newline, which is incorrect.

So what I need to change is that the regex should parse anything and everything up to and before a **newline** (Win or Linux) followed by **<CR>**.

Can anyone suggest a regex for doing this? Thanks.

---

### Post by dcstar on 2009-11-15
> **MountainX said:**
> 
........
So what I need to change is that the regex should parse anything and everything up to and before a **newline** (Win or Linux) followed by **<CR>**.

Can anyone suggest a regex for doing this? Thanks.

[http://www.regular-expressions.info/anchors.html](http://www.regular-expressions.info/anchors.html)

---

### Post by MountainX on 2009-11-15
Here's what I ended up doing.

```
regExpression = r'(?P<comment>.*?)(?=\s*^<CR>)'
```And to make that work on the last line in the file, I did this:
```
input += "\n<CR>"
```So that the input data is guaranteed to end with the terminating sequence the regex expects.
I also used:
```
re.MULTILINE|re.DOTALL
```

I had tried the \Z end of string anchor, but I wasn't able to make it work. However, if my approach can be improved, I would love to do it differently.

---

