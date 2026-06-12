---
title: "store result in a variable?"
date: 2012-07-30
forum: General Help
---

### Post by kosddww on 2012-07-30
Hi all i have basically one question.
Is it possible to place the result from ifocnfig (or a part of result) in a variable?

Couldn't find the answer in this form dos somone know the answer.
Thanks

---

### Post by steeldriver on 2012-07-30
in general, bash lets you return the output of a command using $(command), e.g.

```
$ result=$(ifconfig)
$ echo $result
```it's probably not very useful unless you select out part of the output (using grep for example)

---

### Post by asmoore82 on 2012-07-30
For the Bash shell, the ancient syntax for this is the backticks (the left quote usually above the tab key).

But the more modern syntax is the $( ... ) construct:

```
[COLOR="Purple"]#old and deprecated[/COLOR]
variable=`ifconfig eth0`

[COLOR="Purple"]#new-er and shiny[/COLOR]
variable=$( ifconfig eth0 )
```

As mentioned above, it can be difficult to parse after the fact. Also, if you try to parse it afterwards, you'll quickly pick up on some of the wonders of quoting variable references...

```
**$ echo $variable**
eth0 Link encap:Ethernet HWaddr 00:90:f5:aa:af:e5 UP BROADCAST MULTICAST
MTU:1500 Metric:1 RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0
txqueuelen:1000 RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:35 Base address:0xe000
**$ echo "$variable"**
eth0      Link encap:Ethernet  HWaddr 00:90:f5:aa:af:e5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:35 Base address:0xe000
```

The first command, missing the quotes, creates the illusion that the $( ... ) command failed to capture properly, but in reality, the shell parser itself will eat whitespace on a variable when it is referenced; if the quotes are omitted. Long story short (too late :P), it's almost always a good idea to quote all variable references.

---

