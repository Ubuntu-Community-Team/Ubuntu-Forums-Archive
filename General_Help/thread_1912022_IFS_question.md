---
title: "IFS question"
date: 2012-01-19
forum: General Help
---

### Post by Diametric on 2012-01-19
Hi,

Is the Internal Field Separator always reset with each new login?  Meaning, when you log into bash, is the default IFS space, tab and new line even if you set it to something else in a previous session? 

Thanks!

---

### Post by Buntumatic on 2012-01-19
Not sure of your problem, but ~/.bashrc is sourced every time you log in, whatever you need put it in there.

---

### Post by Diametric on 2012-01-19
There is no problem, I'm just trying to understand how this works.  I think the answer is that, unless a change is made in the ~/.bashrc, all changes it a script or function go back for any new session.  Correct?

---

### Post by Buntumatic on 2012-01-19
Yes, and that's a great thing, you do not need to reboot just to reset to defaults. As a matter of fact, a true multiuser system would not function in any other way.

---

### Post by Diametric on 2012-01-19
Awesome.  Thanks for your replies!

---

### Post by Buntumatic on 2012-01-19
You are welcome!

It's not only about bash, practically every conf is set in /etc with user override in ~/. Generally, there is /etc/profile that sets defaults for login shell, you can override it in ~/.bashrc (for bash) as user, every user can create his/her own defaults this way. 
BTW, in some cases configuration settings in /etc can take precedence and users cannot override it. In this case it is up to discretion of admin which settings can be overridden by users. For instance, you as an admin may want to restrict users to a certain mail server or whatnot. That's the beauty of UNIX systems, all is simple and clear.

---

