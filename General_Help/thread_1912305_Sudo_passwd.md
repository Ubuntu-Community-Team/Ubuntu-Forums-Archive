---
title: "Sudo passwd"
date: 2012-01-20
forum: General Help
---

### Post by CoffeeRain on 2012-01-20
I am root on a computer, and one of the users on my computer changed their password and forgot it. :mad: Is there a way to either read their password or change it without knowing it? Keep in mind that I am root and can use sudo. Thanks! :)

---

### Post by nothingspecial on 2012-01-20
If you are root you simply type

```
passwd username
```

where username is the actual username of the user.

You should not be root in Ubuntu.

---

### Post by CoffeeRain on 2012-01-20
Thanks. What do you mean I shouldn't be root? Do you just mean that I could really screw stuff up? If so, I know that and just meant that I had the possibility of using root, not that I use the Terminal as root all the time.

---

### Post by nothingspecial on 2012-01-20
> **CoffeeRain said:**
> Thanks. What do you mean I shouldn't be root? Do you just mean that I could really screw stuff up? If so, I know that and just meant that I had the possibility of using root, not that I use the Terminal as root all the time.

Then you have an admin account and that is fine. In that case it would be 

```
sudo passwd username
```

---

### Post by CoffeeRain on 2012-01-20
Oh yeah. :oops: Thanks for correcting me. :)

---

