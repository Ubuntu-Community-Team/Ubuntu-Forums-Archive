---
title: "Permissions -- Reset to defaults?"
date: 2011-01-31
forum: General Help
---

### Post by zzzBrett on 2011-01-31
After a regrettable typo, I reset all the permissions in my filesystem. What is the easiest way to restore my permissions to how they were? Is there a list where i can find the recommended permission settings for each directory?

---

### Post by Frogs Hair on 2011-01-31
User permissions can be changed from System > Administration > Users and Groups. I'm not sure if that is what you mean.

---

### Post by Habitual on 2011-01-31
You're going to have to re-install

---

### Post by zzzBrett on 2011-01-31
> **Habitual said:**
> You're going to have to re-install

Any other options? I still have access to the machine remotely. I'm hours away and would prefer not to do a remote re-install.

Thanks

---

### Post by Habitual on 2011-01-31
while your system may be somewhat usable, the only way to restore default permissions is to re-install.

the upside is that you'll never do "that" again. Sorry to be blunt.

---

### Post by zzzBrett on 2011-01-31
> **Habitual said:**
> while your system may be somewhat usable, the only way to restore default permissions is to re-install.

the upside is that you'll never do "that" again. Sorry to be blunt.

Alright, thanks.

Any recommendations on how to just get ssh working? All i have access to right now is webmin (i'm working remotely). I have seen how-to's on re-installing. If it doesn't work out, i can drive to it and fix it in the next week or so, but i'd like to try to get it running now.

---

### Post by zzzBrett on 2011-01-31
This sucks.. i was one character off!

sudo chmod 744 -R /.

instead of

sudo chmod 744 -R ./

I did end the process as soon as i realized, but ssh and many other services are already messed up. Any recommendations on how to get back ssh? I have remote access via webmin and can run commands using that.

---

### Post by Habitual on 2011-01-31
```
apt-get remove openssh-server --purge
apt-get install openssh-server
```
?

Good luck

---

