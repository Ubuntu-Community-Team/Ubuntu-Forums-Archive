---
title: "Jaunty wont startup"
date: 2009-07-11
forum: General Help
---

### Post by c0mput3r_n3rD on 2009-07-11
When I start my computer, at the login it says "Authentication Error" and wont let me log in.  Any ideas?

Thanks

---

### Post by Najand on 2009-07-11
Does it apear after bios? Does your computer perform boot or it appears before that?

---

### Post by c0mput3r_n3rD on 2009-07-11
It appears after the BIOS at login menu of Ubuntu.

---

### Post by c0mput3r_n3rD on 2009-07-12
I got it.  
For future refrence if any one else gets a "Authentication Error" at startup you have to boot into recovery mode, drop to root shell, enter the command:
```

vi /etc/pam.d/gdm

```And comment out the line:
@include common-pamkering
to make it:
```

#@include common-pamkering

```

---

