---
title: "ICE authority...???"
date: 2010-01-15
forum: General Help
---

### Post by robertcoulson on 2010-01-15
Hi
Downloaded Ubuntu 10.04 ISO and when I ran it, it locked up....Now when I dual boot to Ubuntu 9.10 trough Grau I get the following error**"Could not update ICEauthority file/home/robert/.ICEauthority"**
Now mind you once I hit OK Ubuntu logs in as normal...Does anyone know what happened...??
Bob

---

### Post by sisco311 on 2010-01-16
Check your home directory's permissions:
```

ls -al /home
ls -al /home/robert

```

For details see: [thread=976610]Solving .dmrc and $HOME Permission Errors[/thread]

---

### Post by robertcoulson on 2010-01-16
Well...I did what you said and got this reply...Don't know what I am looking at, BUT it looks goog.
Bob

---

### Post by robertcoulson on 2010-01-16
Adding terminal results
Bob

---

### Post by sisco311 on 2010-01-16
> **robertcoulson said:**
> Adding terminal results
Bob

The .ICEauthority file in your home directory is owned by root.

run:
```
sudo chown robert\: ~/.ICEauthority
```
to correct the problem.


In the future use gksu(or sudo -i) to run GUI apps as root, for details see [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo) ;)

---

### Post by robertcoulson on 2010-01-16
Hi [sisco311]("http://ubuntuforums.org/member.php?u=244665")
That seem to do the trick...thanks so much....Almost 100 % back to normal.
Bob

---

