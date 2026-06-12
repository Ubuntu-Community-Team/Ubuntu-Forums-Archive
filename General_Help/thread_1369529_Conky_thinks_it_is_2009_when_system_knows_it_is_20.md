---
title: "Conky thinks it is 2009 when system knows it is 2010"
date: 2010-01-01
forum: General Help
---

### Post by iTrascurato on 2010-01-01
Here is an interesting one for you gurus to try out..

Conky is convinced it is January 1 2009.  Here is the same line of code it has always been in ~/.conkyrc.

```
${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}

```

The system knows it is 2010, including the date command.

```
brendan@slavechild:~$ date
Fri Jan  1 05:22:48 EST 2010
```

Here it is just after restarting conky:

[IMG]http://ourlager.com/forums/conky0101.png[/IMG]



Thoughts?

---

### Post by mobilediesel on 2010-01-01
> **iTrascurato said:**
> Here is an interesting one for you gurus to try out..

Conky is convinced it is January 1st 2009.  Here is the same line of code it has always been in ~/.conkyrc.

```
${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}

```

The system knows it is 2010, including the date command.

```
brendan@slavechild:~$ date
Fri Jan 1 05:22:48 EST 2010
```


Thoughts?

From the man pages for **date**:
>  %G     year of ISO week number (see %V); normally useful only with %V
This is still week 53 for 2009. You want to replace **%G** with **%Y** which will display current year.

---

### Post by HandyAndy on 2010-01-01
Thank you, mobilediesel. I had the same issue and your fix corrected it.

Happy New (correct) Year!

---

### Post by mobilediesel on 2010-01-01
I've been messing with the **date** command a lot recently in editing a few calendar scripts for conky. Go **[[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?p=8592002#post8592002")** top check them out. Some are simpler than others, 2 of them are quite minimal.

---

### Post by iTrascurato on 2010-01-01
Awesome!  Done.  Thank you so much.

It is now officially 2010.

---

