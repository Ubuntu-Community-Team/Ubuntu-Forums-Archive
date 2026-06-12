---
title: "su: Authentication failure"
date: 2012-07-14
forum: General Help
---

### Post by darkdragonfly on 2012-07-14
Hi i'm new on this, I got Kubuntu 12.04 recently installed

I try to access as a super user but it says "su: Authentication failure" and i know the password is right because i used it before (i use it when the computer hibernates)

thanks

---

### Post by diesch on 2012-07-14
Ubuntu doesn't set a valid password  for root so you can't use *su*. Use *sudo* instead.

---

### Post by E5C4P3 on 2012-08-06
Try sudo su. It worked for me.

---

### Post by Cheesemill on 2012-08-06
> **E5C4P3 said:**
> Try sudo su. It worked for me.
You shouldn't use 'sudo su', instead the recommended method is to do:
```
sudo -i
```

---

