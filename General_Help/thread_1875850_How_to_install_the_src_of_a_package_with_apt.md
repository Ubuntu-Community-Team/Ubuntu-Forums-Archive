---
title: "How to install the src of a package with apt?"
date: 2011-11-05
forum: General Help
---

### Post by georgelappies on 2011-11-05
Hi all, I want to have a look at some of the source code of games from ubuntu.

How can I install the src of an app that is available in the repos? For instance chromium-bsu?

---

### Post by haqking on 2011-11-05
> **georgelappies said:**
> Hi all, I want to have a look at some of the source code of games from ubuntu.

How can I install the src of an app that is available in the repos? For instance chromium-bsu?

```
apt-get source packagename
```

---

### Post by georgelappies on 2011-11-05
> **haqking said:**
> ```
apt-get source packagename
```


Thank you for the fast response!

---

### Post by haqking on 2011-11-05
> **georgelappies said:**
> Thank you for the fast response!

no worries, remember to use thread tools to mark thread as solved.

Cheers

---

### Post by oldos2er on 2011-11-05
No need to use 'sudo' when downloading source. **apt-get source <package>** will suffice.

---

### Post by haqking on 2011-11-05
> **oldos2er said:**
> No need to use 'sudo' when downloading source. **apt-get source <package>** will suffice.

ahh yeah good catch, in a world of my own.

edited.

cheers

---

### Post by oldos2er on 2011-11-05
> **haqking said:**
>  in a world of my own.

I usually am too.  :)
Thanks for editing your post.

---

