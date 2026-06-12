---
title: "Restoring default file permissions?"
date: 2009-09-02
forum: General Help
---

### Post by Vunutus on 2009-09-02
I know they say that given root access, someone will eventually type before they think and fubar their machine, and I just did.

I did a recursive chmod changing everything to 775 thinking I was in a sub directory, but alas, I was in /. Is there any magical way to undo this, or at the very least, get a list of default directory permissions and manually restore them?

---

### Post by asmoore82 on 2009-09-02
you should _***never***_ recursively chmod 775
the proper way to achieve the desired effect is with
```
chmod -R g+rwX,o+rX
```
the upper `X` is a smart mode selector that means
"only on all directories -OR- files that are already executable"

---

### Post by Vunutus on 2009-09-02
> **asmoore82 said:**
> you should _***never***_ recursively chmod 775
the proper way to achieve the desired effect is with
```
chmod -R g+rwX,o+rX
```
the upper `X` is a smart mode selector that means
"only on all directories -OR- files that are already executable"

Well, good to know that for round 2 but that's currently the least of my problems lol (this was supposed to change the permissions on a shared Samba network drive, not the whole working system).

Currently in the process of re-installing my server =(

---

