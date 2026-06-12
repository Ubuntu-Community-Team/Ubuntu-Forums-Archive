---
title: "'cd..' won't work"
date: 2006-06-04
forum: General Help
---

### Post by fapapa on 2006-06-04
I'm new to Ubuntu and fairly new to Linux in general. I had Mandriva before Ubuntu, so I really appreciate Ubuntu :) .

In the command line I would like to be able to type **cd..** (notice no space) to go up one directory, **cd../..** to go up two, etc. I'd also like to be able to type **cd-** (again, no space) to go to the previous directory, **cd~** to go home, cd/ to go to root, etc.

I made a few aliases in my .bash_aliases file, but some of these don't work, for obvious reasons, like **cd../..** and just plain **cd/**. I'm fairly convinced by now that the way to do this is not through aliases, but some other way, but I don't know what it is.

Maybe I should create bash scripts with file names like cd~, etc. I think I will run into the same problem with the '/', linux won't like it. Can anyone provide any help? Oh, I used to have all of the above functionality in Mandriva, so if someone out there has mandriva installed, please lend me a hand at type 'which cd../..' at the bash prompt. And if its an alias, let me know what the alias command is.

Thank you all so much.

---

### Post by tigrux on 2006-06-04
alias cd..="cd .."

---

### Post by givré on 2006-06-04
To have a more persistant solution, you should put your alias in ~/.bashrc

---

### Post by blimpyboy on 2006-06-04
By the way, it's 'customary' to in fact have the following aliases:

alias ..='cd ..'
alias ...='cd ..; cd ..'

Then you just use .. and ... to go up 1/2 dirs.
Also typing cd without any arguments takes you to your home dir.

---

### Post by fapapa on 2006-06-04
thanks all,

but none of these seem to solve my problem of being able to do **cd../..**. I guess I should be more specific: If I try to put the following alias in .bashrc or .bash_aliases . . .

alias cd../..='cd ..;cd ..'

I get *bash: alias: `cd../..': invalid alias name*. It has a problem with the first part of the alias, what I'm trying to alias, not the alias I'm trying to assign to it. Obviously bash and/or alias and/or linux have a problem with me trying to alias a command with a '/', as they probably try to interpret it as a directory delimiter. Perhaps there is a way to escape the '/' character so that it can be used in a command?

Again, if anybody has access to Mandriva out there, please have a look at your .bashrc, .bash_aliases, or the usual /etc/ files for me and let me know how they do this. Maybe a function?

Thanks again.

---

### Post by givré on 2006-06-04
[QUOTE=fapapa]
alias cd../..='cd ..;cd ..'
[/QUOTE]
This kind of alias is probably insupported. but i don't know why it should be more difficult to do that : cd ../.. than that cd../..

---

### Post by soze on 2006-06-05
[QUOTE=blimpyboy]By the way, it's 'customary' to in fact have the following aliases:

alias ..='cd ..'
alias ...='cd ..; cd ..'

Then you just use .. and ... to go up 1/2 dirs.
Also typing cd without any arguments takes you to your home dir.[/QUOTE]

I'm not sure about that. I've been working with Unix for over 25 years and I've never seen these aliases used.

I'm not a big fan of "over aliasing" in general. If you get overly dependent on a particular set of aliases, then you will be somewhat crippled when you hop on to a new system for the first time.

---

