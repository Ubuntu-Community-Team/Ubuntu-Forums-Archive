---
title: "unraring en masse in bash"
date: 2010-01-25
forum: General Help
---

### Post by The Switch Blade on 2010-01-25
Basically I have a folder of .rar files that I want to unrar. I have been using the following script:

for name in *.rar; do unrar x $name; done

The script works excellently, except for one thing: all of the files have the same password, and I have to manually type the password every single time. So what I try is

for name in *.rar; do unrar x $name -p<thepassword>; done 

But that doesn't work. Help please?

---

### Post by sisco311 on 2010-01-25
It works for me. Are you sure that the password is correct? Linux is case sensitive. ;) Does it contain any special characters or spaces? Do you get any error message?

EDIT:
You don't have to separate the -p option from the password by a space. 

```
for name in *.rar; do unrar x $name -ppassword; done
```
(Assuming that the password is *password*.)

---

### Post by J V on 2010-01-25
I think sisco means there *should* be a space there...

Also, if your pass includes spaces, quote it.

Also, shoulden't that x be -x?

```
for name in *.rar; do unrar -xp "password" $name; done
```

---

### Post by sisco311 on 2010-01-25
> **J V said:**
> I think sisco means there *should* be a space there...


I mean, the -p switch should **not** be separated from its argument by a space.

The correct syntax is:
```
unrar x file.rar -ppassword
```
where file.rar is the name of the archive & *password* is the password.

---

### Post by J V on 2010-01-27
Thats what it says in the manual, but I think its a spelling error, not good bash standard :/

---

### Post by sisco311 on 2010-01-27
> **J V said:**
> Thats what it says in the manual, but I think its a spelling error, not good bash standard :/

No, it's not. You can try it:
```
> file
rar a -phpassword file.rar file
rm file
unrar x -ppassword file.rar
```

a and x (add/extract) are commands passed to rar and unrar, just like apt-get *install* or apt-get *purge*. -ph and -p are switches like grep -A5 or fsck -C0.

It may look awkward, but the syntax is not uncommon.

---

