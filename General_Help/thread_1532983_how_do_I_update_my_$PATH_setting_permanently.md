---
title: "how do I update my $PATH setting permanently?"
date: 2010-07-17
forum: General Help
---

### Post by engine on 2010-07-17
Clean installation of 10.04 after a hard disk crash ... so long since the last new install there are some things I've completely forgotten how to do.

One question per post, so the question in this one is "how do I update my $PATH setting?" I've installed a new app in its own folder (four or five programs) under usr/local/bin &#8210; if that's not where the executable should be, please correct me &#8210; and want to be able to run it from the command line in whichever directory the data files live in.

Thanks in advance!

---

### Post by WorMzy on 2010-07-17
Stick the following in your ~/.bashrc file:

```
PATH=$PATH:/usr/local/bin
```

---

### Post by engine on 2010-07-17
> **WorMzy said:**
> Stick the following in your ~/.bashrc file:

```
PATH=$PATH:/usr/local/bin
```

By gum &#8210; it worked! It's not your advice I doubted, it's my track-record with solving even the simplest Ubuntu problem <g>

Thanks.

---

### Post by engine on 2010-08-01
I'll append this here before starting a new thread, because it feels to me like the same problem.

I've updated $PATH as WorMzy suggested, and now I can run the command from a terminal no matter what the current directory is; good. However and less good ... if I try the familiar :! {command} from gvim, in a directory where the command works from a terminal, I get the message /bin/bash: {command} not found

It slows me down just enough to be really annoying if I have to change my habits and switch from gvim to a terminal every time I want to run the command. Helpful suggestions gratefully received!

---

### Post by AlphaLexman on 2010-08-01
~/.bashrc is only read for interactive shells. put the 
```
PATH=$PATH:/usr/local/bin 
```in ~/.profile instead. It is read when you login.

---

