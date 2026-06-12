---
title: "Command Line Outputs"
date: 2009-12-11
forum: General Help
---

### Post by HeretikSaint on 2009-12-11
I was wondering if there is a way to store the output of a bash command into a variable.  For instance, can I do
```
>pgrep conky
```
and temporarily store the output of that command into a variable and then use that variable in another command?

Here is a crude idea of what I'm talking about:
```

>pgrep conky --output=conkyvar
>25675
>sudo kill conkyvar

```

Can I do something like that?  Is it possible?

---

### Post by undecim on 2009-12-11
wrapping a command in `` will change it to a value for use with bash variables, etc.```
>CONKY_PID=`pgrep conky`
sudo kill $CONKY_PID
```

You can also use ```
sudo kill `pgrep conky`
``` if you only need it once (or heck, even just "sudo killall conky")

---

### Post by mobilediesel on 2009-12-11
> **HeretikSaint said:**
> I was wondering if there is a way to store the output of a bash command into a variable.  For instance, can I do
```
>pgrep conky
```
and temporarily store the output of that command into a variable and then use that variable in another command?

Here is a crude idea of what I'm talking about:
```

>pgrep conky --output=conkyvar
>25675
>sudo kill conkyvar

```

Can I do something like that?  Is it possible?

> **undecim said:**
> wrapping a command in `` will change it to a value for use with bash variables, etc.```
>CONKY_PID=`pgrep conky`
sudo kill $CONKY_PID
```

You can also use ```
sudo kill `pgrep conky`
``` if you only need it once (or heck, even just "sudo killall conky")

You can also do it like this:
```
>CONKY_PID=$(pgrep conky)
sudo kill $CONKY_PID
```

There's no functional difference as far as I know but it can sometimes help readability in large scripts.

---

### Post by HeretikSaint on 2009-12-11
Thank you very much.  This is definitely what I was looking for.

---

### Post by geirha on 2009-12-11
> **mobilediesel said:**
> You can also do it like this:
```
>CONKY_PID=$(pgrep conky)
sudo kill $CONKY_PID
```

There's no functional difference as far as I know but it can sometimes help readability in large scripts.

$( ) is the new and preferred syntax for command substitution, and there is a difference. The most significant being that escapes are less surprising, and it's easier to nest. Consider:

```
$(foo $(bar $(baz)))
# as opposed to
`foo \`bar \\\`baz\\\`\``

```

---

### Post by mobilediesel on 2009-12-11
> **geirha said:**
> $( ) is the new and preferred syntax for command substitution, and there is a difference. The most significant being that escapes are less surprising, and it's easier to nest. Consider:

```
$(foo $(bar $(baz)))
# as opposed to
`foo \`bar \\\`baz\\\`\``

```

That's a bigger difference than I thought! $( ) makes it WAY more readable! I'm glad that's the first way I learned about substitutions.

---

