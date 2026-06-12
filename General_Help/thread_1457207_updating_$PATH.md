---
title: "updating $PATH"
date: 2010-04-18
forum: General Help
---

### Post by engine on 2010-04-18
So ... I've installed some (non-package) software in its own directory under /usr/local/bin, and now I want to add that directory to my $PATH

It's so long since I last had to do this I've forgotten anything I once knew about export <g> If I look at my .profile, I feel none the wiser: the only thing I recognise as setting $PATH is wrapped in an "if" ...

Thanks in advance for any tips!

---

### Post by wojox on 2010-04-18
Open your terminal and:

```
echo $PATH
```

/usr/local/bin should already be there.

---

### Post by engine on 2010-04-19
> I've installed some (non-package) software in its own directory under /usr/local/bin, and now I want to add that directory to my $PATH

Yes, /usr/local/bin is already included in $PATH: but the new directory /usr/local/bin/mup isn't, which means that simply typing "mup {fname}" does not find/run the app

---

### Post by klemes on 2010-04-19
To make the changes of the path persistent and also system-wide(ie available for all users)
you must edit as root the file /etc/environment and add the new path to the existing ones in the PATH variable.

```
sudo nano /etc/environment
```

---

### Post by lordskid on 2010-04-19
you can just add PATH="/usr/bin/mup:$PATH" to the last line of .profile or .bashrc though I usually add PATH lines to .profile

---

