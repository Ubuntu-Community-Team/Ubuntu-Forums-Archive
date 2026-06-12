---
title: "Move up directory with .."
date: 2012-09-29
forum: General Help
---

### Post by RDWD on 2012-09-29
Hello. I'm new to Ubuntu.

In Ubuntu you have to type "cd .." to move up a directory whereas on many other distributions you can just type ".."

Is there a way to get ".." to work on Ubuntu? It's a habit I don't want to kick.

Thanks.

---

### Post by vasa1 on 2012-09-29
What about an alias?
```
alias ..='cd ..'
```in your ~/.bash_aliases should do it.

---

### Post by Lars Noodén on 2012-09-29
That would be set in .bashrc to make it permanent.

```
alias ..='cd ..'

```

---

### Post by vasa1 on 2012-09-29
> **Lars Noodén said:**
> That would be set in .bashrc to make it permanent.

```
alias ..='cd ..'

```
What is meant by "permanent" in this context?

---

### Post by Lars Noodén on 2012-09-29
I think your post was edited between the time I saw it and got my post done or else I missed part of it.  

.bash_aliases works fine, I just notice that Ubuntu seems to have set its aliases in .bashrc instead.  Either way, it is permanent in that it last more than just the one shell session.

---

### Post by RDWD on 2012-09-29
Wonderful. Thanks both.

---

### Post by vasa1 on 2012-09-29
> **Lars Noodén said:**
> I think your post was edited between the time I saw it and got my post done or else I missed part of it.  

.bash_aliases works fine, I just notice that Ubuntu seems to have set its aliases in .bashrc instead.  Either way, it is permanent in that it last more than just the one shell session.

Yes, I did edit it! If the edit is done very soon it doesn't show.

BTW, I was trying to look up the difference myself and came across **which** which will tell us whether the alias we think up is already in use.

---

