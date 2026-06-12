---
title: "Correct way to add a user to an additional group"
date: 2009-10-17
forum: General Help
---

### Post by CharlesA on 2009-10-17
Hi all.

I was trying to add myself to the "raid" group on my machine.

I used to command: 

```

sudo usermod -G raid charles
  sudo usermod -G raid clone

```

I think that is where I screwed up. Now I'm not in any of the groups except for raid, meaning I am not in the admin group either, so no sudo for me.

I'll have to fix it when I get home by dropping myself into a root shell and fixing the screwup.

What's the correct command for adding yourself to an additional group?

Thanks!

---

### Post by coldReactive on 2009-10-17
You should be using the authorizations GUI or whatever in System > Administration to change your groups.

---

### Post by CharlesA on 2009-10-17
Unfortunately, I don't have access to that since I am accessing my server over SSH. The "unlock" function of users and groups isn't allowed for me.

Is there a command-line tool to do that?

---

### Post by coldReactive on 2009-10-17
> **CharlesA said:**
> Unfortunately, I don't have access to that since I am accessing my server over SSH. The "unlock" function of users and groups isn't allowed for me.

Is there a command-line tool to do that?

You'd still have to use gksudo to access the GUI unlocked, and sudo to change groups, etc. Meaning you're up a creek. Also, only the first user created in the ubuntu system is allowed to change the root password (even if you give yourself admin privledges again, you can't change the password of root without being the first created user. I had to reinstall my system when I found that out one day.)

---

### Post by CharlesA on 2009-10-17
I'll fix it when I get home, boot into a root shell from the machine and fix it there.

Anyway, the thing I am asking is: What's the correct way to add a user to an additional group without removing them from their other groups?

Thanks.

EDIT: Saw the last part of yer post. I guess I am SOL.

Time to reimage the drive.

---

