---
title: "Trying to use at  to end exaile at a certain time."
date: 2009-07-27
forum: General Help
---

### Post by AgentWiggles on 2009-07-27
Here's my command

eric@eric-desktop:~$ at 2am today kill $(pgrep exaile)

And here's my error 

syntax error. Last token seen: k
Garbled time


I'm trying to set it up so I can listen to music while i fall asleep, but not all night. Last time I just used "sudo -h shutdown 60" but that seems a rather unwieldy solution to this problem and it makes my speakers make weird popping sounds.

Either way, can someone help me out? And I won't be surprised when I'm informed I don't properly understand the use of the kill command either, it seemed confusing to me so I just threw in an example I knew would work.

---

### Post by vruum on 2009-07-27
this may not exactly fit the one line elegance but just typing ```
at 2am today
``` gives you an at prompt where you can type all jobs you want executed at that time (eg. kill $(pgrep exaile)), hit ctrl-d to escape the at prompt,

---

### Post by Baelus on 2009-07-27
Found this:

[http://www.nabble.com/"at"-command-examples---usage-td12257213.html]("http://www.nabble.com/"at"-command-examples---usage-td12257213.html")

"at" reads from stdin, so try:

```
echo "kill $(pgrep exaile)" | at 2am today
```

---

