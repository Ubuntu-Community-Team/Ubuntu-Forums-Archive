---
title: "CLI command write."
date: 2010-01-28
forum: General Help
---

### Post by NFblaze on 2010-01-28
I am SSH'd into my desktop computer via the internet thru my laptop. I want to write a message BACK to my laptop using *write* on my desktop. I've *w*, and the output I get is 

```

nfb@MD-Desktop:~$ w
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
nfb      tty1     -                16:45    4:34m  0.32s  0.23s -bash
nfb      tty7     :0               17:13    4:43m 10:49   0.04s /usr/bin/lxsession -s LXDE
nfb      pts/1    c-98-218-129-248 21:09   10:41   0.24s  0.24s -bash
nfb      pts/2    :0               21:25    0.00s  0.23s  0.00s w

```

pts/1 is my laptop.

So I tried

```
nfb@MD-Desktop:~$ write rue pts/1 "stuff that needs to get written"
```

It did not succeed, is there something I'm doing wrong here...or is it because pts/1 isnt a terminal? 

*(Also on a side note what does pts stand for?)*

---

### Post by x33a on 2010-01-28
firstly you need a terminal open at the other end. then do
```

write rue pts/1

```note: pts/1 needs to be a terminal.

now you can type all the messages you want, and when you want to finish the message press ctrl-d.

also, pts means pseudo terminal slave.

try
```
man pts
```for more info.

---

### Post by NFblaze on 2010-01-28
Thank you very much x33a. Indeed that did work. Looks like I shouldnt have had the text to be sent on the same line. 

Thanks. It was fun. I really do like messing with this OS over the net. Thanks again.

---

