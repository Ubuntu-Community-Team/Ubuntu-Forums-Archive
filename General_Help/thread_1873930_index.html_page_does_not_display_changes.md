---
title: "index.html page does not display changes"
date: 2011-11-02
forum: General Help
---

### Post by shafi on 2011-11-02
Hi,
I have installed apache web server on an ubuntu server, and I often copy the files to some existing html folders on the server via the scp command, but sometimes when I update the index page of a html project then the updates could not be seen when I browse the page via the browser; even if I delete the index page I still could browse the deleted index page, seems the old pages are still exist in the cache.
I wonder if some of you guys have already experienced this?

Thanks.

---

### Post by Drenriza on 2011-11-02
Cant this be solved with a 
```
sudo /etc/init.d/apache2 restart
```
?

---

### Post by shafi on 2011-11-02
> **Drenriza said:**
> Cant this be solved with a 
```
sudo /etc/init.d/apache2 restart
```
?

I have already tried this, not working!

---

### Post by Azdour on 2011-11-02
Hi,

You've probably already done this, but I find that browsers cache the pages. When I do updates I always use Ctrl + F5. This makes sure it serves me the latest page. I wonder if this is the issue?

---

### Post by shafi on 2011-11-13
> **Azdour said:**
> Hi,

You've probably already done this, but I find that browsers cache the pages. When I do updates I always use Ctrl + F5. This makes sure it serves me the latest page. I wonder if this is the issue?

Thanks,
It seems to be working!

---

### Post by Azdour on 2011-11-14
Hi,

It good that it is working now. Any chance you can mark this thread as solved?

---

