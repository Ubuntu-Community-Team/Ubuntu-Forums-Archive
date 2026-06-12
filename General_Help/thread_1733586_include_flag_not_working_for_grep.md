---
title: "include flag not working for grep"
date: 2011-04-19
forum: General Help
---

### Post by sneakyimp on 2011-04-19
I'm trying a recursive search -- only PHP files -- and yet grep is searching SQL files too.

```

sneakyimp@Ubuntu-64bit:/var/www/site$ grep  -irl --include='*.php' 'car_images' *
2011_02_11_dump.sql
car_images_pending.sql
client/search_results.php
client/ext_setup.php
client/bobs/ext_setup.php

```

I've tried escaping grep, quoting it, using "command grep" etc. and in every case I'm still getting sql files in my result.  I tried changing commenting out the grep alias in .bashrc and that doesn't help either.

Can anyone tell me how to get grep to work properly?

---

### Post by hwttdz on 2011-04-19
So you're trying to search for "needle" in only php files? 

What's wrong with 

grep "needle" *.php  

?

---

### Post by sneakyimp on 2011-04-19
this command:
```
grep -irl 'car_images' *.php
```
does *not* recurse into subdirectories despite the r flag.  This has always bugged me about grep.

the --include=*.php allows one to filter files recursively.  that command has served me quite well on other machines, i just don't know why it is not working here on ubuntu.

---

### Post by DaithiF on 2011-04-19
> **sneakyimp said:**
> I'm trying a recursive search -- only PHP files -- and yet grep is searching SQL files too.

```

sneakyimp@Ubuntu-64bit:/var/www/site$ grep  -irl --include='*.php' 'car_images' *
2011_02_11_dump.sql
car_images_pending.sql
client/search_results.php
client/ext_setup.php
client/bobs/ext_setup.php

```I've tried escaping grep, quoting it, using "command grep" etc. and in every case I'm still getting sql files in my result.  I tried changing commenting out the grep alias in .bashrc and that doesn't help either.

Can anyone tell me how to get grep to work properly?
One pointer -- notice how the only .sql files its finding are the ones in the current directory?  You're giving grep contradictory instructions here.  The trailing wildcard '*' at the end of your command gets expanded by the shell to include all the contents of the current directory.  It is this expanded line that grep receives.  So grep is getting an instruction like:
```
grep -irl --include='*.php' 'car_images' 2011_02_11_dump.sql car_images_pending.sql client etc...

```So even  though you have said include only '*.php' files you have also explicitly asked grep to search those other files in the curernt directory too ... and it politely obliges.   To do what you want don't use the '*' at the end, instead use .  ie. the current directory.  That way you are giving grep a coherent instruction -- search recursively from the current directory, including only files like '*.php'.

---

### Post by sneakyimp on 2011-04-19
I suppose what you say makes some sense but there are a couple of aspects to this behavior which seem at odds with the man pages:

* man pages say the last parameter is a FILE not a directory.  
* --include=GLOB flag should limit search only to objects matching GLOB

At any rate, thanks for the help.

---

### Post by DaithiF on 2011-04-19
> **sneakyimp said:**
> 
* man pages say the last parameter is a FILE not a directory.  

A directory is just a special type of file.  The man page also says:
```
       -d ACTION, --directories=ACTION
              **If  an  input file is a directory**, use ACTION to process it.

```
which should remove any doubt that it means FILE to include directories.

> 
* --include=GLOB flag should limit search only to objects matching GLOB

I agree this is potentially confusing.  But I'm on grep's side here ... with conflicting instructions safer to work on the superset of whats been asked than decide which of the two conflicting instructions to go with.

---

### Post by sneakyimp on 2011-04-19
The docs could be clearer.  At any rate, *thanks* for your help.  Good stuff.

---

### Post by sneakyimp on 2011-04-20
Sorry to resurrect this, but apparently Ubuntu has a bug in grep:
> Found it. The include=exclude thing's a bug. And it's been fixed, at least in any distro that's up-to-date. Which of course doesn't include Debian, which is still using version 2.6.3.

[http://savannah.gnu.org/bugs/index.php?29876](http://savannah.gnu.org/bugs/index.php?29876)

I wonder if that's what's affecting the processing order too?

Where does one report a bug to the distro folks?

---

### Post by DaithiF on 2011-04-21
You're right.  Grep 2.5.4 (as was in lucid 10.04) works as you expected, 2.6.3 in 10.10 doesn't.  There is already a bug opened for this: [https://bugs.launchpad.net/ubuntu/+source/grep/+bug/651867](https://bugs.launchpad.net/ubuntu/+source/grep/+bug/651867)

---

