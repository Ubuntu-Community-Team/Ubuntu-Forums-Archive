---
title: "a problem with assigning the output from find"
date: 2012-04-21
forum: General Help
---

### Post by Thorsen V on 2012-04-21
If I run a command like this in bash
```

find somepath -iname some-pattern

```it formats the output with one matched  file per line.

Yet when I assign the result to a variable ...
```

list=`find somepath -iname some-pattern`

```... then "echo $list", it seems like it has been created without the new-lines (it looks like they get replaced by spaces)

I've tried a few things to get the new-lines back, for example ...

```

list=`find somepath -iname some-pattern -exec printf "%s\n" {} \; `


```...but I've not been able to get anything but the space substitution.

(I'm trying to build a zenity dialogue box showing the list of matches  but because of this problem it displays only the first match)

I'm stuck so help would be appreciated.

---

### Post by Habitual on 2012-04-21
```
touch {1,2,3}.ogg
list=$(find `pwd` -iname "*.ogg")
echo "$list"| zenity --text-info
```HTH.

---

### Post by Thorsen V on 2012-04-21
yes that was very helpful. Thank you

Initially it still didn't seem to work for my script  but then it did when I noticed you put double quotes round "$list".

Why that should make a difference perhaps makes sense to you but it seems non-intuitive to me :)

Many thanks again.

** Marked as solved**

---

