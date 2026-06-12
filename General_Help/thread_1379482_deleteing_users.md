---
title: "deleteing users"
date: 2010-01-12
forum: General Help
---

### Post by vader95 on 2010-01-12
Hi,

I have ubuntu installed on my computer. I started some HP learning center training courses and one was linux 101. They use debian for that, but it said ubuntu would be fine.


I then started the course. It had me create a user account for a fake person. Now i want to delete that account. I am on my main account because i cannot log into this other account. When i go to delete the account ubuntu says it is deleted, but when i log out, i still see them on the login screen. How should i delete these?


Thanks,
Vader95

---

### Post by michy99 on 2010-01-12
Did you reboot or just log out? If you didn't reboot, try that.

---

### Post by vader95 on 2010-01-12
> **michy99 said:**
> Did you reboot or just log out? If you didn't reboot, try that.

I tried both, and a shut down.

---

### Post by michy99 on 2010-01-12
What method did you use to delete the user?

---

### Post by vader95 on 2010-01-12
> **michy99 said:**
> What method did you use to delete the user?

I went under my original user account.

went to:
system
administration
Users and groups
entered my password
deleted the user account

---

### Post by doas777 on 2010-01-12
it is probably being stored by gdm, though who knows where. my guess is that removing the user will not clear up the issue, because the user is in fact  gone, but that gdm still remembers that they used to be here, and hasn;'t realized that they should go away.

---

### Post by vader95 on 2010-01-12
> **doas777 said:**
> it is probably being stored by gdm, though who knows where. my guess is that removing the user will not clear up the issue, because the user is in fact  gone, but that gdm still remembers that they used to be here, and hasn;'t realized that they should go away.

do you know how to fix this.

---

### Post by doas777 on 2010-01-12
> **vader95 said:**
> do you know how to fix this.not off the top of my head. try a little googling...it's what i would do

---

### Post by vader95 on 2010-01-12
> **doas777 said:**
> not off the top of my head. try a little googling...it's what i would do

OK,

Thank you very much, I'll let you know if i find anything.

---

### Post by vader95 on 2010-01-12
Here is how you do it

```
sudo userdel -r <then the user name>
```

i found this here 

[http://ubuntuforums.org/showthread.php?t=211063](http://ubuntuforums.org/showthread.php?t=211063)

thanks, :D
vader95

---

