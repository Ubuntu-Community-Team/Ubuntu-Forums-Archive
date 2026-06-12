---
title: "Am I having internet connection problems?"
date: 2010-02-05
forum: General Help
---

### Post by Jackzor on 2010-02-05
I can't tell if its my computer or just the internet?

I'm just running the GUI Update Manager.

---

### Post by Jackzor on 2010-02-05
I know that this is a seperate issue but I am not sure how to fix it either so I'll just go ahead and post it here instead of making a new thread.

---

### Post by raffytaffy on 2010-02-05
> **Jackzor said:**
> I know that this is a seperate issue but I am not sure how to fix it either so I'll just go ahead and post it here instead of making a new thread.

You need to add the key for this source to fix this.

---

### Post by Jackzor on 2010-02-05
> **raffytaffy said:**
> You need to add the key for this source to fix this.

How do I do this? I'm kinda lost when it comes to the keys and stuff still

---

### Post by r_s on 2010-02-05
[http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

---

### Post by gmargo on 2010-02-05
What "ppa.launchpad.net" directory are you trying to use?

---

### Post by gmargo on 2010-02-05
> **Jackzor said:**
> I can't tell if its my computer or just the internet?


The error was "lock temporarily unavailable" so there's probably another update running at the same time.

---

### Post by Teunis on 2010-02-05
Have a look in something like top to see if there's another updater running.
Because that's what the first message implies.

When sure there is no such thing then you can manually delete the lock file mentioned (/var/cache/apt/archives/lock) and then continue with the update.

It just happens when you have a crash during an update this file remains in place and prevents the next update running.

---

