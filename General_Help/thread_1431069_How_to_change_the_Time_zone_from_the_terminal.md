---
title: "How to change the Time zone from the terminal"
date: 2010-03-16
forum: General Help
---

### Post by adeelm on 2010-03-16
Hi everyone,
                How to change the time zone from the terminal. I have looked in to 
System > Administration > Time and Date.

I know that it works but I wanted to know how to change it from terminal using commands.

Thanks
Adeel

---

### Post by wojox on 2010-03-16
```
dpkg-reconfigure tzdata
```

---

### Post by thebigob on 2010-03-16
This can also be done using the date command iirc.

```
 man date 
```

---

### Post by slakkie on 2010-03-16
Why reconfigure a package?

```

cat /etc/timezone
Europe/Amsterdam

```

Now, open that file as root with your favorite editor and change the value.

And if you only want a different timezone for your user:

export TZ="Europe/Amsterdam"

---

### Post by dcstar on 2010-03-17
> **adeelm said:**
> Hi everyone,
                How to change the time zone from the terminal. I have looked in to 
System > Administration > Time and Date.

I know that it works but I wanted to know how to change it from terminal using commands.

Thanks
Adeel

```
sudo tzselect
```

---

### Post by adeelm on 2010-03-18
> **slakkie said:**
> Why reconfigure a package?

```

cat /etc/timezone
Europe/Amsterdam

```Now, open that file as root with your favorite editor and change the value.

And if you only want a different timezone for your user:

export TZ="Europe/Amsterdam"

Thanks, it worked. I found another way. it was a bit long. here it is.


ln -sf /usr/share/zoneinfo/Europe/Amsterdam /etc/timezone

and after this command just set the date and time using the "date" command.

Thanks.
Adeel

---

### Post by dcstar on 2010-03-18
> **slakkie said:**
> Why reconfigure a package?
.........

Because that is the way the man page tells you to do it.

---

### Post by rnerwein on 2010-03-18
> **dcstar said:**
> Because that is the way the man page tells you to do it.

hi
real programmes don't use mice.
ciao

---

