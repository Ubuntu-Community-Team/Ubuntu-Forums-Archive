---
title: "terminal into opt"
date: 2009-09-11
forum: General Help
---

### Post by Arminius on 2009-09-11
how do I get terminal into the opt directory, /home/(username) is as far back as it will go

---

### Post by akakingess on 2009-09-11
so typing  ```
cd..
```

doesn't take you back/up a level?  You could just keep entering that until you get to the top and then navigate from there.

---

### Post by Arminius on 2009-09-11
just says command not found

---

### Post by akakingess on 2009-09-11
can you try just?...

```
cd \opt
```

and tell us what that tells you..

---

### Post by Arminius on 2009-09-11
No such file or directory

---

### Post by falconindy on 2009-09-11
cd.. is not a valid linux command. \opt is is not a valid linux directory. However...
```
cd ..
cd /opt
```
**are** both valid.

---

### Post by akakingess on 2009-09-11
When you navigate within Nautilus, you can see the 'opt' directory, correct?  If accessing it is an issue than you could launch Nautilus as root by opening the terminal and entering
```
sudo Nautilus
```and then of course enter your root password and it should launch Nautilus with root privileges (I would be really careful and don't normally recommend stuff like this, but if you gotta get into that directory, you have to). Let me know what comes of this attempt.

Edit: just watch the capitalization on Nautilus (can't remember if it's lowercase or not).

---

### Post by akakingess on 2009-09-11
> **falconindy said:**
> cd.. is not a valid linux command. \opt is is not a valid linux directory. However...
```
cd ..
cd /opt
```**are** both valid.

See, that's what I get for trying to help in a hurry while at work and not in front of my own Ubuntu machine. Thanks for the corrections.

---

