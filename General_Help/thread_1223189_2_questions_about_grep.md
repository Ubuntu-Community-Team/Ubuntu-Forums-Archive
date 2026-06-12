---
title: "2 questions about grep"
date: 2009-07-25
forum: General Help
---

### Post by RobertL on 2009-07-25
1) When I grep for something in a certain text file it never finds anything. Even grepping for a single letter produces no output. But if I use grep on any other file it works as expected. So I guess something is unique about this file that is making grep not work. I remember reading somewhere that the file must not contain any null characters, but now I can't find where I read that. Is is true that grep doesn't work if the target file contains a null? How can I find and delete nulls in my problem file? Is there some other reason grep wouldn't find anything?

2) I seem to remember from the past a grep option to output the entire paragraph in which the search string is found but I don't see such an option now. It might have been "-p". Was that function moved to some other command? Is there a paragrep or some such?

I'm using GNU grep 2.5.3 on Ubuntu 9.04.

---

### Post by LookTJ on 2009-07-25
for #1

grep with no arguments with is case-sensitive
```
lspci | grep Ethernet
``` will display your ethernet while
```
lspci | grep ethernet
``` will not

However if you want to ignore case-sensitive
```
lspci | grep ethernet -i
```will display whether the word is case-sensitive or not.

:)

but if you are looking through a file like xorg.conf, then using
```
cat /etc/X11/xorg.conf | grep Device
``` will show every line with the word "Device" in it
and again -i is ignoring case

the "|" key is below your backspace key, which looks like broken pipes.

Hope that answers #1 for you :)

---

### Post by RobertL on 2009-07-25
> **LookTJ said:**
> for #1

grep with no arguments with is case-sensitive
```
lspci | grep Ethernet
``` will display your ethernet while
```
lspci | grep ethernet
``` will not

However if you want to ignore case-sensitive
```
lspci | grep ethernet -i
```will display whether the word is case-sensitive or not.

:)

but if you are looking through a file like xorg.conf, then using
```
cat /etc/X11/xorg.conf | grep Device
``` will show every line with the word "Device" in it
and again -i is ignoring case

the "|" key is below your backspace key, which looks like broken pipes.

Hope that answers #1 for you :)

I don't think this relates to the problem I'm talking about. I'm not having a problem with case sensitivity. My problem is that grep can't find anything at all in this particular file.  For example:

grep the filename

returns nothing at all. But "filename" has a few thousand lines of text and many "the"s, which I can see in a text editor. If I copy some of the text out of it with a text editor and put it into a new file then grep can find it as expected.

The file was originally a .txt file on windows if that helps.

---

### Post by bchurchill on 2009-07-26
> **RobertL said:**
> 
grep the filename

returns nothing at all. But "filename" has a few thousand lines of text and many "the"s, which I can see in a text editor. If I copy some of the text out of it with a text editor and put it into a new file then grep can find it as expected.

The file was originally a .txt file on windows if that helps.

I'm not sure if this will help, but you could try running

```
dos2unix filename
```This changes the carriage return/linefeed characters on each line, but I'm not sure that's what your problem is.  If you want to try this you may need to #apt-get install tofrodos

also: check for silly things, like if your filename has a space in it, be sure to escape it or put the whole filename in quotes.  There's an unlikely chance that's the problem too.

---

### Post by kaibob on 2009-07-26
> **RobertL said:**
> 1)...How can I find and delete nulls in my problem file?...

You can filter out null characters with the tr utility: 

```
cat file | tr -d '\000'
```

---

### Post by DaithiF on 2009-07-26
regarding the 2nd question about showing the paragraph within which a match is found, i think the closest grep provides to this would be the -C flag, which outputs a certain number of lines before and after each match, so for example:

```
grep -C 2 searchterm somefile.txt
```

would show 2 lines of context before & after each match.

also, 
```
man grep
``` 
for learning more about how to use grep

---

