---
title: "Trying to install emacs..."
date: 2010-08-16
forum: General Help
---

### Post by xalelexx on 2010-08-16
[FONT=Courier New][SIZE=1]mkdir: cannot create directory `/usr/local/share/emacs': Permission denied
mkdir: cannot create directory `/usr/local/share/emacs': Permission denied
mkdir: cannot create directory `/usr/local/share/info': Permission denied
mkdir: cannot create directory `/usr/local/share/man/man1': Permission denied
mkdir: cannot create directory `/usr/local/share/emacs': Permission denied
mkdir: cannot create directory `/usr/local/libexec': Permission denied
mkdir: cannot create directory `/usr/local/share/emacs': Permission denied
mkdir: cannot create directory `/usr/local/share/emacs': Permission denied
mkdir: cannot create directory `/usr/local/share/emacs': Permission denied
mkdir: cannot create directory `/usr/local/share/emacs': Permission denied
mkdir: cannot create directory `/usr/local/share/icons': Permission denied
mkdir: cannot create directory `/usr/local/share/icons': Permission denied
mkdir: cannot create directory `/usr/local/share/icons': Permission denied
mkdir: cannot create directory `/usr/local/share/icons': Permission denied
mkdir: cannot create directory `/usr/local/share/icons': Permission denied
mkdir: cannot create directory `/usr/local/share/icons': Permission denied
mkdir: cannot create directory `/usr/local/share/icons': Permission denied
make: *** [mkdir] Error 1

[SIZE=3]Trying to install emacs so I can do LaTeX work for my thesis, but this is showing up. Any thoughts?[/SIZE]
[/SIZE][/FONT]

---

### Post by spibou on 2010-08-16
Which command did you use in order to install ? Were you root or did you use sudo ?

---

### Post by xalelexx on 2010-08-16
I followed the emacs installation guide...
```

        ./configure

         make

         make install

```

---

### Post by ubudog on 2010-08-16
Instead of doing that, you can just install it with apt:
```
sudo apt-get install emacs23
```

Though for a beginner I recommend using Synaptic for installing it.

---

### Post by spibou on 2010-08-16
I don't know why you didn't use the normal installation procedures instead of compiling the
programme but in any case the last step should have been ```
sudo make install
```

---

