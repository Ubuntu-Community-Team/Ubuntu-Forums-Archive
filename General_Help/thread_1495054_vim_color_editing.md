---
title: "vim color editing"
date: 2010-05-27
forum: General Help
---

### Post by l3ecl on 2010-05-27
I would like to use vim in order to take notes for class. How do I tag/highlight specific words and put them into abstract categories? For example:

[COLOR=Black]1. if i was typing a summary it would be in pink.[/COLOR]
[COLOR=Magenta]this is summary 1.
this is summary 2.[/COLOR]

2.) if i was doing definitions it would be in red.
[COLOR=Red]ourorboros -  a  circular symbol of a snake...[/COLOR]

---

### Post by ibuclaw on 2010-05-27
> **l3ecl said:**
> I would like to use vim in order to take notes for class. How do I tag/highlight specific words and put them into abstract categories? For example:

[COLOR=Black]1. if i was typing a summary it would be in pink.[/COLOR]
[COLOR=Magenta]this is summary 1.
this is summary 2.[/COLOR]

2.) if i was doing definitions it would be in red.
[COLOR=Red]ourorboros -  a  circular symbol of a snake[/COLOR]

Quick crash course guide to syntax highlighting:

1) Create prerequisite directories
```
mkdir -p ~/.vim/{ftdetect,syntax}
```

2) Create syntax file
```
vi ~/.vim/syntax/notes.vim
```
This is a generic template, that has the spec you have asked for (sortof)
```

[COLOR="blue"]" Vim syntax file for taking notes for class

" Quit when a syntax file was already loaded[/COLOR]
if exists("b:current_syntax")
  finish
endif


[COLOR="blue"]" Keyword definitions
" keywords = singular words to match
"   ie: syn keywords if_this_and_that   if this and that
" match = regular expression to match
"   ie: syn match allNumbers "\<\d[0-9]*\>"
"[/COLOR]
syn match noteSummary         "^\s*this.*\."
syn match noteDefinition      "^[A-Za-z]*\s-\s.*$"


[COLOR="Blue"]" Possible cterm colors
" Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta,
" Brown, DarkYellow, LightGray, LightGrey, Gray, Grey,
" DarkGray, DarkGrey, Blue, LightBlue, Green, LightGreen,
" Cyan, LightCyan, Red, LightRed, Magenta, LightMagenta,
" Yellow, LightYellow, White[/COLOR]
hi Summary                      ctermfg=Magenta
hi Definition                   ctermfg=DarkRed


[COLOR="blue"]" The default highlighting.
"[/COLOR]
hi def link noteSummary         Summary
hi def link noteDefinition      Definition


[COLOR="blue"]" What type of syntax highlight we are.
"[/COLOR]
let b:current_syntax = "notes"

```

3) Create filetype detection file
```
vi ~/.vim/ftdetect/syntax.vim
```
And tell vim that files to match the name *.notes
```

"
" Custom syntax highlight defined here
" Syntax files go in ~/.vimrc/syntax
"

au BufRead,BufNewFile *.notes  set filetype=notes

```

4) Create a new file with the suffix ".notes" to test the new syntax highlighting
```
vi test.notes
```
And some dummy text:
```

this is summary 1.
blah blah blah blah.
this is summary 2. Highlighting stops after last period in line. :)
more blahs, and a few bah humbugs.

ourorboros - a circular symbol of a snake

word - Definition of word. Highlighting stops after end of line
Hello World!

```

Should be enough for you to play around and get started.

Regards
Iain

---

### Post by bodhi.zazen on 2010-05-27
Dang it [[COLOR=#D40000]**ibuclaw**[/COLOR]]("http://ubuntuforums.org/member.php?u=490875") you are too fast =)

---

### Post by ibuclaw on 2010-05-27
> **bodhi.zazen said:**
> Dang it [[COLOR=#D40000]**ibuclaw**[/COLOR]]("http://ubuntuforums.org/member.php?u=490875") you are too fast =)

:popcorn:

---

### Post by l3ecl on 2010-05-27
WOW, that is so damn awesome! this is why i love ubuntu. its like you guys can do anything, except maybe get me laid =D. im sure theres a script for that somewhere.

---

### Post by ibuclaw on 2010-05-27
> **l3ecl said:**
> WOW, that is so damn awesome! this is why i love ubuntu. its like you guys can do anything, except maybe get me laid =D. im sure theres a script for that somewhere.

```
man woman
```
Should get you in the right direction. ;)

Good Luck with your vi editing!

---

### Post by filosophem on 2010-06-01
> **ibuclaw said:**
> ```
man woman
```Should get you in the right direction. ;)

Good Luck with your vi editing!

well it gave me this: "No manual entry for woman".

Ibuclaw, are you sure it's the good command ??? :oops:

---

