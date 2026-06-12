---
title: "rename mutiple image files through terminal"
date: 2012-02-08
forum: General Help
---

### Post by pavi_elex on 2012-02-08
I have more than 5000 .jpg files in folder. The names are with backslash.
uploadedfile_129730019157343750\uploadedfile_129730019157343750-001.jpg
uploadedfile_129730019157343750\uploadedfile_129730019157343750-002.jpg
uploadedfile_129730019157343750\uploadedfile_129730019157343750-003.jpg
uploadedfile_129730019157343750\uploadedfile_129730019157343750-004.jpg
uploadedfile_129730019157343750\uploadedfile_129730019157343750-005.jpg
uploadedfile_129730019157343750\uploadedfile_129730019157343750-006.jpg
.... & so on....

I want to rename all files simultaneously. The name should be like
001.jpg
002.jpg
003.jpg

I have used rename command 
$ rename "uploadedfile_129730019157343750\uploadedfile_129730019157343750-" "" *
but I am facing following error.
Bareword "uploadedfile" not allowed while "strict subs" in use at (eval 1) line 1
I have tried all combinations of rename command but result is same error. Ex-
$ rename "uploadedfile" "" *
I have tried for loop too but no luck.
I do not want to use any GUI application like krename or what ever.
I want to do this from terminal. Please help me

---

### Post by HiImTye on 2012-02-08
```
rename -n 's/uploadedfile_129730019157343750\\uploadedfile_12973 0019157343750-//' *
```if it does what you want just change the -n to -v

edit: made it remove the last '-' also

---

### Post by sudodus on 2012-02-08
Will the command line work if you enclose the original file name in single quotes 'filename-with-backslash'? Try with one file. Once something like that works it will be easy to make a batch job.

---

### Post by sudodus on 2012-02-08
Yes, I just found that 
```
echo hello>'h\.txt'
```
creates a file with a backslash in the name
```
mv 'h\.txt' hello.txt
``` will get rid of it :-)

---

### Post by HiImTye on 2012-02-08
now that I think about it, this should work just fine:
```
rename -n 's/.*(\d{3})/$1/' *
```

---

### Post by HiImTye on 2012-02-08
yeah, it works perfectly.
```
tye@T:~/Documents/you're a dummy$ rename -n 's/.*(\d{3})/$1/' *
dummy001 renamed as 001
dummy002 renamed as 002
dummy003 renamed as 003
```

---

### Post by pavi_elex on 2012-02-08
Thanks "[HiImTye]("http://ubuntuforums.org/member.php?u=843901")", Half work is done only because of you. Your first command is really useful.
First I reached in to that folder where all these file are located using cd
like
$ cd Desktop/uploadedfiles
then i tried 
:~ /Desktop/uploadedfiles$ rename 's/uploadedfile_129730019157343750//g' *
Now the files have become
\-001.jpg
\-002.jpg
\-003.jpg
\-003.jpg
.... & so on...
Now I want to get rid off this backslash (\). Please help one more time.
I have tried
rename 's/\//g' *
and other combinations but backslash is there. Please help.

---

### Post by Khayyam on 2012-02-08
> **HiImTye said:**
> yeah, it works perfectly.
```
tye@T:~/Documents/you're a dummy$ rename -n 's/.*(\d{3})/$1/' *
dummy001 renamed as 001
dummy002 renamed as 002
dummy003 renamed as 003
```

No, not "perfectly" .. your not accounting for more than 3 digits (which on an archive of "more than 5000 jpg files" would be required)

```
% touch dummy001 dummy5000
% rename -n 's/.*(\d{3})/$1/' *
dummy001 renamed as 001
dummy5000 [COLOR=Red]renamed as 000[/COLOR]
```I'd probably opt for selecting the position of the string rather than regex

```
% cat input.txt
uploadedfile_129730019157343750\uploadedfile_12973 0019157343750-001.jpg
uploadedfile_129730019157343750\uploadedfile_129730019157343750-5000.jpg
% awk -F"-" '{print $2}' < input.txt
001.jpg
5000.jpg
```This will require scripting to meet the OP's needs, but thats not this threads remit (as the OP asked for a 'rename' solution), so I'll leave it to others to fix the regex. 

best ...

---

### Post by HiImTye on 2012-02-08
\ is an escape sequence in perl so you need to do it twice so it is \\ so to remove the \- you would
rename -n 's/\\-//' *

---

### Post by HiImTye on 2012-02-08
> **Khayyam said:**
> No, not "perfectly" .. your not accounting for more than 3 digits (which on an archive of "more than 5000 jpg files" would be required)
I did 3 digits because the OP asked for 3 digits
> **pavi_elex said:**
> I want to rename all files simultaneously. The name should be like
001.jpg
002.jpg
003.jpg

but yeah, you're right it should be 4 digits if there are >5000 so it should be:[FONT=monospace]
[/FONT]```
rename -n 's/.*(\d{4})/$1/' *
```but thats why we use -n, right?
or we could use something like:
```
rename -n 's/.*(\d{4})\./$1./' *
``` to select only the stuff before the extension

---

### Post by pavi_elex on 2012-02-08
Thanks...[HiImTye]("http://ubuntuforums.org/member.php?u=843901") .... it is done now
I have tried
$ rename 's/\\//g' *
and backslash is gone.
Now the files are like what i exactly want.
Thank you once again.

---

### Post by Khayyam on 2012-02-08
> **HiImTye said:**
> I did 3 digits because the OP asked for 3 digits [...] but yeah, you're right it should be 4 digits if there are >5000

Hilm .. well, that was the example data, the data set was "more than 5000 jpgs".
  
> **HiImTye said:**
> so it should be:[FONT=monospace]

[/FONT]```
rename -n 's/.*(\d{4})/$1/' *
```

This will not match <4 digits .. and so will exclude 'dummy001 - dummy999'

> **HiImTye said:**
> [..] but thats why we use -n, right?

Sure, but we are skinning a cat here, right?

> **HiImTye said:**
> or we could use something like:

```
rename -n 's/.*(\d{4})\./$1./' *
```to select only the stuff before the extension

Yes, we could, it'll still balk on <4 chars .. infact that regex will return nothing as I'm pretty sure its syntax is incorrect.

As I said, I would work on the poistion not the string, field handling is generally far safer.

best ...

---

### Post by HiImTye on 2012-02-08
yeah, (\d{3,4}) seems to pass 3 characters regardless of if there are 4
> infact that regex will return nothing as I'm pretty sure its syntax is incorrect.
it's correct

---

### Post by Khayyam on 2012-02-08
> **HiImTye said:**
> yeah, (\d{3,4}) seems to pass 3 characters regardless of if there are 4

I believe that is because d\{n} would be a place and not a range (but I'm not much of a regexer).

> **HiImTye said:**
> it's correct

It may be "correct" but it doesn't match the string ..

```
% touch dummy001 dummy5000
% rename -n 's/.*(\d{4})\./$1./' *
%
```

best ...

---

### Post by jamesisin on 2012-02-08
I'm a little late to the party, but you might enjoy my renaming script:

[http://jamesisin.com/a_high-tech_blech/index.php/2011/04/malleable-renaming-script/](http://jamesisin.com/a_high-tech_blech/index.php/2011/04/malleable-renaming-script/)

---

### Post by HiImTye on 2012-02-08
> **Khayyam said:**
> I believe that is because d\{n} would be a place  and not a range (but I'm not much of a regexer).
> {n}         Match exactly n times
    {n,}        Match at least n times
{n,m}       Match at least n but not more than m times
[http://perldoc.perl.org/perlre.html](http://perldoc.perl.org/perlre.html)

> **Khayyam said:**
> It may be "correct" but it doesn't match the string ..

```
% touch dummy001 dummy5000
% rename -n 's/.*(\d{4})\./$1./' *
%
```
that's because there's no extension on them
```
tye@T:~/Documents/dummy$ ls
001dummy  002dummy  dummy.003  dummy.004  dummy005  dummy006  dummy007.ext  dummy008.ext  dummy09  dummy10
tye@T:~/Documents/dummy$ rename -n 's/.*(\d{3})\./$1./' *
dummy007.ext renamed as 007.ext
dummy008.ext renamed as 008.ext
```

---

### Post by Khayyam on 2012-02-08
> **HiImTye said:**
> 
[QUOTE=Khayyam]I believe that is because d\{n} would be a place and not a range (but I'm not much of a regexer).
> {n} Match exactly n times
{n,} Match at least n times
{n,m} Match at least n but not more than m times[/QUOTE]

Which would make "\d{n}" a place .. it only matches "digit to {n} places", not a range of digits. So "\d{3,4}" wouldn't match 3 "or" 4 digits .. and **that** is what I was responding to from your post. There is no need to quote perldocs at me, I'm not trying to win regex points.

> **HiImTye said:**
> that's because there's no extension on them

```
tye@T:~/Documents/dummy$ ls
001dummy  002dummy  dummy.003  dummy.004  dummy005  dummy006  dummy007.ext  dummy008.ext  dummy09  dummy10
tye@T:~/Documents/dummy$ rename -n 's/.*(\d{3})\./$1./' *
dummy007.ext renamed as 007.ext
dummy008.ext renamed as 008.ext
```

I see, as I said I'm not much of a regexer, I was matching on the "dummy" data provided in the example which was sans suffix.

best ...

---

