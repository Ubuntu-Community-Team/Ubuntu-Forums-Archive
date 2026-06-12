---
title: "How to capture output from synaptic terminal"
date: 2010-12-09
forum: General Help
---

### Post by adit on 2010-12-09
In synaptic package manager when I expand "Details" tab (at the time when some software is installed or removed), I can see a terminal.
I want to capture the output of terminal into a file.  I tried to highlight and right click.  But there is no context menu(copy, cut)

---

### Post by sikander3786 on 2010-12-09
If you want to copy/paste text, better use apt-get via Terminal under Applications > Accessories menu.

```
sudo apt-get install name-of-package
```

e.g,

```
sudo apt-get install vlc
```

Can't figure out how to copy text from Synaptic's output.

---

### Post by lmarmisa on 2010-12-09
Try this command

```

sudo apt-get install packagename | tee output.txt

```

---

### Post by adit on 2010-12-10
```
sudo apt-get install packagename | tee output
```
Thanks.  That worked.
I have one more problem.  Yesterday when I installed sun-java6-jdk, synaptic package manager output some messages in its terminal.  I want to read that messages.  Is it saved in any log file?

---

### Post by nothingspecial on 2010-12-10
/var/log/apt

---

