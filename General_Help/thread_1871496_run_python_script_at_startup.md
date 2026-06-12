---
title: "run python script at startup"
date: 2011-10-29
forum: General Help
---

### Post by Vinger on 2011-10-29
Hello,

I want to run a python script as sudo on startup.
How can i do this?

Now i always have to login, then open the therminal, run the script and give my password...

Is there a automated way?

tx!

---

### Post by raja.genupula on 2011-10-29
add your line to .basrc file 
as
```
python scrpt.py
```All the best.

---

### Post by Vinger on 2011-10-29
tx, but it doesn't work.

The problem is that the script needs sudo rights.
When i add sudo, it looks for the file sudo...

any solution?

grz

---

### Post by raja.genupula on 2011-10-29
[http://ubuntuforums.org/archive/index.php/t-19236.html](http://ubuntuforums.org/archive/index.php/t-19236.html)

---

### Post by Vinger on 2011-10-29
Hello,

I added 
koenh ALL = (ALL) NOPASSWORD path/to/script/script.py 
to the file /etc/sudoers.

i think i did something wrong:
I cannot run any sudo script anymore!
> koenh@koenh-Kubuntu-11:/etc$ sudo kate
>>> /etc/sudoers: syntax error near line 31 <<<
sudo: parse error in /etc/sudoers near line 31
sudo: no valid sudoers sources found, quitting


How can i restor my sudoers file?
tx!

EDIT:
I restored my sudoers file via the live cd, but what is then the solution to have the permision to run the script at startup?

tx.

---

