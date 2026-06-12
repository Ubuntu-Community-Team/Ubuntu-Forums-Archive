---
title: "Bash script help"
date: 2010-04-07
forum: General Help
---

### Post by patman0623 on 2010-04-07
I'm trying to run a bash script on my computer, because Firefox doesn't properly close when I press Ctrl-Q (which I need to do fairly often, as Flash video can inexplicably lose sound capability)

An output of terminal:
```
patrick@patrick-laptop:~/Desktop$ ps -A|grep firefox
 6242 ?        00:00:00 firefox
 6251 ?        00:30:23 firefox-bin

```

An output of me parsing this text:
```
patrick@patrick-laptop:~/Desktop$ x=(`ps -A|grep firefox`)
patrick@patrick-laptop:~/Desktop$ echo $x
6242

```

So with this in hand, I'm hoping to run a script to terminate Firefox:
```
zenity --question --text "Terminate Firefox?"
if [ $? -eq -0 ]
 then
 x=(`ps -A|grep firefox`); kill $x; x=(`ps -A|grep firefox`); kill $x;
fi
```

But the output:
```
killff.sh: 7: Syntax error: "(" unexpected (expecting "fi")
```

What am I doing wrong here? I'm a total n00b with bash scripts; I grew up on .bat files on MSDOS.

---

### Post by dcstar on 2010-04-07
> **patman0623 said:**
> I'm trying to run a bash script on my computer, because Firefox doesn't properly close when I press Ctrl-Q (which I need to do fairly often, as Flash video can inexplicably lose sound capability)

An output of terminal:
```
patrick@patrick-laptop:~/Desktop$ ps -A|grep firefox
 6242 ?        00:00:00 firefox
 6251 ?        00:30:23 firefox-bin

```

An output of me parsing this text:
```
patrick@patrick-laptop:~/Desktop$ x=(`ps -A|grep firefox`)
patrick@patrick-laptop:~/Desktop$ echo $x
6242

```

So with this in hand, I'm hoping to run a script to terminate Firefox:
```
zenity --question --text "Terminate Firefox?"
if [ $? -eq -0 ]
** then**
 x=(`ps -A|grep firefox`); kill $x; x=(`ps -A|grep firefox`); kill $x;
fi
```

But the output:
```
killff.sh: 7: Syntax error: "(" unexpected (expecting "fi")
```

What am I doing wrong here? I'm a total n00b with bash scripts; I grew up on .bat files on MSDOS.

Get rid of the "then".

---

### Post by patman0623 on 2010-04-07
> **dcstar said:**
> Get rid of the "then".

```
killff.sh: 6: Syntax error: "(" unexpected (expecting "then")

```

---

### Post by dcstar on 2010-04-07
> **patman0623 said:**
> ```
killff.sh: 6: Syntax error: "(" unexpected (expecting "then")

```

Try:

```
zenity --question --text "Terminate Firefox?"
if [ $? -eq -0 ] ;
 then
 x=(`ps -A|grep firefox`)
 kill $x
 x=(`ps -A|grep firefox`)
 kill $x
fi
```

The best way to find out how to use shell scripts is to look at the existing ones in your system folders (like /etc/init.d)

---

### Post by patman0623 on 2010-04-07
I'm actually trying all of the above, and nothing is working; I'm formatting it just like I see in the files in the system folder.

I'm quite sure it has something to do with the parentheses, as when I remove them, the syntax becomes valid, though obviously the function doesn't work.

---

### Post by matchett808 on 2010-04-07
if [ condition ]; then
do something
fi
  should do the trick, try that

---

### Post by falconindy on 2010-04-07
if [ $? -eq **-0** ]

Just zero, please. You're not testing for negative zero.

---

### Post by epicoder on 2010-04-07
Try:
```

zenity --question --text "Terminate Firefox?"
if [ $? -eq 0 ]
then
  kill `ps -A|grep firefox`; kill `ps -A|grep firefox`
fi

```

---

