---
title: "pyRenamer / Expression Help"
date: 2011-08-02
forum: General Help
---

### Post by dwitkin on 2011-08-02
Hello.  I posted this question to the pyRenamer Launchpad site and didn't get a response, so thought I'd try it here.  Any suggestions would be appreciated!


I'd like to use pyRenamer to identify and rename files with reserved characters in the file name. The files came from windows where I'm guessing the characters didn't cause problems.

For example, I want to replace the ? (question mark), ' (single quote), etc. I tried using the escape (\) character before the special character in the replace field on the substitutions tab, but for some reason I don't believe that method was identifying the special characters.

What is the correct way to identify a special / reserved character within a file name and replace it? A few examples would be helpful. Thanks in advance for your help.

---

### Post by sisco311 on 2011-08-02
Not sure about pyRenamer, but in GPRename you can use regular expressions: **['"?]** should do the trick. 

[[img]http://ompldr.org/tOXE1cA[/img]](http://ompldr.org/vOXE1cA)

If you don't mind using the perl based rename command, in bash, you can try something like:
```
reg=$'?\'\"'
rename **-n** "s/[$reg]/FOO/g" ./*
```

Invoked with the -n flag it will only show what files would have been renamed.

It will replace each question mark, single and double quote with FOO.

---

### Post by nomnex on 2013-02-06
> **dwitkin said:**
> 
For example, I want to replace the ? (question mark), ' (single quote), etc. I tried using the escape (\) character before the special character in the replace field on the substitutions tab, but for some reason I don't believe that method was identifying the special characters.

What is the correct way to identify a special / reserved character within a file name and replace it? A few examples would be helpful. Thanks in advance for your help.

Substitution tab > replace 'x' by 'y' for each character to replace or remove.
Or if you want to do it all in once, you will need to use the pattern tab

Example:
foo ? and foobar, live2007.wav

Pattern:
```
Original file: {L} ? {L} {L}, {X}
Renamed file: {1}_{2}_{3}_{4}
```Output:
foo_and_foobar_live2007.wav

---

### Post by wildmanne39 on 2013-02-06
Thanks for sharing. Thread Closed.

---

