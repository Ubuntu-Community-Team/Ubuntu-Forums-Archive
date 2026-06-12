---
title: "Make root password visible as asterisk"
date: 2010-12-30
forum: General Help
---

### Post by satish_j on 2010-12-30
Is it possible to make root password visible as asterisk(or any other character) on using sudo command??
Currently,it does not display anything on monitor,thus,making it difficult to count the number of keystrokes pressed...

---

### Post by karthick87 on 2010-12-30
AFAIK it is not possible..

---

### Post by tech-hero on 2010-12-30
linux is designed to to be like that even during command line days... it is for security purposes. :)

---

### Post by karthick87 on 2010-12-30
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by matt_symes on 2010-12-30
Hi

There is a way to do what you want.

Open a terminal and type

```
sudo visudo
```Navigate to the line 

```
Defaults        env_reset
```and change to

```
Defaults        env_reset,pwfeedback
```Save the file. Close the terminal then open a new terminal (so no sudo time) and enter

```
sudo apt-get update
```to check it's working. Be careful with this file though.

See

```
man sudoers
```and look for SUDOERS OPTIONS section

Kind regards

---

### Post by karthick87 on 2010-12-30
+1 on post #4

---

