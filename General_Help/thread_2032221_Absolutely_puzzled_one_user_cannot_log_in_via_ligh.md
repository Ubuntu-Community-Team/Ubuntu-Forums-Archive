---
title: "Absolutely puzzled: one user cannot log in via lightdm into any workstation"
date: 2012-07-23
forum: General Help
---

### Post by loximann on 2012-07-23
Hi,

First of all, in my bewildered mental state, I was not sure about where to post this.

Today, one user  force-closed a workstation and since then he has not been able to log in to any of the machines in the network using lightdm (he was kicked out immediately). Logging in via tty works fine. User authentication is managed via NIS. The user home directory is remotely mounted via NFS.

The first thing I thought was that some user configuration file had gone bonkers, so I moved his home somewhere else and created a new clean home directory. Since then, trying to log in doesn't bounce him out, but freezes X (sudo service lightdm restart does not help).

So:
- It cannot be a problem with some files at $HOME because it was perfectly clean.
- It cannot be a workstation configuration problem, because he cannot log in any workstation in the network (plus other users can log in into the original workstation).

Is it possible that some files on the server configuration became corrupted? How could I track where the problem is? I had a look in /var/log/lightdm but saw nothing of interest, although that probably means I don't know how to interpret it.

For the moment I have created a new account for him, and everything is fine. But this is *very* weird.

---

