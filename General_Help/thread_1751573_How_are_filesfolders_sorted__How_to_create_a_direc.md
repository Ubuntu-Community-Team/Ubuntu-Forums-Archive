---
title: "How are files/folders sorted / How to create a directories that always stay on top?"
date: 2011-05-06
forum: General Help
---

### Post by agrayray on 2011-05-06
have been working how to do this for a while finally getting around to asking....

as a long time windows user I have used a trick of creating directories that will always be the first ones displayed by using an _foldername model, for ex:

_temp
A dir
B dir
temp

assuming the four above are directories that is how they are sorted by default in windows and I commonly use this technique for special folders.

for my virtual machines folder in windows looks like this:

_base
LX-Ubuntu9.1
LX-Ubuntu11.4
XP-TestVM
...

where I put base virtual machines in _base and it makes it easy to separate them for all the other folders which are virual machines....SO....

in Ubuntu, I cant figure out a character or way to ensure this type of behavior, for example if I create a _base folder it shows up after a dirs and around the bs etc...

any know a way to create a dir with a special char that will ensure it stays on top?

---

### Post by agrayray on 2011-05-10
just figured I would post again to see if anyone might catch a glimse of this question...?

Does anyone know if there is way to create a folder names with a special character so that they are always sorted first in a directory listing (assuming all else is the same with regards to the sorting)...I want to keep my folders sorted by name by default but would love to have directories beginning with an underscore always sorted first as in the following example:

(assume all the names below are directories)

_apple
_banana
_carrot
apple
banana
carrot
....
zucchini

?

---

### Post by Telengard C64 on 2011-05-10
Each program can choose its own default sort order. Not knowing what program you are using to list files makes it hard to recommend a single method which will work in all cases.

Just as an example, I whipped this up in the console.

```
foo$ for i in " " "%" 0 1 "=" A a ; do touch "${i}file" ; done
foo$ ls -1
0file
1file
afile
Afile
=file
 file
%file
```

So on my system it looks like **ls** sorts digits before alphas and specials. But that is only for **ls**; Konqueror or Dolphin will undoubtedly do things their own way.

And that's only on my own system. Another factor is your locale. Applications which sort lists frequently take your locale into account, because not every language uses the English alphabet.

[quote=man sort]Comparisons shall be based on one or more sort keys extracted from each
       line of input (or, if no sort keys are specified, the  entire  line  up
       to,  but  not  including,  the  terminating  <newline>),  [b]and  shall be
       performed using the collating sequence of the current locale.[/b]
[/quote]

I don't really have a solution for you, but at least I hope you now have enough information to come up with a system that will work the way you want.

---

### Post by agrayray on 2011-05-10
Thanks for the reply...btw I guess I should have clear about this as this is really for Nautilus..as I use Ubuntu GNOME and the default viewer for that and whereas 'ls' will print things in nice orders that you specify, I cant seem to find out how to get this with nautilus.

To be more precise I create and use directory names like this so when I get a file dialog in some application (which uses nautilus) I want to easily click into the folder  and select some entries at the top versus moving around forever searching for things..and given your example and assuming there are also equivalent {i}gile and {i}hile files nautilus will list them like this

0file
..
file
0gile
...
gile
0hile
...etc

as it seems there is no special character you can place where nautilus wont attach it to a alpha sorting by a character.

Thanks for the reply again!

Would be curious if anyone has figured a way to do this as I think I cant be the only who wants this trick to easy get to files from file dialogs when they have lots of directories to sort through...

---

### Post by Mat11 on 2011-12-31
> **agrayray said:**
> Thanks for the reply...btw I guess I should have clear about this as this is really for Nautilus..as I use Ubuntu GNOME and the default viewer for that and whereas 'ls' will print things in nice orders that you specify, I cant seem to find out how to get this with nautilus.

To be more precise I create and use directory names like this so when I get a file dialog in some application (which uses nautilus) I want to easily click into the folder  and select some entries at the top versus moving around forever searching for things..and given your example and assuming there are also equivalent {i}gile and {i}hile files nautilus will list them like this

0file
..
file
0gile
...
gile
0hile
...etc

as it seems there is no special character you can place where nautilus wont attach it to a alpha sorting by a character.

Thanks for the reply again!

Would be curious if anyone has figured a way to do this as I think I cant be the only who wants this trick to easy get to files from file dialogs when they have lots of directories to sort through...


I was wondering if the programmers of software like Nautilus in Ubuntu could provide better software recognition and start up options in the default viewer.
Have had the same problem finding a way to start Audicity. Have noticed that there is always an assumption in Ubuntu forums that you have to be an experienced Ubuntu user to understand what is being written but surely that might put people off for Using the OS.

---

### Post by rjf1 on 2012-01-01
Doesn't this work?

01_apple
01_banana
01_carrot
apple
banana
carrot
....
zucchini

---

