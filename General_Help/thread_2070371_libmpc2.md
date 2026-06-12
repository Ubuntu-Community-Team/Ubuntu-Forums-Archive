---
title: "libmpc2"
date: 2012-10-12
forum: General Help
---

### Post by Kreacher on 2012-10-12
I have had problem with updates in 10.04 Lucid for a while. This is on a laptop (Acre Aspire 3613). The libmpc2 file always errors with error number 2 on any updates. I tried to reinstall and the remove through the terminal. Then I tried using the -f in apt-get to reinstall and that seemed to work. 

Questions: 
What is libmpc2 for?
What might I have installed that required it? 
May I safely remove it now?

I understand that it is a library file, but how did I get it? I hope the reinstall cures the update errors.

Thanks for your help in advance.

---

### Post by Rexilion on 2012-10-13
> [http://packages.ubuntu.com/libmpc2](http://packages.ubuntu.com/libmpc2)

'multiple precision complex floating-point library'

Seems important, maybe it's being used by GCC and some number intensive programs...

***_Make a backup of *all* your data. This could bork your system._***

Anyway's, try this:

```
apt-get download libmpc2
sudo dpkg --purge --force-all libmpc2
sudo dpkg -i libmpc2*.deb
```

---

