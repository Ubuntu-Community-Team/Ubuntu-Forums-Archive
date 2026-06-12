---
title: "running script files from anywhere"
date: 2011-11-30
forum: General Help
---

### Post by rng on 2011-11-30
How can I keep some bash script files in a subfolder of bin folder so that I can run them from anywhere? 

Thanks for your help.

---

### Post by gennatolls on 2011-11-30
You could put them in ~/.bin I believe (someone correct me if that's wrong) or you could just add them to your $PATH

---

### Post by rng on 2011-11-30
The path includes:  /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

1. Should I keep them in /bin  or /usr/bin  or /usr/local/bin  or  /usr/sbin etc ?

2. Can I keep them in a subfolder and add that folder to the path?  Also can I manage that I do not have to change path every time I start the computer?

Thanks for your help.

---

### Post by papibe on 2011-11-30
If you create a ~/bin directory, it will be added to your path at startup.

That is set on the .profile file. This is an extract:
```

...
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
...
```
Regards.

---

### Post by rng on 2011-12-01
This is exactly what I wanted. Thanks.

---

