---
title: "bash"
date: 2012-04-07
forum: General Help
---

### Post by NyteRukh on 2012-04-07
im new to linux and going through some books i downloaded about the bash shell..
currently im only able to access bash shell if i hit ctrl+alt+1 and go to a console..none of the gui's terminal's allow me to access bash...is there a way fix that?

---

### Post by nothingspecial on 2012-04-07
They should do, if you open a gui terminal and type

```
echo $SHELL
```

you should get ```
/bin/bash
```

If you do you are using bash.

---

### Post by Habitual on 2012-04-07
> **NyteRukh said:**
> ...ctrl+alt+1 and go to a console..none of the gui's terminal's allow me to access bash...is there a way fix that?

```
ctrl+alt+t
```

should bring up a terminal emulator (gnome-shell, etc....).

---

### Post by NyteRukh on 2012-04-07
ok i did echo $shell and shows that /bin/csh is my shell on the terminal. i type chsh -s /bin/bash to change to bash...but it wont work..terminal doesnt change from csh

---

### Post by skabople on 2012-04-07
Try logging out and logging back in. That should work...

If it doesn't work then vim (or vi) into .bashrc (in your home directory) and add:
```
SHELL=/bin/bash
```
Then save the file and type this:
```
source .bashrc
```
Tell us how it goes \\:D/

---

### Post by raja.genupula on 2012-04-07
```
chsh -s /usr/local/bin/bash 
```
do this

---

### Post by NyteRukh on 2012-04-07
ok that worked thanks

---

### Post by skabople on 2012-04-07
Or you could do this:
```
usermod -s /bin/bash username
```

change *username to your username of course....

---

### Post by raja.genupula on 2012-04-07
> **NyteRukh said:**
> ok that worked thanks

ok please mark the thread as solved from thread tools.

---

