---
title: "Using sed to change date string order"
date: 2010-10-31
forum: General Help
---

### Post by timgood on 2010-10-31
Hello code poets: I have a string (a date) ordered as dd/mm/yy and I am trying to use sed to reformat this as yy/mm/dd so I can import it into a quirky database driven CMS site.

I know that sed has pattern recognition and saving, so what I need to do is to recognise the first two characters (dd) as pattern1, the next four characters (/mm/) as pattern2, and the last two characters (yy) as pattern3 and then output as /3/2/1 but I am having spectacular and enigmatic failure at achieving this modest end.

I would really appreciate it if someone could give me a clue! Thanks in anticipation.

---

### Post by DaithiF on 2010-10-31
Hi, something like:
```
echo "31/10/10" | sed -r 's#([0-9]{2})/([0-9]{2})/([0-9]{2})#\3/\2/\1#'
```

---

### Post by timgood on 2010-10-31
> **DaithiF said:**
> Hi, something like:
```
echo "31/10/10" | sed -r 's#([0-9]{2})/([0-9]{2})/([0-9]{2})#\3/\2/\1#'
```

Takes off hat, bows respectfully and walks backwards while keeping eyes averted...

Many thanks. Much appreciated. Marked solved.

---

