---
title: "Showing files starting with a capital"
date: 2010-12-27
forum: General Help
---

### Post by nir2000 on 2010-12-27
Hi everybody!
I want to show only the files starting with a capital letter in a directory.
I have tried this:
ls [A-Z]*
and it shows me almost all the files in the directory.
I read somewhere that i should write it as follows:
LC_ALL=C ls [A-Z]*
but it does not work also
I mildly understand that it somehow might be connected with locals(mine is en_US).
Please, if someone knows how to make the above command work please let me know.
Thank you in advance.
Nir

---

### Post by karthick87 on 2010-12-27
```
ls | grep -e '^[A-Z]'
```

---

### Post by noah++ on 2010-12-27
> **karthick87 said:**
> ```
ls | grep -e '^[A-Z]'
```
That's what I thought would work. But, as if trying to outsmart me, my terminal lists all files in the directory and merely **H**ighlights the characters that would make a line a match. It still prints non-matching lines. Why is that happening?

---

### Post by karthick87 on 2010-12-27
It lists files that has all uppercase letters in their names.
```
ls | grep  '^[A-Z0-9]*$'
```

---

### Post by sisco311 on 2010-12-27
See [http://www.mail-archive.com/bug-bash@gnu.org/msg02653.html](http://www.mail-archive.com/bug-bash@gnu.org/msg02653.html)

Setting the value of LC_COLLATE to C should do the trick:
```

LC_COLLATE=C
ls -1 [A-Z]*

```

---

### Post by nir2000 on 2010-12-29
Sisco311 thank you very much for your replay, I will check it out as soon as I get home.
as far as I understand, this may solve my problem.
I will mark the tread SOLVED as I get home.
Thank you evertbody
Nir

---

### Post by nir2000 on 2010-12-29
BTW Sisco is the change is permanent?
I mean, will it always work now?
Thank you in advance 
Nir

---

### Post by sisco311 on 2010-12-29
No, to make it permanent you have to add:
```
LC_COLLATE=C
```
to the ~/.bashrc (only for your user) or /etc/bash.bashrc (for all users) file.

---

