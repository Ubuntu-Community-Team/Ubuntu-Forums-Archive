---
title: "Need help with perl regex"
date: 2012-10-13
forum: General Help
---

### Post by AlexBooton on 2012-10-13
Hi,  I don't know perl at all and am not very good with regular expressions. 

I'm trying to eliminate some non-utf8 characters in file names and don't know the original charset.  Here's an example of one of the file names:  ```
GebÃ¤udet
``` although I don't know if you'll see this the way I do.

I've tried convmv with several different -f (i.e. from) charsets but none work.  I'm almost certain the characters are in German but in convmv latin-1, iso-8859-16 and cp850 don't work to fix it. 

So I'm trying to use the rename command to rename the files.  I found a site with an example of how to do this here: [http://askubuntu.com/questions/25823/best-practice-to-replace-unknown-chars-from-unknown-charsets-in-filenames]("http://askubuntu.com/questions/25823/best-practice-to-replace-unknown-chars-from-unknown-charsets-in-filenames") and here's what it says: ```
If you just want to get rid of some characters, you could try this:

rename "s/^[A-Za-z0-9-_]/_/g"

That would replace every character that is not just char, 
number or dash with an underscore. 
Run with the -n option to see what is happening 
in a dry-run.

```

But instead of replacing the unknown characters it seems to be replacing the FIRST character in the file name even when it's a perfectly acceptable character AND NOT fixing the "bad" characters.

Here's an example: ```
GebÃ¤udetechnik.pdf renamed as _ebÃ¤udetechnik.pdf
```

Can you help with the proper perl regex to convert the non-utf8 characters to something else?

And also, the replace command doesn't seem to have a -r option for recursive processing.  Is there an easy way to make it work recursively?

Thanks in advance.

---

### Post by erind on 2012-10-13
> **AlexBooton said:**
> [...]
 
Here's an example: ```
GebÃ¤udetechnik.pdf renamed as _ebÃ¤udetechnik.pdf
```
 
Can you help with the proper perl regex to convert the non-utf8 characters to something else?
 
And also, the replace command doesn't seem to have a -r option for recursive processing. Is there an easy way to make it work recursively?
 
Thanks in advance.
 
One way would be:
 
```
 
rename -n 's/[^[:ascii:]]/_/g' *

```
 
For recursive renaming try:
 
```
 
find /path/to/files -type f -exec rename -n 's/[^[:ascii:]]/_/g' {} +

```When happy with results, remove **-n** option from *rename*.

---

### Post by AlexBooton on 2012-10-13
Thank you very much!

Your solution worked.

Unfortunately, I wasn't able to use it because it created a lot of useless file names like: ____________.______._______abc_____

It would have made it almost impossible to tell one file from another.

But your solutions were quite instructive.  I learned something.

Thanks again!

---

### Post by kbrodenhau on 2012-10-13
> **AlexBooton said:**
> Hi,  I don't know perl at all and am not very good with regular expressions. 

I'm trying to eliminate some non-utf8 characters in file names and don't know the original charset.  Here's an example of one of the file names:  ```
GebÃ¤udet
``` although I don't know if you'll see this the way I do.

I've tried convmv with several different -f (i.e. from) charsets but none work.  I'm almost certain the characters are in German but in convmv latin-1, iso-8859-16 and cp850 don't work to fix it. 

So I'm trying to use the rename command to rename the files.  I found a site with an example of how to do this here: [http://askubuntu.com/questions/25823/best-practice-to-replace-unknown-chars-from-unknown-charsets-in-filenames](http://askubuntu.com/questions/25823/best-practice-to-replace-unknown-chars-from-unknown-charsets-in-filenames) and here's what it says: ```
If you just want to get rid of some characters, you could try this:

rename "s/^[A-Za-z0-9-_]/_/g"

That would replace every character that is not just char, 
number or dash with an underscore. 
Run with the -n option to see what is happening 
in a dry-run.

```But instead of replacing the unknown characters it seems to be replacing the FIRST character in the file name even when it's a perfectly acceptable character AND NOT fixing the "bad" characters.

Here's an example: ```
GebÃ¤udetechnik.pdf renamed as _ebÃ¤udetechnik.pdf
```Can you help with the proper perl regex to convert the non-utf8 characters to something else?

And also, the replace command doesn't seem to have a -r option for recursive processing.  Is there an easy way to make it work recursively?

Thanks in advance.


Try this maybe:

rename "s/[^A-Za-z0-9-_\.]*/_/g"

---

