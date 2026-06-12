---
title: "Replacing a string in microsoft word files from the command line."
date: 2011-04-20
forum: General Help
---

### Post by quickk on 2011-04-20
Hy everyone, 

   I am making a bunch of participation certificates for an elementary school math contest.   The certificate is written up using Microsoft Word.  I would like to write a script that replaces the name in the certificate with another name.

I've tried the following command to replace "Jane" with "Brad"

```
sed 's/Jane/Brad/g' test.doc > test2.doc
```

which works fine as long as the two names are of the same length.   The problem is that the word document is a binary file, and if the strings being swapped are of different length, the output file gets corrupted.  

Is there any way to do the swap without messing up the binary file?   

I suppose that I could have a really long original name, and pad the name being swapped in with the appropriate number of spaces, but I don't know how to automatically do this while keeping the name centered in the document.

---

### Post by DaithiF on 2011-04-20
Hi, save the word doc first as an xml file rather than in the binary ms word format.  Once you're dealing with plain text you can apply whatever transforms you need using sed etc., and on re-opening Word will be happy with the updated files.

---

### Post by quickk on 2011-04-20
Brilliant!  Thanks!

---

