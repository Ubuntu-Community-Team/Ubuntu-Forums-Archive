---
title: "Need a script"
date: 2010-07-28
forum: General Help
---

### Post by kleinempfaenger on 2010-07-28
Hi,
I need to sort hundreds of files in Nautilus, which are named xxxx.png (for examle 0223.png). I want to separate odd and even filenames and move them to different subfolders. I think it must be very simple, but I am not experienced in bash-scripting.
Thanks for help.

---

### Post by uRock on 2010-07-28
cd to the directory containing the files, then run ```
cp *1.png,*3.png,*5.png,*7.png,*9.png /recieving_directory_path/
```
then run the same, but change the odd numbers to even numbers and run it. This may need some adjustments. ```
man cp
``` may be more helpful on setting up the syntax.

---

### Post by uRock on 2010-07-28
Let us know how it works and if you had to make any adjustments. Being that you are using copy instead of move you don't have to worry about loosing files.

---

### Post by uRock on 2010-07-28
I played with this command until I could make it work and here was the winning syntax.
```
cp *1.png *3.png *5.png *7.png *9.png /recieving_directory_path
```

---

### Post by kleinempfaenger on 2010-07-29
Thanks, uRock. It worked perfectly!

---

### Post by ghostdog74 on 2010-07-29
you can use brace expansion
```

cp *{1,3,5,7,9}.png /destination

```

---

### Post by uRock on 2010-07-29
> **ghostdog74 said:**
> you can use brace expansion
```

cp *{1,3,5,7,9}.png /destination

```
That does look a bit cleaner.

---

