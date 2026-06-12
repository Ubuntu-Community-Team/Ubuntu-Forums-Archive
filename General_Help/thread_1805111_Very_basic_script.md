---
title: "Very basic script"
date: 2011-07-15
forum: General Help
---

### Post by JigglyWiggly_ on 2011-07-15
I want to do this
sudo kill pidof apache2 in one line, this won't work though it says garbage process ID apache2

How can I get this working in one line? (for reference I realize you can just do pidof apache 2
then kill the id), but I want to do this in one line.

---

### Post by TheMatej on 2011-07-15
what about command [I]killall
[/I]```
# killall apache2
```
or
```
# kill -9 `pidof apache2`
```

---

### Post by nickna on 2011-07-15
sudo kill `pidof apache2`


(they are backticks)

---

### Post by papibe on 2011-07-15
You can use the 'killall' command like this:
```
$ sudo killall apache2
```
Regards.

---

### Post by bodhi.zazen on 2011-07-15
> **JigglyWiggly_ said:**
> I want to do this
sudo kill pidof apache2 in one line, this won't work though it says garbage process ID apache2

How can I get this working in one line? (for reference I realize you can just do pidof apache 2
then kill the id), but I want to do this in one line.

What is wrong with

```
service apache stop
```

---

### Post by nothingspecial on 2011-07-15
> **bodhi.zazen said:**
> What is wrong with

```
service apache stop
```

Nothing except sudo :D

---

