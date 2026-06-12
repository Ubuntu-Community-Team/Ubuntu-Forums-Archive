---
title: "Grep"
date: 2012-04-06
forum: General Help
---

### Post by hilaldm on 2012-04-06
I am tasked with reworking all pointer to pointer implementations in our company's code (big and many .c .h files). The problem that I am having is finding all those occurrences of ** (pointer to pointer) using grep. I don't seem to have success. I tried all options that I am familiar with grep (not many!). But my results have been frustrating. I get all outputs of comment lines. And there are thousands of lines of those. 
Could someone help with this? I need an expression that would result in only '**" that relate to the pointer to pointer part.

Thanks in advance.

---

### Post by codemaniac on 2012-04-06
in order to search ** in your .c files you need to escape then , because they mean something special to grep and as well as shell .

```
grep "\*\*" *.c
```

---

### Post by F.G. on 2012-04-06
I'd suggest grepping for them, as codemaniac suggests, though with the -r, -n and --include options, eg:
> grep -rn --include ".c" --include ".h" "\*\*" *
as the -r will make it recursive, and the -n will show the line numbers in the file. then use vim to edit the files, probably either using
> /\*\*
to search for the occurrences in the file or the vim sed style command with the c option, eg:
> %s/\*\*/<whatever you to change them to>/c
then vim will ask you at each occurrence of ** if you want to switch it. 

good luck with it,i 'd be interested to see what you come up with.

edit -> i just re-read your post, and i'm not sure exactly how to do this, but i would look into doing two greps and piping one into the other, changing the delimiter in one to EOF and using the backreference functionality to search for and get rid of stuff between the comment tags /* */ and then use the second grep to look for the **.

---

### Post by hilaldm on 2012-04-06
Thanks for the replies so far.
I am aware of the / escape character as * is treated as a metachar in grep and treated specially by the shell.
I used the combinations /*/*, /*/*{2,2}, recursively and others with no luck. 
I keep getting hundreds of irrelevant lines.

---

### Post by F.G. on 2012-04-06
um, shouldn't it be a backslash, eg '\' rather than a forward one, eg '/'?

---

### Post by hilaldm on 2012-04-06
> **F.G. said:**
> um, shouldn't it be a backslash, eg '\' rather than a forward one, eg '/'?

Sorry, I meant to say \ rather than / .

---

### Post by Vaphell on 2012-04-06
another way to escape metachars is to put them in enumeration brackets [] - "metacharness" doesn't work inside them

either way something like grep -E '[*]{2}' should work, what kind of irrelevant lines you get in output?

---

### Post by Bobhuber on 2012-04-07
> **hilaldm said:**
> I am tasked with reworking all pointer to pointer implementations in our company's code (big and many .c .h files). The problem that I am having is finding all those occurrences of ** (pointer to pointer) using grep. I don't seem to have success. I tried all options that I am familiar with grep (not many!). But my results have been frustrating. I get all outputs of comment lines. And there are thousands of lines of those. 
Could someone help with this? I need an expression that would result in only '**" that relate to the pointer to pointer part.

Thanks in advance.
If you have a lot of files and want to replace ** with the same variable or string in all of the files try using rpl ( RPL >intelligent recursive search/replace utility) found in the synaptic package manager. It has saved me many hours of work.
rpl -R -e -f -x'.c' '**' '<newstring>' /sourcedirectory 
-- This will find and replace all occurrences of ** on all files with a .c extension in your source directory with a string that you define (newstring). It will also work thru multiple subdirectories in the source if you have any.

---

