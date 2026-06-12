---
title: "Where is the &quot;alias&quot; command!!??"
date: 2011-07-20
forum: General Help
---

### Post by SOMDdan on 2011-07-20
I am running Lucid, and wanted to find the options for the "alias" command. When I enter "alias" I get a list of aliases, but I cant find **anything** more about the command. **Man alias** has no entry, **whereis **gives nothing, **which **gives nothing, **whatis alias** gives "nothing appropriate." I can't find it in **/bin, /sbin **or **/usr/sbin. **It works, I can set an alias, but there is **no informati****on** about it anywhere? What gives??

---

### Post by MG&amp;TL on 2011-07-20
[http://linuxcommand.org/wss0020.php#aliases](http://linuxcommand.org/wss0020.php#aliases)

Here should get you started. Great site for general terminal/bash script stuff.

---

### Post by MG&amp;TL on 2011-07-20
You can edit stuff manually in gedit, btw.

---

### Post by SoFl W on 2011-07-20
Check out your ".bashrc" file, some people prefer a ".bash_alias" file to separate aliases.

From the .bashrc file: > # Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/bash in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fiYou might also be interested in functions which can be set up to execute several commands.

---

### Post by sisco311 on 2011-07-20
alias is a shell builtin, you probably use bash, so check out `man bash' and search for `alias' or `SHELL BUILTIN COMMANDS':
```
man bash | less +/"^ +alias \["
```

You may also want to check out [Greg's Wiki]("http://mywiki.wooledge.org/") for a good bash guide.

---

### Post by SOMDdan on 2011-07-20
That link only told me the one thing that I already knew: how to set an alias. My original questions still stand: if it is a working command then where is the man page, binary file for the command, what are the options, etc. 

( I don't mean to sound ungrateful for you trying to answer my questions by posting the link, it is just that it seems so unusual to not find any information about a linux shell command like that)

---

### Post by SOMDdan on 2011-07-20
D'oh! I forgot about shell built-ins! Thanks for the FAST replies!

---

### Post by MG&amp;TL on 2011-07-20
Sorry, misread the question. Looks like you've got at least two answers now!

---

### Post by SoFl W on 2011-07-20
I don't think there are any options.

---

### Post by sisco311 on 2011-07-20
> **SOMDdan said:**
> D'oh! I forgot about shell built-ins! Thanks for the FAST replies!

```
 ________________________________
/ You are welcome... to kiss my  \
\ copper-planted @$$, Homer!     /
 --------------------------------
   \
    \
     ( )
      H
      H
     _H_
  .-'-.-'-.
 /         \
|           |
|   .-------'._
|  / /  '.' '. \
|  \ \ @   @ / /
|   '---------'
|    _______|
|  .'-+-+-+|
|  '.-+-+-+|
|    """""" |
'-.__   __.-'
     """

```

/joke


No problem!

---

