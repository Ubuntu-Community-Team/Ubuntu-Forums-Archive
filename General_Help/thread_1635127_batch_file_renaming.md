---
title: "batch file renaming"
date: 2010-12-01
forum: General Help
---

### Post by dentex on 2010-12-01
Hi!
Is it possible to rename a list of files in batch in order to maintain the last part of them, then purge a central section and then again maintain the extension?

I.E.:
```
file01.qwertyuiop.txt
file02.asdfghjklmnbvzxcqwertyuiop.txt
file03.asdfghjklqwertyuiiop.txt
```in
```
file01.txt
file02.txt
file03.txt
```many thanks.

---

### Post by Hawkoon on 2010-12-01
Sorry for not giving you a bash solution. I use gnome-commander for problems like this because it has an excellent renaming option. It even allows you to use meta tag information for renaming (useful when when working with photos), add counters etc...

---

### Post by dentex on 2010-12-02
hey, great solution anyway. I'm going to google for it.

thanks!

---

### Post by luigi_mb on 2010-12-02
Get pyrenamer from the repositories. Very good.

/luigi

---

### Post by sisco311 on 2010-12-02
There are many great GUI mass file rename tools in the repositories. Thanks Hawkoon, I added gnome-commander to my list. :)

[list]
[*]thunar (file manager)
[*]**gprename** 
[*]gnome-commander (file manager)
[*]purrr 
[*]pyrenamer 
[*]gwenrename 
[*]**krename** 
[/list]

thunare, gprename and krename are easy to use, but still powerful.

The perl based rename command is installed by default Ubuntu:
```
rename -n 's/(file[0-9]+)\..*/$1.txt/' *.txt
```

mmv is in the repositories:
```
mmv '*.*.txt' '#1.txt'
```

and you can always write a little script:
```
cd path/to/dir
for file in *.txt; do 
  echo mv -b "${file}" "${file//.*/}.txt"; done
done
```

---

### Post by Hawkoon on 2010-12-03
> **sisco311 said:**
> There are many great GUI mass file rename tools in the repositories. Thanks Hawkoon, I added gnome-commander to my list.

I grew up with Norton Commander, so for me gnome-commander is a must-have.

> **sisco311 said:**
> 
```
rename -n 's/(file[0-9]+)\..*/$1.txt/' *.txt
```mmv is in the repositories:
```
mmv '*.*.txt' '#1.txt'
```and you can always write a little script:
```
cd path/to/dir
for file in *.txt; do 
  echo mv -b "${file}" "${file//.*/}.txt"; done
done
```

I do write the odd bash script and always find the string manipulation quite challenging. Do you have any good reference that explains how to use the formating characters, like the ones you use in 1st and 3rd example? That'd be really great.

---

### Post by sisco311 on 2010-12-03
The rename command uses Perl Regular Expressions. The Perl Programming Documentation is quite good:
[http://perldoc.perl.org/perlre.html](http://perldoc.perl.org/perlre.html)

For learning bash, I recommend:
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) ( [Parameter Expansion]("http://mywiki.wooledge.org/BashGuide/Parameters") )
and
[http://wiki.bash-hackers.org/doku.php](http://wiki.bash-hackers.org/doku.php)

And of course the man pages. At first glance, they can look intimidating and very cryptic, but if you learn how to use them, you will find them indispensable. ;)

EDIT: i.e. If you want to check out "Parameter Expansion" in bash, open its manpage:
```
man bash
```
hit / for search, type in *parameter expansion*, Enter, then n until you find the section. (press h for a summary of command)

---

### Post by dentex on 2010-12-03
> **luigi_mb said:**
> Get pyrenamer from the repositories. Very good.
Really thanks! this is what I was looking for!!!


[QUOTE=sisco311]The perl based rename command is installed by default Ubuntu:
```
rename -n 's/(file[0-9]+)\..*/$1.txt/' *.txt
```[/QUOTE]
Great! I tried a bit with the "rename" command, but I had no success in choosing the right sintax for the substitution.

Thanks everyone!

---

