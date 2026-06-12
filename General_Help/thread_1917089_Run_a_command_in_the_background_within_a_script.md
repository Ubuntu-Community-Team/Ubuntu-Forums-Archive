---
title: "Run a command in the background within a script"
date: 2012-01-29
forum: General Help
---

### Post by zedixal on 2012-01-29
Hi,

I need to run this command:

```
sudo socat -T15 udp4-recvfrom:53,reuseaddr,fork tcp:localhost:5353 &
```If I type this in shell, the command is executed in the background, as expected. If I put this in a script, namely thiswontwork.sh, and I type:

```
sudo thiswontwork.sh
```socat is executed, but not in the background, so the script stops and waits forever.

Is there a way to run this command in a script?

---

### Post by zedixal on 2012-01-29
OK, I solved it; in a script the command runs as expected if put in parentheses:

```
( sudo socat -T15 udp4-recvfrom:53,reuseaddr,fork tcp:localhost:5353 ) &
```

I thought that parentheses were equivalent to "&", but, clearly, I was wrong

---

