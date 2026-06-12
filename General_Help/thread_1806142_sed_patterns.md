---
title: "sed patterns"
date: 2011-07-17
forum: General Help
---

### Post by maclenin on 2011-07-17
I am trying to create a sed script to append a number to a block of text within a config file.

A. block(s) of text:
```
Host A
 HostName

Host B
 HostName

Host C
 HostName
```

B. block of text with number appended:
```
Host A
 HostName **number**
```

I tried the following...
```
sed "s/Host A\n HostName/& number/" -i ~/config
```
...but can't seem to figure out how to define the block of text properly.

Thanks for any suggestions.

---

### Post by Vaphell on 2011-07-17
sed by default works on per-line basis, so putting multiline pattern there won't trigger any matches. Either match HostName alone or read [http://www.grymoire.com/Unix/Sed.html#uh-51](http://www.grymoire.com/Unix/Sed.html#uh-51) or similar sources for more info on sed

edit: or go with perl
```
echo $'Host A\n HostName\n\nHost B\n HostName' | perl -0777 -pe 's/(Host.*\n HostName)/\1 number/g'
Host A
 HostName number

Host B
 HostName number

```

---

### Post by maclenin on 2011-07-17
Thanks, **Vaphell**. I had found the sed reference you indicate. The issue is HostName is not unique, in and of itself - only becoming so when identified as part of a Host A, Host B or Host C (bloc), respectively - to which I then need to assign unique (Host A, B or C) numbers (ip addresses). I'll report back on what I find.

edit: looking at "Pattern Matching Across More than 1 Line" on [this page]("http://www.panix.com/~elflord/unix/sed.html").

---

### Post by maclenin on 2011-07-17
Solved:

After a bit of additional looking, it seems the **N** command incorporates \n (or newline) into sed's (otherwise single-line - i.e. \n ignoring) "pattern space", allowing for multi-line / "block of text" searches....

The resulting code is tantalizingly simple (in my case):

```
sed '**N**; s/Host A\n HostName/& number/' -i ~/config
```

Thanks, **Vaphell**, for the link and to these additional sources:

[source1]("http://www.unix.com/shell-programming-scripting/20049-paragraph-sed.html")
[source2]("http://en.wikipedia.org/wiki/Sed")
[source3]("http://systemnotesorg.blogspot.com/2007/04/using-bash-and-sed-to-modify-text-file.html")

---

