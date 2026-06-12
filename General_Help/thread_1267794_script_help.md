---
title: "script help"
date: 2009-09-16
forum: General Help
---

### Post by veeseekay on 2009-09-16
Hi folks,

I have a file with text like this :

<!--
    some text some text some text
    <test>test</test>
-->

I need to replace this entire piece of text to something else.
I have tried using sed, perl, tr, etc...but unsuccessful.

any pointers will be of great help!

cheers!

---

### Post by keplerspeed on 2009-09-16
Should be able to do this with bash. For example:

#! /bin/bash
echo text > file.txt


So it depends on what your trying to replace. Are you wanting to replace just the line: "some text some text some text" or the entire thing?

---

### Post by lvlint67 on 2009-09-16
> **veeseekay said:**
> Hi folks,

I have a file with text like this :

<!--
    some text some text some text
    <test>test</test>
-->

I need to replace this entire piece of text to something else.
I have tried using sed, perl, tr, etc...but unsuccessful.

any pointers will be go great help!

cheers!
This is the perfect spot for a regex... I'm rusty on them so maybe you could research it a bit or someone else could answer this?

---

### Post by DaithiF on 2009-09-16
using sed, something like this (this assumes that the 'some text some text some text line' can vary):
```
$ sed '/^<!--/{N;N;N;s/^<!--\n.*\n<test>test<\/test>\n-->/replace/}' 

```

for a testfile containing 
```
firstline
<!--
some text some text some text
<test>test</test>
-->
lastline

```

gives:
```
firstline
replace
lastline

```

---

### Post by veeseekay on 2009-09-17
Thnx DaithiF, your soln fixes my issue.

thnx all for your comments..

cheers!

---

