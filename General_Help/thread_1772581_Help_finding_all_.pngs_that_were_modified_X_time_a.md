---
title: "Help finding all .pngs that were modified X time ago, excluding a couple directories"
date: 2011-05-31
forum: General Help
---

### Post by FabianN on 2011-05-31
I am trying to run a find that will return all .png files that were modified 180 (exact amount/time not critical) minutes ago, excluding all the contents in two directories.

With the help of google I've been able to have the find either return all .png that were x old and at one point I was able to get it to exclude the desired directories (I've now lost that method, unfortunately I didn't paste it into my notes), but when I try to put the two expressions together it doesn't return anything (as in, no results from the find).

Halp?


This is what I've gotten to find all .png at X time old:
```
find /var/www/minecraft/map -name *.png -a -mmin +180
```

The two directories (and all its contents) I'd like to exclude are /var/www/minecraft/map/spawn and /var/www/minecraft/map/minerals


I've tried -name spawn -prune and ! -name spawn and both cases have not worked for me.

---

### Post by AlphaLexman on 2011-05-31
I believe you need to utilize the **-path** and the **-prune** options together.

From the man page:
```
-path pattern
              File  name matches shell pattern pattern.  The metacharacters do
              not treat `/' or `.' specially; so, for example,
                        find . -path "./sr*sc"
              will print an entry for a directory called `./src/misc' (if  one
              exists).   To  ignore  a whole directory tree, use -prune rather
              than checking every file in the tree.  For example, to skip  the
              directory  `src/emacs'  and  all files and directories under it,
              and print the names of the other files found, do something  like
              this:
                        [COLOR="Blue"]find . -path ./src/emacs -prune -o -print[/COLOR]
              Note that the pattern match test applies to the whole file name,
              starting from one of the start points named on the command line.
              It  would  only  make sense to use an absolute path name here if
              the relevant start point is also an absolute path.   This  means
              that this command will never match anything:
                        find bar -path /foo/bar/myfile -print
              The  predicate -path is also supported by HP-UX find and will be
              in a forthcoming version of the POSIX standard.

```

---

### Post by erind on 2011-05-31
Elaborating further on AlphaLexman's advice, you can try something like this:

```
find /var/www/minecraft/map -path /var/www/minecraft/map/spawn -prune -o -path /var/www/minecraft/map/minerals -prune -o -type f -name '*.png' -mmin +180 -print
```Also don't forget to quote the wildcards (**'*.png'**) when using *find*.

---

### Post by AlphaLexman on 2011-05-31
^ +1 ^

---

### Post by FabianN on 2011-05-31
> **erind said:**
> Elaborating further on AlphaLexman's advice, you can try something like this:

```
find /var/www/minecraft/map -path /var/www/minecraft/map/spawn -prune -o -path /var/www/minecraft/map/minerals -prune -o -type f -name '*.png' -mmin +180 -print
```Also don't forget to quote the wildcards (**'*.png'**) when using *find*.

Your example wouldn't work for me (returned all images), but it pointed me in the right direction.

I tried your example with some modifications of my own and I found that the use of the full path, -prune, and -o were all causing issues.

I ended up doing this:
[SOLUTION]
```
find /var/www/minecraft/map -name *.png -a -mmin +180 -a ! -path "*spawn*" -a ! -path "*mineral*"
```

And this appears to be working for me, though I need to do some more thorough testing to ensure that the -mmin 180 is actually working as it should, but that ought to be fairly easy for me to deal with if it's not.


Thanks for the help.

---

### Post by erind on 2011-06-01
> **FabianN said:**
> Your example wouldn't work for me (returned all images), but it pointed me in the right direction.

I tried your example with some modifications of my own and I found that the use of the full path, -prune, and -o were all causing issues.
...```
find /var/www/minecraft/map -name *.png ... 
```
I successfully tested my code a few times - it'll exclude from the search two given directories. 
Just to point out again, never leave unquoted or unescaped the wildcard patterns in the* find* command, namely:** *.png **-> **'*.png'**
Also note that *find* is very picky on its syntax, always test it thoroughly. Besides *find*'s man pages, another good source is:

[http://www.softpanorama.org/Tools/Find/find_mini_tutorial.shtml#Introduction](http://www.softpanorama.org/Tools/Find/find_mini_tutorial.shtml#Introduction)

> Thanks for the help.Welcome, glad you got it working.

---

