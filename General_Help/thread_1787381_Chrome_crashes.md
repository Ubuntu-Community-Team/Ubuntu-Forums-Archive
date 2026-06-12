---
title: "Chrome crashes"
date: 2011-06-21
forum: General Help
---

### Post by anshulfy on 2011-06-21
Hi,

I am having a problem with Chrome-browser. Whenever I open it, i get the following error.

--
Your profile could not be opened correctly.

Some features may be unavailable.  Please check that the profile exists and you have permission to read and write its contents.
--

After that when I try to access preferences, it crashes without any warning or error. 
I uninstalled it and reinstalled but that's also not helping. I don't know what to do. Please help me.

--
Anshul

---

### Post by TeoBigusGeekus on 2011-06-21
Sounds like a home folder's permission problem.
Make sure that you're the owner of your home folder
```
sudo chown -R yourusername ~/
```

---

### Post by anshulfy on 2011-06-21
Thanks for your reply.....but a restart solved my problem.

---

