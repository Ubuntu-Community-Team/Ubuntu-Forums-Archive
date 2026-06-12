---
title: "Plain text formatting"
date: 2009-09-07
forum: General Help
---

### Post by jfitzpat on 2009-09-07
Hi,

Im having trouble with plain text formatting. With Both Ubuntu and Fedora. Here is an explanation:

If I create a text file in linux and type some stuff in it as such:

```
1
2
3
```

it will look fine in linux but look as such in windows:

```
123
```

If I do the same first example in Windows and then open it in linux, I get the following:

```
1

2

3
```

This is actually problematic for me as I am writing programs that use plain text files, so line format must be precise.

Are there any solutions available?

Thank you,
-Jason

---

### Post by ddrichardson on 2009-09-07
Windows handles carriage returns differently, there are commands to change it - unix2dos and dos2unix. I *think *the package is tofromdos but I could be wrong.

---

### Post by credobyte on 2009-09-07
Use Notepad++ - it handles line breaks very well ( unlike Notepad or any other Micro-product ).

---

### Post by cybergalvez on 2009-09-07
like ddrichardson said windows and linux use different end-of-line characters.  If you are writing a program that needs to read a text file and EOL characters are important (which they usually are as you've already noticed) you are going to have to check what platform you are on and fix the EOL for that platform.  What you have to do is know who made your text file and who uses it.  I had a similar problem, I wrote a program what crated a text config file for a windows program.  My program ran on either on windows or linux and the windows program worked well in wine, So when I ran my program on Linux I had to make sure I used the right EOF character so that the windows program would read it correctly.  On Windows it just worked.  My program was written in python, so when I was in linix I just make sure to end lines with /r/n, on windows I would just end with /n (Python actaully took care of using the right EOL in windows.

Hope this helps

---

### Post by DaithiF on 2009-09-07
and just for sake of illustration:
heres your file with unix line endings dumped in hex, so you can see the line-endings
```
hexdump -C testfile
```
00000000  31 [COLOR=Red]0a[/COLOR] 32 [COLOR=Red]0a[/COLOR] 33 [COLOR=Red]0a[/COLOR]                                 |1.2.3.|
The '0a' characters are the newlines, where 0a = the hex representation of ascii character code 10, also known as newline or '\n'

```
unix2dos testfile
use unix2dos command to convert it to dos/windows line endings:

```
and now dump the file in hex again to see the difference:
```
hexdump -C testfile

```
00000000  31 [COLOR=Red]0d 0a[/COLOR] 32[COLOR=Red] 0d 0a [/COLOR]33 [COLOR=Red]0d  0a[/COLOR]                       |1..2..3..|
now the line endings are 0d 0a pairs, where 0d = hex representation of ascii character 13, also known as carriage return, or '\r'

the unix2dos | dos2unix commands just add or delete the extra '\r' character that dos/windows requires.

but if you're regularly using the same files from both environments then as credobyte says you really need an editor that can handle both filetypes without bugging you.  My personal preference is vim, which on windows you can run in graphical form as gVim, or as plain vim on Cygwin.

---

### Post by jfitzpat on 2009-09-08
Thanks!

I just found out that all the problems I was having during my whole development were because of this. Pasting my config file into Notepad2 gave me a good idea of which lines were causing problems and now everything runs great.:)

Thanks a bunch everyone!

---

