---
title: "Conceptual question"
date: 2010-09-20
forum: General Help
---

### Post by Atamisk on 2010-09-20
i'm trying to teach myself how linux handles I/O streams (mostly for kicks). Something odd happened when i ran

```
 cat /dev/stdout > /dev/dsp 
```This code really should do nothing, because there's no real output to stdout while the command is active, right?

Well, when i ran it, i got a slightly delayed stream from my MICROPHONE. odd, eh?

My main question is: why?

---

### Post by papibe on 2010-09-20
I don't know how to answer that, but...

If you're just starting, I would advice for now, NEVER use "> /dev/xxx". I could be deadly. In fact you should read this first:
[INDENT][ATTENTION ALL USERS: Malicious Commands]("http://ubuntuforums.org/announcement.php?f=331")[/INDENT]

As for tutorials here's a couple:
[INDENT][1. I/O Redirection]("http://linuxcommand.org/lts0060.php")
[2. I/O Redirection]("http://tldp.org/LDP/abs/html/io-redirection.html")[/INDENT]

Regards.

---

### Post by Atamisk on 2010-09-20
Thanks for the tutorials, those should help a bit. 

However, i am aware of the power contained in /dev directory. when i say just starting out, i mean really getting into the nuts and bolts of linux. i've been arond linux for roughly 2 years.

---

### Post by papibe on 2010-09-20
If you want to continue your holly search :P for the nuts and bolts, I would recommend this tutorial:

[INDENT][Advanced Bash-Scripting Guide]("http://tldp.org/LDP/abs/html/index.html")[/INDENT]

Regards.

---

### Post by Atamisk on 2010-09-21
:guitar: that's epic. thanks!


Now, anyone got a clue as to why i got microphone output when i redirected stdout to my speakers?

EDIT: why is it possible? when i redirect stdout to a file, it generates an error....

---

