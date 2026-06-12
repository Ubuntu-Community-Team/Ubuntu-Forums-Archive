---
title: "Combine sed and date in bash?"
date: 2011-12-19
forum: General Help
---

### Post by peter11a on 2011-12-19
How can I combine the command sed and date in a bash file?

I have tried this with no success:

sed '/"date --date='2 days ago' '+%m/%d/%y'"/d' temperature.bak> new.file

(The goal for me is to get rid off all lines in the file "temperature.bak" that is to days old.)

Ex. this lines.
12/17/11 22:42:02 Sensor 0 C: 41.19
12/17/11 22:42:03 Sensor 1 C: 1.31
12/17/11 22:42:04 Sensor 2 C: 45.25

Best Regards
Peter

---

### Post by erind on 2011-12-19
I modified your code a bit:

```
sed [COLOR=Blue]"[/COLOR]/"$(date --date='2 days ago' '+%m[COLOR=Blue]\[/COLOR]/%d[COLOR=Blue]\[/COLOR]/%y')"/d[COLOR=Blue]"[/COLOR] temperature.bak > new_file

```or

```
grep -v "$(date --date='2 days ago' '+%m/%d/%y')" temperature.bak > new_file
```

---

### Post by Habitual on 2011-12-19
> **erind said:**
> ...```
grep -v "$(date --date='2 days ago' '+%m/%d/%y')" temperature.bak > new_file
```

Funny, I came up with the the exact same code!

Eerie.

---

### Post by peter11a on 2011-12-20
Thank you very much guys.
It works perfect with these lines.

Best regards
Peter

---

