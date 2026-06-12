---
title: "Need help with .bashrc"
date: 2011-02-05
forum: General Help
---

### Post by LanguidLegend on 2011-02-05
So I've started writing my .bashrc file and I'm trying to create an ls alias that prints: ls -aghx, except I'd like to edit out the 3rd and 4th fields (permissions for group and everyone else).
Does anyone know how that can be done?

Also, does anyone know of any other cool or useful things I can put in my .bashrc?

Thanks!

---

### Post by TeoBigusGeekus on 2011-02-06
[http://ubuntuforums.org/showthread.php?p=6924592]("http://ubuntuforums.org/showthread.php?p=6924592")

---

### Post by Stephen Morgan on 2011-02-06
When I type ls -aghx it doesn't show any permissions or groups.  Anyway you could try using awk, like this: ```
ls -lh | awk '{printf "%s %s\n", $8, $3}' -
``` That outputs the name of the file first, because that's the eighth field, then the file owner which is the third field. Just add a %s between the quotes for each field you want shown, list the fields after the comma following the quotes in the order you want them shown, leave out the ones you don't want.

---

### Post by whatthefunk on 2011-02-06
I like these ones

```
alias cp='cp -v -i'
alias rm='rm -i'
alias mv='mv -i'
alias today='date +"%A, %B %-d, %Y"'

```

The first three are more for safety than anything...they make it so that if you try to remove something or move/copy something to a file name that already exists a prompt come up to ask you if you really want to do that.  Could save you a major headache.

The fourth displays the date if I type "today."

I also have this in mine

```
export PATH=$PATH:/home/my_username/bin/programs

```

It makes it so the system looks for executable files in the listed directory so no matter where I am on my system, I can type in a command that I have written and it will execute it.

---

### Post by Habitual on 2011-02-06
> **LanguidLegend said:**
> Also, does anyone know of any other cool or useful things I can put in my .bashrc?

God yes.

This is IMO THE SINGLE BEST TIP I have ever learned.
**Leave man pages on the screen after exiting man** <page>
```
export LESS='FiX'
```

Other goodies:
**Reload .bashrc** without exiting bash:
```
alias reload='source ~/.bashrc'
```

**Colorized man pages**
```
export LESS_TERMCAP_mb=$'\E[01;31m'
export LESS_TERMCAP_md=$'\E[01;37m'
export LESS_TERMCAP_me=$'\E[0m'
export LESS_TERMCAP_se=$'\E[0m'
export LESS_TERMCAP_so=$'\E[01;44;33m'
export LESS_TERMCAP_ue=$'\E[0m'
export LESS_TERMCAP_us=$'\E[01;32m'
```

are good tips for any new user. (IMHO)

enjoy!

---

### Post by LanguidLegend on 2011-02-14
Thanks for all the responses, they helped a lot!

So right now, I'm trying to write in a shortcut for the unrar command which will take a file split into parts (i.e.: CompressedFile.part1.rar, CompressedFile.part2.rar, etc.), extract it, then remove the archive files.
(I've tried the -df switch for the unrar command, but it doesn't seem to work for some reason..)

This is what I have so far:
```
alias ext='unrar x `echo "$1"`; rm `echo "$1"`'
```
What I do is write in 'ext ', then 'Compre', press [Tab], which auto-fills the remainder to give me 'ext CompressedFile.part'. So 'CompressedFile.part' is the argument '`echo "$1"` onto which I want to somehow append '1.rar'.

I guess what I'm asking is how can I join echo commands to create the equivalent of '`echo CompressedFile.part1.rar`'?

---

### Post by VCoolio on 2011-02-14
Like this:
```
alias ext='for i in $(ls | grep -i $1); do unrar $i && rm $i; done'
```
As argument give part of the filenames of the archives. Adjust 'unrar' command as needed. Archive will be removed if unrarred successfully.
Edit: to explain:
"for i in" = "for everything that is returned on the following, which we call i"
"$(ls | grep -i $1)" = "which is any filename in this folder containing $1, non case sensitive"
"do unrar $i && rm $i" = "unrar that and if done successfully, remove"
Main sentence: for i in $(A); do B && C; done
$(A): A between $() so it executes this part first before execeting the rest; it needs this first.

---

### Post by LanguidLegend on 2011-02-14
> **VCoolio said:**
> Like this:
```
alias ext='for i in $(ls | grep -i $1); do unrar $i && rm $i; done'
```
As argument give part of the filenames of the archives. Adjust 'unrar' command as needed. Archive will be removed if unrarred successfully.
Edit: to explain:
"for i in" = "for everything that is returned on the following, which we call i"
"$(ls | grep -i $1)" = "which is any filename in this folder containing $1, non case sensitive"
"do unrar $i && rm $i" = "unrar that and if done successfully, remove"
Main sentence: for i in $(A); do B && C; done
$(A): A between $() so it executes this part first before execeting the rest; it needs this first.
I copied and pasted it into my .bashrc, re-entered bash, typed 'ext CompressedFile.part' and got this result:
bash: syntax error near unexpected token `CompressedFile.part'

---

### Post by GrouchyGaijin on 2011-02-14
Hi Guys,

Here is a dumb question. Where exactly in the .bashrc file do you add these things?  Does it matter?  Can I screw something up if I put it in the wrong place?

---

### Post by m_duck on 2011-02-14
Generally, wherever you like. If, however, you refer to a function, you need that function to be above the point at which you are referring to it from, likewise with variables.

I typically put aliases et al in a separate file, and so add one line to ~/.bashrc to reference said file, and make my changes in the new file. E.g. if my file with aliases in was ~/.bash_aliases, in ~/.bashrc I would add:```
[ -f $HOME/.bash_aliases ] && . $HOME/.bash_aliases
```The above checks if the ~/.bash_aliases file exists, and if it does, sources it to allow the use of the shiny new aliases.

---

### Post by GrouchyGaijin on 2011-02-14
Thank you Mr. Duck.

---

### Post by VCoolio on 2011-02-15
> **LanguidLegend said:**
> I copied and pasted it into my .bashrc, re-entered bash, typed 'ext CompressedFile.part' and got this result:
bash: syntax error near unexpected token `CompressedFile.part'

Hmm. Dunno. It works as a little script:```
#!/bin/bash
for i in $(ls | grep -i $1); do
  echo $i
done 
```

Try that, replace echo with "unrar $i && rm $i" if it works.

---

