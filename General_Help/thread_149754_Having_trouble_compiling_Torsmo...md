---
title: "Having trouble compiling Torsmo.."
date: 2006-03-24
forum: General Help
---

### Post by Piggah on 2006-03-24
Hi,

I just got ahold of the Torsmo source and went to compile it, and am unable to compile it due to what seems strange to me. 

When I run ./configure, it stops at this line, which seems quite odd to me: 

```
 checking for X... no
Sorry, X is very much needed

```

I don't really understand how I could not have X. So now I'm lost. 

Any help is appreciated. Thanks. :)

---

### Post by krusbjorn on 2006-03-24
Sorry, cant help you with the error, but there is a program in the repos that is very much the same, called conky. Could give it a shot.

---

### Post by taurus on 2006-03-24
Are you running X at all?  Do you log into Gnome or any other window manager?  Just so you know, you may want to install conky instead of torsmo since torsmo project has been idle for a while conky is an extension of torsmo...  Then again, if you want to build something from source, make sure you have build-essential first!
```

sudo apt-get install build-essential

```

---

### Post by Piggah on 2006-03-24
Yes, I'm using X and I have build-essential installed. 

I would use conky, but I couldn't get it working properly for the life of me.

---

