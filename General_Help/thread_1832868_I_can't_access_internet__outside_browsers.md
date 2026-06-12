---
title: "I can't access internet  outside browsers"
date: 2011-08-25
forum: General Help
---

### Post by linuxiano on 2011-08-25
Hello

i can browse internet through firefox and chrome,but i can't access internet in USC,synaptic package manager and update ....,is there something wrong with Ubuntu server?what is the problem?

i'm using 10.04

---

### Post by haqking on 2011-08-25
> **linuxiano said:**
> Hello

i can browse internet through firefox and chrome,but i can't access internet in USC,synaptic package manager and update ....,is there something wrong with Ubuntu server?what is the problem?

i'm using 10.04


That depends on the error you are getting, be more specific.

When you say no Internet, you mean an error about connectivity to a source is the issue ?

I supsect an issue with your sources list however we need to know the error you are having.

Show a screen capture when possible

---

### Post by jim_deadlock on 2011-08-25
You are probably using a repository that's not responding, if you hit the Settings button in Update manager, go to the  Ubuntu Software tab and you'll see a Download From dropdown menu. Select Other -> Select best server and it will test all the repos to find the fastest one for you.

---

### Post by linuxiano on 2011-08-25
thanks for answers

*Ubuntu software center keeps loading but nothing appears
*it's the same error for updates manager and synaptic package manager:

[IMG]http://img849.imageshack.us/img849/390/13389336.png[/IMG]

---

### Post by e79 on 2011-08-25
Should be easily fixable

```
sudo rm /var/lib/apt/lists/* -vf
```

```
sudo apt-get update
```

---

### Post by linuxiano on 2011-08-25
thanks that was helpful and i marked it [solved]

---

### Post by e79 on 2011-08-26
I'm glad we could help you resolve this issue :P

---

