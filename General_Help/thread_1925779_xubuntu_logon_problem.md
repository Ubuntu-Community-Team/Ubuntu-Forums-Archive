---
title: "xubuntu logon problem"
date: 2012-02-15
forum: General Help
---

### Post by FemmeFatale on 2012-02-15
Hello, 

Here is a brief overview of my issue -- i am using xubuntu 11.10, running on VirtualBox. It was all good. For some reason, today when I tried to logon, it said my password is incorrect. This happens for second time -- the first time I used another host machine, another instance. I believe it's kind of bug. May anyone tell me what's the reason or have you experienced issue like this one?

The solution is to logon as guest, sudo bash, and delete your .personal settings in /home/problem_user/. Well, that's how I solved the issue, i guess it's not required to delete the entire content of /. however i dont have time to fight against stupid bugs.

Anyone?

---

