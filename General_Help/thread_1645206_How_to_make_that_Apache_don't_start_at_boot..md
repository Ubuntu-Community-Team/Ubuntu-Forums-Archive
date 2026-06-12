---
title: "How to make that Apache don't start at boot."
date: 2010-12-14
forum: General Help
---

### Post by nagisa on 2010-12-14
Well I have apache2 installed, and I have apache2 in init.d directory.

I want to make possible, so apache won't run on boot, but only when I type
```
sudo service apache2 start
```.
I know I could make it not executable, but I won't be able to run apache on terminal too.
I also tought about moving apache shell file, but running it gives me errors, so it's not a solution as well.

---

### Post by nagisa on 2010-12-15
B(l)ump(t).

---

### Post by lukeiamyourfather on 2010-12-15
Remove the apache symbolic links from the different run levels, like /etc/rc1.d, /etc/rc2.d, etc. Be sure ***NOT*** to remove the apache script in /etc/init.d though. Then you can manually start and stop the service as you wish.

```
sudo service apache start
```
```
sudo service apache stop
```

---

### Post by nagisa on 2010-12-15
Thanks. Solved.

---

### Post by azzid on 2010-12-15
To get some help with the symbolic links, check out update-rc.d.
```
man update-rc.d
```

---

