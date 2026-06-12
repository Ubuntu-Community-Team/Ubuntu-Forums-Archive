---
title: "How do i get a normal root account?"
date: 2006-03-31
forum: General Help
---

### Post by John64 on 2006-03-31
What I would like to do is have a normal root account like all other linuxes i have used have.  I want it to be a distinct user that can (but wont) be used to login, like when the computer boots.  This is so i can have multiple people able to be root.  I dont like sudo, never have.  its my ONLY quip with ubuntu

---

### Post by taurus on 2006-03-31
Just create a password for root and log in as root then...
```

sudo passwd root

```
Then,
```

su -

```

---

### Post by testube_babies on 2006-03-31
if you want to log in as root, set a root password (sudo passwd root) and then go to System -> Administration -> Login Screen Setup.

Security Tab -> Options -> Allow root to login with GDM

---

### Post by John64 on 2006-03-31
Thanks!!!

I tried something like that (sudo -H -s then passwd) that didnt work.

Awesome!  I dont have GDM, or any X for that matter!

---

### Post by Madpilot on 2006-03-31
[QUOTE=John64]This is so i can have multiple people able to be root.[/QUOTE]

Umm... just for future reference, multiple accounts can have sudo privs, too.

Just because you have multiple accounts doesn't mean you need a root user.

---

### Post by John64 on 2006-03-31
I dont personally like the sudo system on systems which i use in purely console mode.  I end up using sudo -H -s all the time, so i may as well have a dedicated root account.

Another question - is it possible to have another account that has full root permissions that isnt called root?

---

### Post by mcmillan on 2006-03-31
> 
Another question - is it possible to have another account that has full root permissions that isnt called root?

I don't think you can give someone all the root permissions, though you can give someone full sudoer permission.  Just add this line to the sudoer file
[name]        ALL=(ALL)       ALL

---

