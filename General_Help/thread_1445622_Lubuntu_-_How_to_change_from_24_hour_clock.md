---
title: "Lubuntu - How to change from 24 hour clock?"
date: 2010-04-02
forum: General Help
---

### Post by Uncle Spellbinder on 2010-04-02
No clue how to change the 24 hour clock format in Lubuntu 10.04 Beta. Ideas anyone?

[img]http://content.imagesocket.com/images/2010_04_02_201017_1680x1050_scrot9c4.png[/img]

---

### Post by stone1343 on 2010-04-02
The %R specifies the time format from the locale. Here's one place you can go for info on alternate formats:

[http://php.net/manual/en/function.strftime.php](http://php.net/manual/en/function.strftime.php)

You might want %r Example: 09:34:17 PM for 21:34:17

---

### Post by stone1343 on 2010-04-02
I just noticed, there was a hint right in the dialog you posted the screencap of, in lxterminal,

man 3 strftime

explains the format codes too.

---

### Post by ad_267 on 2010-04-02
```
%I:%M %P
```

would give you 09:34 pm.

---

### Post by kerry_s on 2010-04-02
i got mine like gnome: 
```
%a %b %d, %l:%M%P
```

---

### Post by Uncle Spellbinder on 2010-04-03
Thanks for the responses, all!

;)

---

### Post by TheNerdAL on 2010-04-03
Please mark as [SOLVED] if solved. :)

---

