---
title: "Replace CRLF with two Spaces: sed and/or tr help"
date: 2010-12-20
forum: General Help
---

### Post by gordonsowner on 2010-12-20
Hi,

I have a binary file with fixed-width fields.  I have a dataset that has some stray CRLF (\x0d0a) in it.  I want to replace those bytes with one space each (\x20).  However, I want to leave lone LF (\x0a) chars alone.  I can't seem to figure out how to do this.

sed doesn't look right, as it is line-oriented and ignores \x0a everywhere it sees it (ref: [http://ubuntuforums.org/showthread.php?t=69115](http://ubuntuforums.org/showthread.php?t=69115)).  I can't seem to figure out any way around not using \x0a as a line separator.  I also looked at 'tr', but that doesn't seem quite right either, as it is a character for character replacement.  Which means that I can't do:

```
tr '\x0d\x0a' '\x20\x20' my.file 
```

because it will replace all \x0a chars with spaces, regardless of whether or not they are preceded by \x0d.

Help is appreciated.

TIA,
Matt

---

### Post by DaithiF on 2010-12-20
you can probably still use sed, something like:

```
sed -e :a -e '/\r$/{N;s/\r\n/ /;ta}' thefile > newfile

```(untested)

as you point out it will split lines based on newline characters, however if the char preceding that is a carriage return, then perform the 3 steps of (a) reading in the next line, (b) replacing the \r\n pair with a space, and (c) repeating as necessary

---

### Post by gordonsowner on 2010-12-20
Thank you!  I will try, but I am first researching the structure you used -- I've used sed, but not with these advanced options.  I'll post with results, but I'm reading documentation on your solution and explanation now.

Thanks again,

---

### Post by gordonsowner on 2010-12-21
Hi,

Thank you for the help.  The solution didn't work... it still left the '0a' in the file.  I was, however able to use the sed-like capabilities of perl to get this done.  My solution was:

```
perl -0777 -pe "s/\x0d\x0a/\x20\x20/gi" < orig.dbf > new.dbf
```

I just tweaked the solution found here: [http://forums.devshed.com/perl-programming-6/perl-searching-and-replacing-an-hex-pattern-514905.html](http://forums.devshed.com/perl-programming-6/perl-searching-and-replacing-an-hex-pattern-514905.html)

Thanks again for your help!
Matt

---

