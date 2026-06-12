---
title: "machine's domain name"
date: 2009-10-19
forum: General Help
---

### Post by krishna1650 on 2009-10-19
hi all, i want to know my machine's domain name? by using "hostname" command i can get my machine's name, but i don't know how to get domain name. so need help.

thank you.

---

### Post by Bachstelze on 2009-10-19
```
hostname -f
```

---

### Post by krishna1650 on 2009-10-19
> **Bachstelze said:**
> ```
hostname -f
```

thanks for the quick reply. but sadly i am getting only the machine name, "hostname -f" gives same result, which is given by "hostname"

---

### Post by Bachstelze on 2009-10-19
> **krishna1650 said:**
> thanks for the quick reply. but sadly i am getting only the machine name, "hostname -f" gives same result, which is given by "hostname"

Then you don't have a domain part in your hostname.

---

### Post by krishna1650 on 2009-10-19
> **Bachstelze said:**
> Then you don't have a domain part in your hostname.

how can i set it? please tell.

---

### Post by Bachstelze on 2009-10-19
> **krishna1650 said:**
> how can i set it? please tell.

Edit /etc/hostname and reboot.

---

