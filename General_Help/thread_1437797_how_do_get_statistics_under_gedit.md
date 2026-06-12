---
title: "how do get statistics under gedit?"
date: 2010-03-24
forum: General Help
---

### Post by lidengdeng on 2010-03-24
Hi, i always use gedit to write and edit text file under ubuntu. However, i cant find the way to get some statistics, like how many times a word presents in the txt file?

Any suggestion?

thanks.

---

### Post by audiomick on 2010-03-24
Hi.
I don't think gedit can do that itself. You might be able to do what you want with the command "grep".

Do
```
man grep
```in a terminal to read the man page. 

This, from there, could be what you are looking for.
```
 General Output Control
       -c, --count
              Suppress  normal output; instead print a count of matching lines
              for each input file.  With the -v,  --invert-match  option  (see
              below), count non-matching lines.  (-c is specified by POSIX.)
```

I haven't used this myself, but this is, as far as I understand it, the method recommended by my big fat smart Linux book to do things like what you descrbed with .txt files.

---

### Post by KB1JWQ on 2010-03-24
Also look into the "wc" program.

If you want a full fledged text edtior, try Open Office.  It's more targeted towards what you want than gedit is.

---

### Post by cjhabs on 2010-03-24
> **lidengdeng said:**
> Hi, i always use gedit to write and edit text file under ubuntu. However, i cant find the way to get some statistics, like how many times a word presents in the txt file?

Any suggestion?

thanks.

Tools -> Document Statistics

---

