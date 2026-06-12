---
title: "Most replaces more?"
date: 2010-11-16
forum: General Help
---

### Post by herda05 on 2010-11-16
So I've got Ubuntu 10.04.1 LTS installed and I issue a more foo. I then see:

```
dan@arrakis:~$ more foo
The program 'most' is currently not installed.  You can install it by typing:
sudo apt-get install most
```

I do a which more:

```
dan@arrakis:~$ which more
/bin/more
dan@arrakis:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```



So what's the deal? Why doesn't more work out of the box with Ubuntu 10.04.1? Who's pushing "most" on me and why?

```
dan@arrakis:~$ touch foo
dan@arrakis:~$ echo aasdasidalkdlna > foo
dan@arrakis:~$ /bin/more foo
aasdasidalkdlna
dan@arrakis:~$ more foo
The program 'most' is currently not installed.  You can install it by typing:
sudo apt-get install most

```

More importantly, how do I get more working without having to install most? It's in my path, so just exectuing more should work.


[SOLVED] The problem was bash_aliases.

---

### Post by bodhi.zazen on 2010-11-16
My guess is you are using a custom ~/.bashrc (or similar) file which specifies your pager as most.

Edit ~/.bashrc and specify your pager as more.

FYI: The advantage of most is that man pages appear in color (if that sort of thing appeals to you).

```
pager='/bin/more'
```

---

### Post by sisco311 on 2010-11-16
Did you add any new aliases recently?

Most likely more is an alias for most (no pun indeed).

To temporarily bypass an alias precede the command with a \:
```
\more foo
```
or you could list the aliases:
```
alias
alias more
```

If it's an alias, then search the bash init files to find where it's defined:
```
grep "alias more" /etc/profile  /etc/bash.bashrc ~/.bash_profile  ~/.bashrc
```

---

### Post by herda05 on 2010-11-16
It was bash_aliases. I just copied on up from another machine and it had settings for more and less.

Thanks guys.

---

### Post by sisco311 on 2010-11-16
Cool! You're welcome!

You can mark this thread as [SOLVED] from the [COLOR="Red"]Thread Tools[/COLOR] menu; it's at the top of the page. Thanks!

---

