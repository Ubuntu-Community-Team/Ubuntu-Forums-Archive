---
title: "TAB completon and mc problems"
date: 2009-07-29
forum: General Help
---

### Post by dmitriid on 2009-07-29
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

```

This is the server version.

When I ssh into it, I encounter the following problems:

**Problem 1**

tab completion behaves weird to the point of being unusable:
```

> cd ~/<press TAB>
-sh: <( compgen -d -- '/home/dmitriid/' ): No such file or directory

> vi ~/.<press TAB>
<( compgen -d -- '/home/dmitriid/.' ): No such file or directory
-sh: <( eval compgen -f -X '*.@(o|so|so.!(conf)|a|rpm|gif|GIF|jp?(e)g|
JP?(E)G|mp3|MP3|mp?(e)g|MPG|avi|AVI|asf|ASF|ogg|OGG|class|CLASS)' -- 
$(quote_readline $cur) ): No such file or directory

> nano ~/.<press TAB>
./              .bash_logout    .mc/            .viminfo
../             .bashrc         .mysql_history  
.aptitude/      .erlang.cookie  .profile        
.bash_history   .gitconfig      .ssh/

```


Is there a way to fix that?


**Problem 2**

I use mc quite a lot. I often do a Ctrl+O to hide panels and work in the shell. In my case:

1. Ctrl + O hides panels
2. Any keypress brings the panels back


Is there a way to fix that as well?



Thank you!

---

