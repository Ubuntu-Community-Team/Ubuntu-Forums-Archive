---
title: "Multiple versions of Ubuntu OS"
date: 2011-06-10
forum: General Help
---

### Post by ManishV on 2011-06-10
Hi,

I have installed windows vista and Ubuntu. At the time of starting the computer, I have to choose between many versions of Ubuntu. I dont want to have such long list of ubuntu versions. How can I ensure that there is only one version available.

Also I dont want the ubuntu OS to be user specific and it should start without asking password. I tried to have a look at the settings to remove password but couldnt find anything.

---

### Post by john77eipe on 2011-06-10
If you have old versions of Linux kernels and if you wish to remove them, use Synaptic package manager.

But before you do that check the current verison of kernel you are using. Use the command uname -r. 
In my case, it's 2.6.35-28.
```

$ uname -r
2.6.35-28-generic

```

which means I can remove the older versions.

Open the Synaptic package manager from the System>Administration menu.

Search for linux-image-2. Mark the old versions for removal. Click Apply.

---

### Post by ManishV on 2011-06-12
Thanks a lot. It worked.

---

### Post by john77eipe on 2011-06-12
Welcome to Ubuntu forms. :p
If you do not have any more questions, you can mark this thread as solved.

---

### Post by VanR on 2011-06-12
You really should keep at least one of those older kernels to boot from just in case.

---

