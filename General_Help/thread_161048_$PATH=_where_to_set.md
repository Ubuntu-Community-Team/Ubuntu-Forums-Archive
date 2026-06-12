---
title: "$PATH= where to set?"
date: 2006-04-16
forum: General Help
---

### Post by rensu on 2006-04-16
I have a question... Where i can set the $PATH= for everyone, not only for one user.

---

### Post by mlind on 2006-04-16
see /etc/environment

---

### Post by rensu on 2006-04-16
Should i just put into the file this:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/usr/local/mysql/bin/"

/usr/local/mysql/bin/ #added#

Or how I should put it. Because it didn't work :(

---

### Post by souki on 2006-04-16
you have to login again for this to take effect
personnaly, I prefer put a symlink inside /usr/bin

---

### Post by rensu on 2006-04-16
What do you mean?:S I didn't understand it... could you give some examples?

---

### Post by souki on 2006-04-16
[QUOTE=rensu]What do you mean?:S I didn't understand it... could you give some examples?[/QUOTE]
for example, you want 'msql' in your path ...
```
sudo ln -s /usr/local/mysql/bin/msql /usr/bin/
```
et voilà, you don't need to login again

---

### Post by mlind on 2006-04-16
for debian, you should check out *update-alternatives* script,
that's used to manage systemwide symlinks on /usr/bin.

```

sudo update-alternatives --help

```


if you need certain path to every user, put it on /etc/environment
if you need it for just yourself, put it on ~/.bashrc

---

