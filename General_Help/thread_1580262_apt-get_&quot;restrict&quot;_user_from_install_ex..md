---
title: "apt-get &quot;restrict&quot; user from install ex. dhcpserver"
date: 2010-09-23
forum: General Help
---

### Post by romulan on 2010-09-23
Hi I am managing a large amount of ubuntu 10.04 machines in a corporation.

Due to pressure from the user we had to give them the sudo access to use apt-get install but we want to be able to stop the users from installing packages that can break the machine or the IT environment.

Like users installing a dhcpserver or any other type of server function that they should not use.

Tried to google and look at forums to find a way to restrict or block users but can't find anything.

Can you help me?
//Erik

---

### Post by romulan on 2010-09-24
Any news?

---

### Post by lloyd_b on 2010-09-24
That is going to be tough to solve - you've given them the ability to 'sudo' and access the program to install, so there isn't any simple way to keep them from installing certain packages.

One possibility, but it'll involve a lot of work - create your own repository, containing only those packages that they are permitted to have installed.  Then direct their machines to use that instead of Canonical's repos.

Besides the hassle of setting up the repository, and figuring out which packages to include/exclude from it, you'll also have to worry about keeping that limited repository updated.

Sorry I couldn't give you a more reasonable answer, but I really don't think there is one...

Lloyd B.

---

### Post by QLee on 2010-09-24
[QUOTE=romulan]...
Due to pressure from the user we had to give them the sudo access to use apt-get install but we want to be able to stop the users from installing packages that can break the machine or the IT environment.
...[/QUOTE]
There was your mistake, no you did not "have" to give them sudo access and you should not have done so. The whole issue should be handled by corporate policy, it's a company machine and the company has the right to specify how it is used. Then you as IT support could install any personal software for your users if it is approved by the IT department. The situation you are now in is a support nightmare waiting to happen, maybe even worse than that if you store any confidential information that you are required by law to protect. If you cannot convince the management to ban giving users sudo permissions, I suggest you clean up your resumé and start a job search.

---

### Post by CharlesA on 2010-09-24
> **QLee said:**
> There was your mistake, no you did not "have" to give them sudo access and you should not have done so. The whole issue should be handled by corporate policy, it's a company machine and the company has the right to specify how it is used. Then you as IT support could install any personal software for your users if it is approved by the IT department.

Bingo.

You don't just give a user "admin" privileges in a corporate environment. The general rule of thumb is to give only the privileges a user needs to get their job done. No more.

If they need something installed, they should email the IT people and have them install it if it is needed.

---

### Post by romulan on 2010-09-28
Thanks for the feedback.
I was thinking that we need to back the sudo access to apt-get and just create more specific meta files.

Today we are using that we call site-build-required and site-build-required-gui-addon.

Was hoping there was a "clean" easy to way restrict users. 
So I guess its back to drawing board. 

Thanks again for feedback!

---

