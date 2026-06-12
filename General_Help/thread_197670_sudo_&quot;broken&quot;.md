---
title: "sudo &quot;broken&quot;"
date: 2006-06-16
forum: General Help
---

### Post by flashman on 2006-06-16
Hi all,
        I just installed ubuntu on a laptop at work, as the laptop is not mine i didn't want sudo working. So i just chmod 600 /usr/bin/sudo (ofc i enabled su bfore :)), i know that editing sudoers would have been smarte now :).

       The thing is that now all graphical tools that require password are not working anymore. I have tried restoring privileges on sudo, and checked gksudo as well. No way.... :(

       Can i config gnome some how so it asks for root password and not user password? Can i restore sudo properly? 

       Is not big deal anyway as i can still use console, but it's annoying sometimes to use console for some simple things like changing time for example.I would appreciate any help. :)

---

### Post by lamego on 2006-06-16
sudo needs the "+s" (set user id) bit to work, which you have removed with your chmod.
To fix it:
```
chmod 755 /bin/sudo
chmod u+s /bin/sudo
```

---

### Post by flashman on 2006-06-16
thanks a lot lamego now it works perfectly

Great advice :)

---

