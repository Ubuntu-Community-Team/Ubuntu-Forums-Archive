---
title: "How can I get rid of text screen when shutting down?"
date: 2010-05-10
forum: General Help
---

### Post by crjackson on 2010-05-10
Ubuntu 10.04 - Clean install

Laptop - HP Pavilion dv6929nr

Graphics - Intel X3100

When shutting down the desktop, The screen goes black with white text detailing what I believe is the shutdown process and modules closing out.  Then the purple Ubuntu splash screen comes on until the shutdown is complete.

Does anyone know how to kill the text display?

Thanks

---

### Post by crjackson on 2010-05-11
23 1/2 hour bump

---

### Post by GSF1200S on 2010-05-11
> **crjackson said:**
> 23 1/2 hour bump

I got the black screen with flashing cursor on startup and shutdown as I had an nvidia driver issue, which has since been patched in the X ppa. I say this because I dont know if this link will fix your problem, but for me it presented a splash screen (plymouth) and made the transition between the kernel and X smooth. It uses v86d to do the plymouth rendering- you can give it a try (easy to revert back):
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by crjackson on 2010-05-12
I've actually done this already and it fixed everything except the problem mentioned in the title.

Thank for the reply though.

---

### Post by crjackson on 2010-05-13
Okay, so I've tried every posted solution I can find.  The boot splash works fine, but when I shut down or restart I get a screen full of killed processes and then the shutdown splash screen.

If anyone else has an idea please jump in and let me know.

---

### Post by cavh on 2010-05-13
Suggest installing startupmanager and then using that
```

sudo apt-get install startupmanager
```

See screenshot attached

---

### Post by crjackson on 2010-05-13
> **cavh said:**
> Suggest installing startupmanager and then using that
```

sudo apt-get install startupmanager
```

See screenshot attached

I already tried that.  startupmanager caused more problems than you can shake a stick at on 3 of my machines.

I highly discourage startupmanager on any Lucid machine.

---

