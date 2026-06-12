---
title: "Displaying man pages"
date: 2012-03-14
forum: General Help
---

### Post by andna on 2012-03-14
Hello

On my previous system, openSUSE, when I invoked for example 'man open', it asked me which page I wanted to view, but on Xubuntu when I type 'man open' I get page about 'openvt', but when I type 'man 2 open' then I get man page about this system call, what can I do, to make man ask me about, which page I want to view?

---

### Post by raja.genupula on 2012-03-14
hi just type [COLOR="Blue"]man[/COLOR] , then it will prompt for what page you wanna view .

---

### Post by andna on 2012-03-14
As I wrote in my previous post:
'man open' - opens page about 'openvt'
'man 2 open' - opens page about system call

I want man to list me possible choices, not to choose for me which man page should be displayed, unless I tell him to like in 'man 2 open'.

---

### Post by raja.genupula on 2012-03-14
sorry i am not getting you . could you please explain some more . 
you mean ... ? sorry i am not getting .

EDIT: you want options means , you looking for this ?
**man -k <search term>**

it will give all possibilities of that word you searched

---

### Post by andna on 2012-03-14
Maybe misunderstanding comes from my bad usage of 'page', let me rephrase my question.

Here are man sections in Unix like systems:

1	General commands
2	System calls
3	Library functions, covering in particular the C standard    library
4	Special files (usually devices, those found in /dev) and drivers
5	File formats and conventions
6	Games and screensavers
7	Miscellanea
8	System administration commands and daemons

When I type:
'man open'
it automatically open section (1) and man page about 'openvt', I need to manually specify that I want section 2 when I want to view page about 'open' which is system call. On my older linux, when I typed 'man open' I got asked, from which section of manual I want to view page about 'open', so I could do:
'man open'
and I could choose which section of manual I want to view.

---

### Post by winh8r on 2012-03-14
Look here for full manpages database with search function:

[http://manpages.ubuntu.com/]("http://manpages.ubuntu.com/")

---

