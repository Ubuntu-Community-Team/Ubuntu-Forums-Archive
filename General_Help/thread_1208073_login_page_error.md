---
title: "login page error"
date: 2009-07-08
forum: General Help
---

### Post by theo.ew on 2009-07-08
Whenever I login to Ubunut from the GDM it gives me this error message and then logs on.

User's $HOME/.drmc file is being ignored. This prevents the default session from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

What's going on here? I have Ubuntu 9.04 with all updates installed.

---

### Post by wojox on 2009-07-08
When you go to your /home directory and open the .drmc file what does it say?

---

### Post by merlinus on 2009-07-08
```
gksudo nautilus
```

Navigate to your user directory (/home/username), rightclick, properties, permissions.  Make sure user is owner with read&write, group is user with read&write, and others is read only.

---

### Post by theo.ew on 2009-07-08
the thing is there is no .drmc file in my home directory. I just changed the permissions of the home folder and will restart in a minute...so I will post the results soon.

---

### Post by theo.ew on 2009-07-08
changing the home/username folder permissions does not fix the problem.

---

### Post by synapsys on 2009-07-08
This problem has a known fix...

[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

PS there IS a .dmrc file in your home directory... it is hidden.

---

### Post by theo.ew on 2009-07-09
haha...sorry for my stupidness...hehe

I had my files aranged by type then alphabetically. I thought I had arranged them by alphabetically only. My fault...I'll look into that link and see if it fixes the problem.

---

### Post by theo.ew on 2009-07-09
that fixed the problem. Thanks!!

---

### Post by oboedad55 on 2009-08-15
> **synapsys said:**
> This problem has a known fix...

[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

PS there IS a .dmrc file in your home directory... it is hidden.

Thanks for the link. I had this problem with a Linux Mint installation.

Cheers,

---

