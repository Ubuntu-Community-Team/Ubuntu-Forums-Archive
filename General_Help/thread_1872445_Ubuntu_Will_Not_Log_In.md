---
title: "Ubuntu Will Not Log In"
date: 2011-10-30
forum: General Help
---

### Post by Jaybyrrd on 2011-10-30
Ok so I am using 11.10 Oneiric Ocelot, and currently whenever I type in my password at the login screen, the screen goes black, and then returns to the login screen where it just asks for my password once more?

Currently logged in as guest. Help?

JayByrd

---

### Post by Script Warlock on 2011-10-30
you forgot your login password?

---

### Post by Jaybyrrd on 2011-10-30
No I am not that bad.. (Really).

I actually did some preliminary work, got logged into as root by stop lightdm and sudo starting lightdm. Then from there did some research.


Solution.
```

cd /home/(username here)

sudo mv .Xauthority Xauthority.bak

Ctrl+Alt+F3

sudo service lightdm start

```

Login and all should be right with the world. :)

---

