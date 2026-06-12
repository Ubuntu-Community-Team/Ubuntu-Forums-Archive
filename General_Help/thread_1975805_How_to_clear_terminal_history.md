---
title: "How to clear terminal history?"
date: 2012-05-07
forum: General Help
---

### Post by codingman on 2012-05-07
Is it possible to clear the terminal history? 

Any help is appreciated,
Codingman

---

### Post by wilee-nilee on 2012-05-07
I use bleachbit to clear that and much more, be careful it can remove passwords from your browser if you tick it to do so.

---

### Post by scouser73 on 2012-05-07
> **wilee-nilee said:**
> I use bleachbit to clear that and much more, be careful it can remove passwords from your browser if you tick it to do so.

+1 for this.

---

### Post by mc4man on 2012-05-07
Simply delete ~/.bash_history either manually in nautilus or from terminal 

```
rm ~/.bash_history
```
&
```
history -c
```

---

### Post by CharlesA on 2012-05-07
history -c works fine by itself. You don't have to delete .bash_history

---

### Post by mc4man on 2012-05-07
> **CharlesA said:**
> history -c works fine by itself. You don't have to delete .bash_history

history -c only removes from  terminal it's run from, figured the Op wanted it emptied altogether

Edit: if inappropriate  will remove the command & just point to browse down in home folder > delete .bash_history

---

### Post by CharlesA on 2012-05-08
> **mc4man said:**
> history -c only removes from  terminal it's run from, figured the Op wanted it emptied altogether

Edit: if inappropriate  will remove the command & just point to browse down in home folder > delete .bash_history
Well that's something new.

Thanks. :)

---

### Post by Primefalcon on 2012-05-08
> **mc4man said:**
> Simply delete ~/.bash_history either manually in nautilus or from terminal 

```
rm -rf ~/.bash_history
```
&
```
history -c
```
Dont do a recurcive delete unless you are deleting folders... can be dangerous if the path is mistyped... especially if you use the f switch which I am not sure why you would use that here.......

rm ~/.bash_history is quite sufficient.... either that or open nautilus show hidden files and delete .bash_history file in the home folder since that is where terminal history is stored

---

