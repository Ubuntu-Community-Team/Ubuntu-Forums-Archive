---
title: "recalling a command"
date: 2010-01-14
forum: General Help
---

### Post by 0xeb on 2010-01-14
Hello

In Windows command prompt, one can type a part of a command that was already entered, and then press F8 (repeatedly) and the command history beginning with what was typed before start on showing.

so supposed the history contains:

kill $(pidof abc)
kill $(pidof abc2)
kill $(pidof abc3)

Anything similar in Ubuntu?

I tried typing couple of commands, then pressed CTRL+R and it matched the first "kill" but how to have it suggest the other "kill" commands?

Thanks,
Elias

---

### Post by wojox on 2010-01-14
Keep pressing Ctrl + r. ;)

---

### Post by konqueror7 on 2010-01-14
> **0xeb said:**
> Hello

In Windows command prompt, one can type a part of a command that was already entered, and then press F8 (repeatedly) and the command history beginning with what was typed before start on showing.

so supposed the history contains:

kill $(pidof abc)
kill $(pidof abc2)
kill $(pidof abc3)

Anything similar in Ubuntu?

I tried typing couple of commands, then pressed CTRL+R and it matched the first "kill" but how to have it suggest the other "kill" commands?

Thanks,
Elias

you may want to look at
```
history
```
to look your previous commands, combine it with *less* to be more readable,```
history 20 | less
```
this will show last 20 commands.

in case you want to execute the last command, you may use '!', so for example i have typed,
```
!ls
``` this will execute the last 'ls',,,

---

### Post by nothingspecial on 2010-01-14
If you know part of the command, you can pipe it through grep

```
history | grep apt-cache
```

for example

---

### Post by efflandt on 2010-01-14
I have been using Linux since about 1995.  And as long as I can remember, bash has been able to scroll back through history of commands using the up cursor key (or down cursor to go forward if you went back too far).

However, it you have more than one terminal open, the history of another still opened terminal may not show up on a different terminal.  Although, reopening a single terminal/console that was closed should be able to bring up previous history.

---

### Post by kaibob on 2010-01-14
Another option. After displaying the history, you can execute any command by entering an exclamation point followed by the number shown for the command in the history listing (e.g. !495).

---

### Post by 0xeb on 2010-01-14
thanks alot all for the replies, very helpful of you!

keep pressing ctrl+r is what i want.

---

