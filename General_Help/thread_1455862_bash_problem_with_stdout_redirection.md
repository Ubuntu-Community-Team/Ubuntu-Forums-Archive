---
title: "bash problem with stdout redirection"
date: 2010-04-16
forum: General Help
---

### Post by Ali Kante on 2010-04-16
Hi,

I have a problem with the output of netcat. nc uses stderr for default output, so I have to redirect stdout like in this command:

nc -znv -w 3 192.168.11.220 20-22 2>&1 | grep open > output220

which works pretty fine...

but it won't do as I like, when I try to scan the whole 9 yards:
nc -znv -w 3 192.168.11.220 1-65535 2>&1 | grep open > output220

Then the output220 file will have zero bytes and no content respectively.

I have no idea what happens here. Maybe there's a buffer limit here that kills the output, but stderr is not buffered. I already tried puzzling around with xargs and tee, but with no further succes.

I really want to know, what's going on here, not absolutely how to scan that server. I can use nmap and other tools and maybe other ways with nc. What I really want to know is: 

What's going on here? :confused:

really appreciate any hint, clue and/or help.

---

### Post by jpaugh64 on 2010-04-16
Well, I can say a few things that might help. First of all, I checked the info page of bash, and found that '|&' can be used to pipe stderr, which is a handy shortcut. Secondly, I tried
"nc.traditional -znv -w 3 192.168.X.X 1-65535 2>&1 | grep open > output220" and it worked fine for me. Even found a few ports I thought were closed.

---

### Post by Ali Kante on 2010-04-17
That's strange. I tried it on a different machine with the same result: nothing. :-(

---

