---
title: "sed"
date: 2009-12-04
forum: General Help
---

### Post by spongemonkey on 2009-12-04
I can't seem to get sed to work properly. I have an html file containing a lot of spacing, blank lines and lines with only spaces in them, and I'm told that

```
sed '/^$/d' filename
```

will delete every blank line in *filename* and output to stdout ready to be piped/redirected. But it doesn't appear to affect the text at all. The same goes for

```
sed '/^[ ]*$/d' filename
```

which I was hoping would delete lines that are just spaces.

Any advice? Thanks

---

### Post by lovemylady on 2009-12-04
[COLOR=Magenta]Ain't 100% sure but doesn'T gedit support that? to for example delete all "d" from a text so i think it should also be able to delete all spaces by just type in " " a space instead of any symbol or whatever.. :P[/COLOR]

---

### Post by spongemonkey on 2009-12-04
Thanks for the speedy reply!

I'm looking to include the process in a script so I really want a command line way of doing it.

I suppose one way would be to do

```
grep [a-zA-Z] > somefile
```

but sed should be able to do this... (ultimately I want to be doing more to the file which requires sed 's/.../g' type stuff so I'd rather do it all in sed. Plus it's nice to learn)

---

### Post by lovemylady on 2009-12-04
[COLOR=Magenta]Ahhw I see, well i personally got 0 plan about sed atall i even don't know what it is ;) just wwanted to give ya an alternative..

But if you got hundrets of files fom wich you would like to remove the spaces it would be really bad to do it 1 after one with gedit..

hm did you also already google perhaps?

for example "sed remove space script" or so? Who knows perhaps you find something :o[/COLOR]

---

### Post by DaithiF on 2009-12-04
perhaps there are tab characters or other forms of whitespace on the 'blank' lines.
try:
```
sed '/^\s*$/d' somefile 
```

---

### Post by spongemonkey on 2009-12-04
This works, thanks.

Could you explain what the code does please?

---

### Post by Diod on 2009-12-04
DaithiF's regex removes any line containing only whitespaces (or nothing).

^ is the start of the line
\s is whitespace, the * means it will look for 0 or more whitespaces. (? would be 0 or 1 whitespace; + would be 1 or more whitespaces)
$ is the end of the line

---

### Post by spongemonkey on 2009-12-04
Thanks very much guys.

Out of interest, is searching for ^$ quite fragile then? Doesn't seem to "do what it says on the tin"

---

### Post by Diod on 2009-12-04
It does do what it's supposed to: search for empty lines.
A space might mean nothing to a human, but it's a character just like any other for a computer ;)

The '^$' searches for a line without any characters in it, and since a space is a character like any other, it won't match a line like " ".

---

### Post by spongemonkey on 2009-12-04
There were plenty of lines that had no characters at all on (in Gedit), no spaces, tabs... could this have been a line with \n or something?

Thanks again

---

### Post by Diod on 2009-12-04
Hmm I'm not sure, but i guess it could've been the case.
[http://www.bio.ic.ac.uk/Evolve/docs/regex.html](http://www.bio.ic.ac.uk/Evolve/docs/regex.html) says that \s is an alternative for [ \t\n\r\f]

So it could've been a newline, carriage return or a form feed. I doubt it was a newline since it didnt show up like that in gedit, more likely a carriage return or form feed.

---

