---
title: "grep returns odd results based on EOL"
date: 2012-04-10
forum: General Help
---

### Post by thatsmyboy on 2012-04-10
I'm doing some file manipulation which requires using grep to handle files. For some reason, grep returns strange results with Mac format text end of line (EOL) characters (CR). Grep works okay for me as long as the end of line is given with a line feed (LF), but not with carriage returns only. 

The idea is this:

ThisIsMySearchString
THISISMYTESTINGSTRING

if I use grep to locate the string 'Search', it should return the name of the file and the line in which it is found. Instead, the CR file (testing2) returns 

THISISMYTESTINGSTRINGchString

in the command line interface. 
What's more, when I use redirection to output the results of the command, I GET A DIFFERENT RESULT!

Any help would be appreciated.

---

### Post by papibe on 2012-04-10
Hi thatsmyboy.

When you are doing this:
```
$ grep This testing2.txt 
THISISMYTESTINGSTRING

```
The whole file is being printed because grep doesn't recognize 'cr' as line endings. You don't see the whole content because you are printing crs the lines get overwritten.

You can see what is going on if you do:
```
$ grep This testing2.txt | od -a
0000000   T   h   i   s   I   s   M   y   S   e   a   r   c   h   S   t
0000020   r   i   n   g  **[COLOR="Red"]cr[/COLOR]**   T   H   I   S   I   S   M   Y   T   E   S
0000040   T   I   N   G   S   T   R   I   N   G  **[COLOR="Red"]cr[/COLOR]**  nl
0000054

```
I hope that points you in the right direction.
Regards.

---

### Post by ridetheteapot on 2012-04-10
worth nothing - it is the '^M' character that is boofing you up.
Open testing2 in vi to it plainly.
You can use sed to convert the ctrlM's to /r or /n or whatever you want.
also worth noting - just try to even cat testing2, you'll see grep isn't actually the problem.

---

### Post by thatsmyboy on 2012-04-11
Thanks for those suggestions. I realized that it had to do with the line endings, but typically grep will return the file name FIRST. In my results it doesn't return the filename (which is actually kind of the point of this exercise for me).:p

Would you consider this a feature or a bug? Also, can you explain the different results when printing to screen versus printing to file?

---

### Post by Vaphell on 2012-04-11
grep returns matches with filenames when there are multiple files given (with * or whatever), when there is only one file or when it gets data from stdandard input via pipe, there is no name in the output.

> Would you consider this a feature or a bug?
what, not working with newlines in foreign formats? A fact of life. Normalize everything to the format native to the platform you work on (linux in this case) and everything will be peachy (with sed 's/\r/\n/g' or whatever). Whole toolchain assumes \n, go with it to save yourself a lot of pain.

---

