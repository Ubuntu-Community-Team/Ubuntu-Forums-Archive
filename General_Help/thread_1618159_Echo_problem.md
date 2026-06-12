---
title: "Echo problem"
date: 2010-11-10
forum: General Help
---

### Post by Party on 2010-11-10
Hello! I recently installed ubuntu because i wanted to take a look at some other operating systems instead of windows.I gotta say i really like ubuntu.Alright here's the problem: A friend of mine told me that by typing PS1="" you don't see the User@user-System-Product-Name:~$ thing.You see just what you type.I want PS1="" to be executed whenever i open my terminal automatically.Is there any way i can do that? Thanks.

---

### Post by Crusty Old Fart on 2010-11-10
Check out your ~/.bashrc file:
```

cat ~/.bashrc

```
You'll discover where you can customize PS1= and a whole lot more. There's a ton of stuff on the 'net regarding how you can customize your terminal behavior by modifying .bashrc.

Have fun!

---

### Post by Party on 2010-11-10
Thank you!!

---

### Post by Crusty Old Fart on 2010-11-10
You're mighty welcome.

---

