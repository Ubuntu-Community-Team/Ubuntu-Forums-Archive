---
title: "Why doesn't this bash line delete all /tmp/ files over 24 hours old?"
date: 2012-06-04
forum: General Help
---

### Post by tarahmarie on 2012-06-04
sudo find /tmp -mtime +1 -exec rm -f {} \;

And second, why can't I see the "New Thread" orange button in the "Development and Programming" subforum? Is it limited now?

---

### Post by Cheesemill on 2012-06-04
Why would you want to delete anything in /tmp ?

/tmp gets deleted every time you boot your machine.

---

### Post by tarahmarie on 2012-06-04
tmp is filling rapidly, and I don't reboot my machine but about once a week. I have a 10GB home partition, and tmp gets up to 3GB pretty quickly given my activity; I have started having issues with no space on /home. So, I want to run a cleaner script, and this is one of the lines. 

And I still don't know why I can't post this in Development and Programming; anyone know?

---

### Post by PaulW2U on 2012-06-04
> **tarahmarie said:**
> And I still don't know why I can't post this in Development and Programming; anyone know?

Because that forum is Read Only?

You should be able to post in most of the Development and Programming sub-forums though.

---

### Post by Cheesemill on 2012-06-04
> **tarahmarie said:**
> And I still don't know why I can't post this in Development and Programming; anyone know?
Development and Programming is a top-level category, you have to click on one of the sub-forums to choose which one to post into.

---

### Post by steeldriver on 2012-06-04
is there an error message? if there are A LOT of files, you may be overflowing the argument list - in which case try xargs

[http://ubuntuforums.org/showpost.php?p=11985435&postcount=4](http://ubuntuforums.org/showpost.php?p=11985435&postcount=4)

---

### Post by bab1 on 2012-06-04
> **tarahmarie said:**
> sudo find /tmp -mtime +1 -exec rm -f {} \;

And second, why can't I see the "New Thread" orange button in the "Development and Programming" subforum? Is it limited now?

I agree with the others, you should find the source of the problem.  i believe the reason why this is not working probably because the exec rm is not being executed with elevated permissions.  You could try this rather scary incantation  :-)```
sudo find /tmp -mtime +1 -exec [COLOR="Red"]sudo rm -f[/COLOR] {} \;
```

---

