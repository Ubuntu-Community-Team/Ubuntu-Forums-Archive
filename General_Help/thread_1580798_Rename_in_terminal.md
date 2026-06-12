---
title: "Rename in terminal"
date: 2010-09-23
forum: General Help
---

### Post by miststlkr on 2010-09-23
I have been using the gnome-terminal *rename* command with regexp to bulk rename files, but have to run several consecutive *rename*s some times.  Is there a way to pass the results from one directly into the next regexp using one command?


For example, I might currently do something like this:

rename 's/.{3}/Toronto Trip/' * *[ENTER]*
rename 's/JPG/jpg/' * *[ENTER]*
rename 's/[0]{4}//' * *[ENTER]*

surely there is a way to do this without typing each command separately?

---

### Post by gzarkadas on 2010-09-24
rename accepts only one regular expression, so the answer is basically, not. However you can:

1. Put the regular expressions in a for loop: 
```

for ex in 's/.{3}/Toronto Trip/'  's/JPG/jpg/'  's/[0]{4}//' ; do rename "$ex" * ; done

```2. Write a wrapper script to do (1) for you:
```

#!/bin/bash
#works always in current directory
for ex in "$@" ; do rename "$ex" * ; done

```As is always a good practise, if you make a script test it well in a scrap folder that you can safely delete (and mesh with it).

---

### Post by miststlkr on 2010-09-24
Outstanding.  Thank you.  The for loop suits my needs well enough.  How might I then use the variables as I would in a single command?  for example one might use 

```
rename 's/(\d{4})/Summer of $1/' *
```

can this then be incorporated into a group in a for loop like what you described?  Either way that has already saved me a lot of work/time.   Cheers!

---

### Post by gzarkadas on 2010-09-24
In order for your example to work inside a script, you must use double quotes instead of single quotes to enclose the regular expression; else the variable substitution will not work. You can also declare variables directly in command line, say (see my notes below for this curious chore of single - double quotes):

```

T1='some text'
rename 's/(\d{4})/Summer of '"$T1"'/' *

```Or in one line:
```

T1='some text' ; rename 's/(\d{4})/Summer of '"$T1"'/' *

```If you have a small series of standard rename operations it is easier to make it an alias instead of a script. You make aliases with:

```
alias [short-name]='command string'
```To have them permanently, edit your ~/.bashrc (or ~./bash_aliases, if you use one) and put them there. Type `help alias' to read information about the command.

To use single quotes for surrounding regular expressions, you can use the concatenation feature of the shell, that is the fact that multiple quoted strings are concatenated to one. You will have to escape your literal quotes with a backslash. 

For example (please note that I haven't tested it; it may need tweaking. Also use your cursor to distinguish by moving left-right between double quotes and two consecutive single quotes - there is some trickery in there :)):

```

alias summer-ren='T1='\''some text'\'' ; rename '\''s/(\d{4})/Summer of '"$T1"/\'' *'

```Or, more complex:

```

alias summer-ren='T1='\''some text'\'' ; rename '\''s/(\d{4})/Summer of '"$T1"/\'' * ; rename '\''s/JPG/jpg/'\''

```Or, more complex and allowing text to be specified when running the command:

```

 alias summer-ren='read -p "Enter description:" ; rename '\''s/(\d{4})/Summer of '"${REPLY}"/\'' * ; rename '\''s/JPG/jpg/'\''
 
```

---

### Post by miststlkr on 2010-09-24
Wow.  Tons of information.  Thanks!   I'd like to learn more about this kind of stuff, would that be BASH scripting or something else?  I have previous coding experience but not at all in linux/BASH environments.   Thanks for all of your time and help.

---

### Post by gzarkadas on 2010-09-24
It's plain bash (shell) commands. The only "fancy" thing here is the need to protect the strings inside the regular expressions from the shell (in order not to interpret them as variables and such). Hence those awkward sequences of quotes.

`info bash' is all you will need to start; If you prefer to use your browser, [see there]("http://www.gnu.org/software/bash/manual/bashref.html") or you can install the apache2 and dwww packages. Your local man, info (and other) files will then be accessible from [http://localhost/dwww/index.html](http://localhost/dwww/index.html)

Well, this is enough to keep you busy for a while; happy renaming :).

---

