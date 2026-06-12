---
title: "Kontact sync problem - libmultisynkpart.la?"
date: 2006-05-27
forum: General Help
---

### Post by petteri on 2006-05-27
Hello,

I'm trying to get my Palm Treo 650 phone synced with Kontact, but I can even get past pressing "sync" button in Kontact. When I do I get the following error:

> Cannot load part for Synchronization.
Library files for "libmultisynkpart.la" not found in paths.

What does this mean? I tried searching for it here and in Adept but found nothing. I did install the multisync packages but that didn't change anything. Can anyone help?

Thanks!

---

### Post by glinsvad on 2006-05-27
I'm pretty sure Kontact uses multisynk to syncronize calendars etc. Try installing kitchensync - is is listed as "Recommends" for installing Kontact as it contains the multisynk GUI frontend.
```

sudo apt-get install kitchensync

```

---

### Post by tim.rittman on 2007-05-16
Thanks, that worked for me! :)

---

