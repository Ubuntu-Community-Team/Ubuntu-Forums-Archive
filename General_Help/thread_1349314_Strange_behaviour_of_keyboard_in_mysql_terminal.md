---
title: "Strange behaviour of keyboard in mysql terminal"
date: 2009-12-08
forum: General Help
---

### Post by Queequeg on 2009-12-08
For a while now, (¿maybe since I upgraded to Karmic?) the mysql console has been behaving in the most annoying way. *Delete* key does not delete, but provides a ~ instead. *Back* key effectively deletes previous character, but it then doubles the next one, making impossible to edit any previous query.
I do a lot of work on mysql terminal, so this is bugging me beyond description. Keyboard works as expected everywhere else.

I have no idea of what's going on.

Please help.

---

### Post by karlwilbur on 2009-12-09
This is a bug in the version of libedit bundled with MySQL. Recompiling MySQL using --without-libedit configure option will fix it. 

[http://bugs.mysql.com/bug.php?id=33091](http://bugs.mysql.com/bug.php?id=33091)

I am still looking into a possible fix without the need to recompile.

---

### Post by karlwilbur on 2009-12-09
_Non-recompile solution:_

```

sudo apt-get install rlwrap

```

Then you can do this:
```

rlwrap -a mysql -u root -p

```

or, so you dont have to type  "[FONT="Courier New"]rlwrap -a[/FONT]" everytime, this:
```

alias mysql='rlwrap -a mysql'
mysql -u root -p

```

For persistence, you can add  "[FONT="Courier New"]alias mysql='rlwrap -a mysql'[/FONT]"  to your  [FONT="Courier New"]~/.bash_profile[/FONT].

```

cp ~/.bash_profile{,.bak}; echo "alias mysql='rlwrap -a mysql'" >> ~/.bash_profile; source ~/.bash_profile 

```

EDIT:
Actually, aliases don't really belong in the [FONT="Courier New"]~/.bash_profile[/FONT]. So, what you **should** do is uncomment the aliases section in your [FONT="Courier New"]~/.bashrc[/FONT] so that this:
```

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

```
becomes this:
```

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```

Then, put your aliases in into [FONT="Courier New"]~/.bash_aliases[/FONT]
```

cp ~/.bash_aliases{,.bak} 2> /dev/null; echo "alias mysql='rlwrap -a mysql'" >> ~/.bash_aliases; source ~/.bash_profile 

```

(NB: the following is not meant to grant a complete understanding of [FONT="Courier New"]bash[/FONT] config files. For a more accurate explanation of the difference between [FONT="Courier New"]~/.bash_profile[/FONT] and [FONT="Courier New"]~/.bashrc[/FONT], please read the [FONT="Courier New"]bash[/FONT] man page)

[FONT="Courier New"]~/.bashrc[/FONT] is loaded for **non**-interactive shells
[FONT="Courier New"]~/.bash_profile[/FONT] is loaded for interactive shells.
I have code in my [FONT="Courier New"]~/.bash_profile[/FONT] which loads my [FONT="Courier New"]~/.bashrc[/FONT] and my [FONT="Courier New"]~/.bashrc[/FONT], in turn loads [FONT="Courier New"]~/.bash_aliases[/FONT]. This allows for quick and easy management of aliases.

Snippet from my [FONT="Courier New"]~/.bash_profile[/FONT]:
```

if [ -f ~/.bashrc ]; then
   source ~/.bashrc
fi

```


References:
[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/472156](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/472156)
[http://ubuntuforums.org/showthread.php?t=1147183](http://ubuntuforums.org/showthread.php?t=1147183)

---

### Post by Queequeg on 2009-12-15
Thanks a lot! Problem solved!
I may try recompiling later in my life :) but as the second solution works so well I'll stick by it for the moment.

---

