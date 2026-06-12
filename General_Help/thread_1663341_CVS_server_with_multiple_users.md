---
title: "CVS server with multiple users"
date: 2011-01-09
forum: General Help
---

### Post by mrmozart on 2011-01-09
Hello,
I have tried this a hundred different times during many years without succeeding. Hopefully someone can help me this time so that I can finally get it to work fully.

The small thing that I want to have a CVS server for multiple users that should be able to work (read+write) to the same projects.

Many will probably suggest to use another system, but I have no choice here.

Right now I have a functional CVS server with SSH connection. I have two users who belong to the usergroup "cvsusers". The group connection for the cvsroot is set to cvsusers:

morgan@ProvecoCVS:~$ ls -al /var/lib/cvs/
total 12
drwxrwxr-x  3 root cvsusers 4096 2011-01-09 18:50 .
drwxr-xr-x 61 root root     4096 2011-01-09 18:51 ..
drwxrwxr-x  3 root cvsusers 4096 2011-01-09 18:50 CVSROOT

The problem is that when the user "morgan" adds a project with Eclipse, the project is created as belonging to morgan rather than cvsusers. This means that when the second user, "anders", tries to commit changes he doesn't have authorization for this.

How to set it up so that multiple users can work with the same projects?

---

### Post by McNils on 2011-01-09
Why cvs??? Thease days it exist way better version control systems like git, mercurial, bazaar, svn...

---

### Post by HermanAB on 2011-01-09
The CVS administrator should create projects.  So Morgan should log in as the admin user for that task.

Another crummy way is to run a cron job every hour to fix the permissions.

---

### Post by mrmozart on 2011-01-09
> **McNils said:**
> Why cvs??? Thease days it exist way better version control systems like git, mercurial, bazaar, svn...

Like I said, I don't have an option. The system that I am working with only supports CVS (unless I should spend much more work trying to integrate one of the other solutions myself).

---

### Post by mrmozart on 2011-01-09
> **HermanAB said:**
> The CVS administrator should create projects.  So Morgan should log in as the admin user for that task.

Another crummy way is to run a cron job every hour to fix the permissions.

Well, we are all kind of administrators here. Cron job is not an option since we need to wait for it.

---

### Post by mrmozart on 2011-01-09
Found the solution!

By setting the setgid flag ("sudo chmod g+s /var/lib/cvs") new files created inherit the group ownership from the folder.

---

