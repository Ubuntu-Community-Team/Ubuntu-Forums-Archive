---
title: "Git problems"
date: 2011-07-16
forum: General Help
---

### Post by renegadeandy on 2011-07-16
Hey folks.

I have a git repository setup on a server:


andy@ubuntu:/home/git/repositories$ ls
gitosis-admin.git  GoGoFlow.git
andy@ubuntu:/home/git/repositories$ pwd
/home/git/repositories

All fine and dandy.

I then come to a new machine - which I have not used before with git **I manually added my machines public key into the export_dir/keydir in the gitosis project**

and type:

git clone [email]git@novo.dyndns.tv[/email]:GoGoFlow
Cloning into GoGoFlow...
[email]git@novo.dyndns.tv[/email] password:<passwd>
fatal: GoGoFlow.git does not appear to be a git repository
fatal: The remote end hung up unexpectedly

Have I missed a setup step in my new git installation **windows 7**?

Cheers

---

### Post by renegadeandy on 2011-07-16
anyone got any experience with fixing this kinda git problem!?

---

### Post by renegadeandy on 2011-07-16
help help! Still stuck on this and cannot start developing until I can access my repo!?

---

### Post by renegadeandy on 2011-07-16
Well some kind folks on stack overflow helped me solve the problem. It was because it was managed by gitosis - had to get to my other machine which was an admin on gitosis - and add the public key for this new pc to the repo, and to the projects list. 

After doing that it was all fine.

---

