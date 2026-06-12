---
title: "Remove 'user@name-of-computer' from terminal"
date: 2011-04-01
forum: General Help
---

### Post by Reiny Junior on 2011-04-01
Hi Guys !

How i remove 'user@name-of-computer', from initialization of terminal ?

---

### Post by nothingspecial on 2011-04-01
Edit your bashrc

```
nano .bashrc
```

Find the lines that start with PS1= and delete this bit 

```
\u@\h\
```

Then type ```
. ~/.bashrc
```
(notice the "." at the start of that.

If you want to change it back or something goes wrong there is a default bashrc in /etc/skell so

```
cp /etc/skel/.bashrc ~/
```

---

### Post by Reiny Junior on 2011-04-01
Hey Guy !

Thanks for your help, it's exactly what i wanted !!!

Thanks :D  !

---

### Post by nothingspecial on 2011-04-01
No problem :popcorn:

---

