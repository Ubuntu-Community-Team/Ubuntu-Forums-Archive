---
title: "zenity alternatives for big texts?"
date: 2012-08-10
forum: General Help
---

### Post by codell on 2012-08-10
Are there any alternatives to zenity?

Ones that can show big amounts of text inside a single window?

Preferably in available in Ubuntu package sources.

---

### Post by Vaphell on 2012-08-10
define 'big amounts of text'

```
zenity --height=600 --width=800 --text-info < <( ps ux )
zenity --height=600 --width=800 --text-info <<< "some string"
zenity --height=600 --width=800 --text-info --filename=some_file.txt
echo "some string" | zenity --height=600 --width=800 --text-info

```

---

### Post by Habitual on 2012-08-13
Yad works too!

---

