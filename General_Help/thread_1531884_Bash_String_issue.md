---
title: "Bash String issue"
date: 2010-07-15
forum: General Help
---

### Post by iMetaphysikz on 2010-07-15
Hi I'm just wondering why bash needs "\\" to produce "\" in a string from user input. Also is there anyway to get bash to put "\\" in a string when a user enters "\\"

```
 
    echo "Please enter the directory to back-up:"
    read tardir
    echo $tardir

```

---

### Post by Skaperen on 2010-07-15
That's because \ is used in front of some other things to have special meanings, such as \n to mean a newline character.  If you really want it to have a '\' and a 'n' then "\\n" accomplishes that escapement.

I think the command```
sed 's/\\/\\\\/g'
``` might do what you want, for strings piped through it.

I hope you are aware that it is odd to use \ in filenames in Linux/Unix, though it can be done. But more importantly, the \ is NOT a directory separator character ... the / is.

---

### Post by yaaarrrgg on 2010-07-15
also you can do:

```
 
echo "Please enter the directory to back-up:"
read -r tardir
echo $tardir

```

---

### Post by corncob on 2010-07-15
I've heard something like this: \ is a control or meta character that tells the shell that the next character is a real one, so to actually print one you'd need to put in \\.  To print \\ I'd try typing in "\\\\".

---

### Post by sisco311 on 2010-07-15
Quoting is fun! :) You have to use single quotes '\\', check out:
```
man bash | less +/QUOTING
```

---

### Post by btindie on 2010-07-15
Are you sure you mean "\"? That's the windows directory separator character.
 
It's used as an escape character so you can insert things like a "\t" tab. So to get it to show just the back slash character you need to use it twice "\\".
 
If you want to get bash to output a string that is escaped then you'll need to do a string substitution - replacing "\" with "\\".

---

### Post by Skaperen on 2010-07-15
> **corncob said:**
> I've heard something like this: \ is a control or meta character that tells the shell that the next character is a real one, so to actually print one you'd need to put in \\.  To print \\ I'd try typing in "\\\\".
In some contexts, that, or some other character, can do exactly that.  But in the shell context, and general programming languages like C, C++ and others, it applies a special interpretation to what follows. At the end of a line in C, a \ means to not parse the newline that follows, in the contexts where it would (e.g. in preprocessor directives). And what follows may be more than one character.  For example "\012" is another way to express a newline character.  See the "Oct" column from "man ascii".

---

### Post by iMetaphysikz on 2010-07-15
Thanks everyone, I was having a moment as it were and using \\ instead of //, I realized this about 5 minutes after I posted, this thread but, left it as I was interested into why this was the case anyway.

---

