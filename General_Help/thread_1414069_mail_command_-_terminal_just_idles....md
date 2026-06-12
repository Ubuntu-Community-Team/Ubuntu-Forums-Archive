---
title: "mail command - terminal just idles...?"
date: 2010-02-23
forum: General Help
---

### Post by d3v1150m471c on 2010-02-23
I tried testing mail from the command line as I've never used it.

```

mail -s "hello world" myemail@yahoo.com

```

It sits there and does nothing. I waited ten minutes...still nothing. Killed the firewall, same gig. Obviously this is user error but what I'm doing wrong is unknown to me. Any suggestions?

---

### Post by d3v1150m471c on 2010-02-23
I tried using sendmail and that's not working either... hmmz

---

### Post by d3v1150m471c on 2010-02-24
bravo uniform mike papa

---

### Post by falconindy on 2010-02-24
You need to establish an MTA like postfix or courier in order to send mail from your command line.

---

### Post by d3v1150m471c on 2010-02-25
Say I wanted to send it to yahoo. How would I go about that?

---

### Post by gmargo on 2010-02-25
> **d3v1150m471c said:**
> It sits there and does nothing. I waited ten minutes...still nothing. Killed the firewall, same gig. Obviously this is user error but what I'm doing wrong is unknown to me. Any suggestions?

It just "sits there" because it's reading from standard input - it's waiting for you to type the message.  After you type your message you can terminate the message with either a single period or with CTRL-D.  Alternatively if your message is in a file, you can use redirection like "mail -s subject address < file".

---

### Post by d3v1150m471c on 2010-02-25
Thanks man, that got it.

---

### Post by dcstar on 2010-02-26
> **gmargo said:**
> It just "sits there" because it's reading from standard input - it's waiting for you to type the message.  After you type your message you can terminate the message with either a single period or with CTRL-D.  Alternatively if your message is in a file, you can use redirection like "mail -s subject address < file".

Two days of waiting that "man mail" would have solved in 60 seconds.....

---

