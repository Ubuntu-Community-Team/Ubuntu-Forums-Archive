---
title: "How to disable authentication for software centre"
date: 2010-12-20
forum: General Help
---

### Post by karthick87 on 2010-12-20
I am the only user.So i would like to disable authentication for software center and update manager which is being asked everytime when i install softwares/updates..How to acheive it???

---

### Post by garvinrick4 on 2010-12-20
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mastablasta on 2010-12-20
> **karthick87 said:**
> I am the only user.So i would like to disable authentication for software center and update manager which is being asked everytime when i install softwares/updates..How to acheive it???
 
 
you are coming from windows aren't you? well the thing is authentication is there to check that it was you (the user) that requested the change of system files not some virus or malicious programme. it's there to protect your computer from malicious programmes. not to verify that it is really you sitting in front of the monitor.

---

### Post by karthick87 on 2010-12-20
I have edited the sudoers file,and gave
> karthick ALL=NOPASSWD: ALL

But still software centre is asking for password..

---

### Post by HermanAB on 2010-12-20
> But still software centre is asking for password.

Fortunately the Linux security measures are not that simple.

Relax and enjoy your nice secure system and get used to typing in your password.

---

### Post by Elfy on 2010-12-20
The long and short of it is that there are ways to do it - however as this forum is joined regularly by people from other OS's who want this to mimic that with no thought about the security of changing the best you can do is look for the information that is available already.

Closed.

---

