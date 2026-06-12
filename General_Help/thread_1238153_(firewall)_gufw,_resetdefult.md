---
title: "(firewall) gufw, reset/defult?"
date: 2009-08-12
forum: General Help
---

### Post by VipX1 on 2009-08-12
How can I default the firewall? I have lots of rules in my firewall now. Instead of deleting them one by one how can I just reset or default the firewall back to having zero rules?

---

### Post by VipX1 on 2009-08-12
Burp!!

---

### Post by wojox on 2009-08-12
Only thing I could think of would be to edit  /etc/ufw/before.rules,     /etc/ufw/after.rules, /var/lib/ufw/user.rules

---

### Post by Soul-Sing on 2009-08-12
```
sudo nano /etc/ufw/before.rules
```

edit: your first wojox! :)

---

