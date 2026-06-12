---
title: "Why do I get message: &quot;sudo: unable to resolve host D07&quot;?"
date: 2011-06-02
forum: General Help
---

### Post by Rytron on 2011-06-02
Hi.

I am running Linux Mint 11 based on Natty.

Any time I run a command with [COLOR="Navy"]sudo[/COLOR] e.g. [COLOR="Indigo"]sudo bleachbit[/COLOR], I get this:
```
sudo: unable to resolve host D07
```

As far as I know it causes no problems but how can I fix it? Is the host the same as my computer name?

Thanks.

---

### Post by jamesisin on 2011-06-02
This thread should help you solve your problem:

[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

---

### Post by Rytron on 2011-06-02
> **jamesisin said:**
> This thread should help you solve your problem:

[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

Thank you jamesisin. However, my [COLOR="Indigo"]/etc/hosts[/COLOR] file is empty!

So would I just do 

```
gksudo gedit /etc/hosts
```

and add this to [COLOR="Indigo"]/etc/hosts[/COLOR]:

```
127.0.0.1 localhost
127.0.1.1 D07
```

---

### Post by jamesisin on 2011-06-02
I believe that should be sufficient.

---

### Post by Rytron on 2011-06-02
> **jamesisin said:**
> I believe that should be sufficient.

Yep, it seems fine now. ;)

Strangely this also solved another recent thread I made: [http://ubuntuforums.org/showthread.php?t=1772099](http://ubuntuforums.org/showthread.php?t=1772099)

---

### Post by jamesisin on 2011-06-02
Probably because it was not able to resolve local host (the 27 IP in your hosts file).  Be sure to link that thread back to this one (and mark it solved) so others can benefit.

---

### Post by Rytron on 2011-06-03
> **jamesisin said:**
> Probably because it was not able to resolve local host (the 27 IP in your hosts file).  Be sure to link that thread back to this one (and mark it solved) so others can benefit.

Done!

---

