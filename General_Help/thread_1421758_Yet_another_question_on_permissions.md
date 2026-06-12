---
title: "Yet another question on permissions"
date: 2010-03-04
forum: General Help
---

### Post by belnac on 2010-03-04
Hi,

I've set up a mercurial master repository in /rep and gave it ownership to root:developers, developers being a group I created. I then included my user name in that group so I could pull/push from the repo.

Trouble is I cannot do any commits in my local repos (the ones I pull from /rep to work locally on) and I'm getting the error: "Could not lock working directory"

I've given my local repo g+rwx, u+rx and o+x, as can be seen by the following permissions:
dr-xrwx--x for a directory
-r-xrwx--x for a file

I'm a Linux newbie, however I would've most likely found the solution to this little annoying issue if I hadn't had a long day and weren't too tired, so i'm giving up today. But I'd really appreciate it if any of you guys could show me the light and tell me the permission(s) I need to set.

Thanks!

---

### Post by Agent ME on 2010-03-04
Have you logged out and back in since adding yourself to the developers group?

Are you sure all files under /rep have the right permissions set?

Can you post the output of the command "groups", and "ls -l /rep"?

---

### Post by belnac on 2010-03-05
> **Agent ME said:**
> Have you logged out and back in since adding yourself to the developers group?

Are you sure all files under /rep have the right permissions set?

Can you post the output of the command "groups", and "ls -l /rep"?

Nothing like a good night's sleep to restore awareness and perception!

Got it working just now. Turns out I'd forgotten to grant user write permissions on some directories.

Thanks for your reply man.

---

