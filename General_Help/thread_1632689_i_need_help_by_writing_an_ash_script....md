---
title: "i need help by writing an ash script..."
date: 2010-11-28
forum: General Help
---

### Post by m.alkhalel on 2010-11-28
hallo all ,
im trying to write a simple script and sometimes it asks me yes/no? and i have to type yes , so my question is how do i make it run the commands without needing my confirm ? or how to make automaticly type "yes" ?
thx in advance

---

### Post by asmoore82 on 2010-11-28
We're going to need more info. It's likely not the script that is asking yes/no, but instead the programs you are calling from the script. Most command line programs will accept some form of a `--force` or `--yes` option to skip confirmations.

---

### Post by m.alkhalel on 2010-11-28
heres the commands that need confirmng sometimes :
apt.get update
apt-get upgrade

and thx for ur reply

---

### Post by m.alkhalel on 2010-11-28
thank it works now , all i had to do is to use "-y"

---

### Post by conradin on 2010-11-28
Yo could write an auto-root login portion to your script, then commands needing root permission would run without input. (I think)

---

