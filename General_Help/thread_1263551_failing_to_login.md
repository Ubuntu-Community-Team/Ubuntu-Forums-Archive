---
title: "failing to login"
date: 2009-09-11
forum: General Help
---

### Post by stooby on 2009-09-11
I rebooted an Ubuntu PC at work this morning, and when I attempted to log in, I got the following error message:

**GDM could not write to your authorisation file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator.**

Well, I am the system administrator, and I am stuck...

I have gone to the console and checked the disk space with df -h and the result showed the boot partition at 33% full, /home at 16% full and everything else at 6% or less.

I tried making a new user to test (called test), and got the following error:

**Your home directory is listed as: '/home/test' but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session.**

To which I click 'yes' and get the following error:

**User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.**

Then the original error '**GDM could not write to your authorisation file......**' comes up.

As the directory /home/test was not created, the .dmrc related error stumps me.

Could someone please point me in the right direction to solve this issue?

Thanks

Stooby

---

### Post by stooby on 2009-09-11
While I was waiting for some guidance, I continued to look for a solution myself.

I stumbled upon a suggestion that the problem was being caused by permissions settings on /tmp

So I typed the following:

```
sudo chown root:root /tmp
sudo chmod 777 /tmp
```

Tried logging in again, and it works.

---

