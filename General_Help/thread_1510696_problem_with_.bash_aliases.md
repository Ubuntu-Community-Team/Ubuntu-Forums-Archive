---
title: "problem with .bash_aliases"
date: 2010-06-15
forum: General Help
---

### Post by Hathadar on 2010-06-15
I setup a series of commands to show failed login attempts on my ssh server.
```
 grep  fail /var/log/auth.log | awk '{ print $14 }' |sort -n | uniq -c | sort -rn | head
```
I wanted to put this in my .bash_aliases file.  I am running into a problem where the apostrophes for the awk command interfear with the apostrophes to surround my alias.
```
alias showhackers='grep fail /var/log/auth.log | awk '{ print $14 }' |sort -n | uniq -c | sort -rn | head'

```
How can I use escape characters to overcome this problem or otherwise fix it?

---

### Post by john newbuntu on 2010-06-15
alias showhackers="grep  fail /var/log/auth.log | awk '{ print \$14 }' |sort -n | uniq -c | sort -rn | head"

---

### Post by Hathadar on 2010-06-16
Thanks!

---

