---
title: "Can I fix my seagate with ubuntu?"
date: 2009-12-29
forum: General Help
---

### Post by Han Solo on 2009-12-29
I have a seagate barracuda 7200.11 that bricked for about a month now. But I later found that they have a firmware problem that needs to be resolved. I know what I have to input to the hyperterminal but when I try to plug it in to my computer win xp doesn't recognize any new devices. So I was wondering if I could the same operation with ubuntu. I am not too familiar with linux terminal or XP's hyperterminal for that manner. For reference I attempting to follow this [http://www.youtube.com/watch?v=29FztWJVxbM](http://www.youtube.com/watch?v=29FztWJVxbM) and the links that she provides.I am in the process of upgrading ubuntu to 9.04 and currently firefox can't display any sound for youtube etc. I am hoping that I could get sound back with 9.04. Pardon my ignorance if any.

---

### Post by falconindy on 2009-12-29
Minicom or Kermit are valid replacements to HyperTerminal. You'll want to look at the man page associated with the program to determine how to set the flow control and baud rate of the connection. If you were feeling brave, you could just echo the commands directly to the device file (e.g. /dev/ttyS0) the hard drive is attached to.

---

### Post by Han Solo on 2009-12-29
As I am new to this my question would be once I get these hyperterminal replacements would I get that pop up device installation that one gets using win? I ask this since in my previous attempts I wasn't able to get any recogination of the drive. And lastly what's echo?

---

### Post by doas777 on 2009-12-29
> **Han Solo said:**
> As I am new to this my question would be once I get these hyperterminal replacements would I get that pop up device installation that one gets using win? I ask this since in my previous attempts I wasn't able to get any recogination of the drive. And lastly what's echo?

no probably no software install. echo just prints what you tell it to. eg
```

karmic:~$ echo hello
hello

```

if you want to pipe a commands output into another command or redirect the output to a file or device, you use echo.

---

### Post by Han Solo on 2010-03-01
Nevermind HDD was unbricked. Had to use hyperterminal commands. Thanks anyway.

---

