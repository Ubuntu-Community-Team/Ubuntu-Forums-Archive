---
title: "ubuntu 11.04 User swicth in shell - some function stop working"
date: 2011-05-06
forum: General Help
---

### Post by rabla on 2011-05-06
Hi.

When i switch from the shell from my main user account to another one:

```
sudo su - git
```

it switches correctly, however some things stop working:
Tab - autocompletion
Arrow up(history)/down/left/right - it just types ^[[A^[[B^[[B	
Home/End - types ^[OF^[OH^

and some other less important actions. Is is possible to fix this?

---

### Post by imigueldiaz on 2011-05-06
> **rabla said:**
> Hi.

When i switch from the shell from my main user account to another one:

```
sudo su - git
```

it switches correctly, however some things stop working:
Tab - autocompletion
Arrow up(history)/down/left/right - it just types ^[[A^[[B^[[B	
Home/End - types ^[OF^[OH^

and some other less important actions. Is is possible to fix this?

Test if git user is using bash as shell :)

Best

---

### Post by rabla on 2011-05-06
> **imigueldiaz said:**
> Test if git user is using bash as shell :)

Best

Ty! It helped :) The problem was indeed in the wrong shell


For the newbies like me who will be struggling with this problem:

i logged in under that user account 
typed
```
chsh
```
and entered
```
/bin/bash
```

logged out, and logged in again

Cheers!

---

