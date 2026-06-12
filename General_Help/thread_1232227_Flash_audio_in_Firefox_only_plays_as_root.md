---
title: "Flash audio in Firefox only plays as root"
date: 2009-08-05
forum: General Help
---

### Post by Scienceman123 on 2009-08-05
I recently updated Firefox (Ubuntuzilla), and noticed that on sites such as Youtube, audio only plays when Firefox is run as root. I am in all PulseAudio-related groups.

---

### Post by Scienceman123 on 2009-08-05
Bump.

---

### Post by nanotube on 2009-08-06
any chance any of your profile files ended up being owned by root? try running
```
sudo chown -R yourusername:yourusername ~/.mozilla
```

---

### Post by lswb on 2009-08-06
I sometimes have to 
```

$ rm .pulse-cookie
$ rm -r .pulse

```
to get sound. Don't know why yet but if I don't figure it out soon I'm just going to put those commands in my .profile

---

### Post by Scienceman123 on 2009-08-08
> **nanotube said:**
> any chance any of your profile files ended up being owned by root? try running
```
sudo chown -R yourusername:yourusername ~/.mozilla
```

That did it! Thank you so much!

---

### Post by nanotube on 2009-08-08
> **Scienceman123 said:**
> That did it! Thank you so much!

you're welcome :)

---

