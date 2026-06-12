---
title: "apt-get What is difference between purge and autoremove?"
date: 2012-05-21
forum: General Help
---

### Post by charleswb on 2012-05-21
I'm working on learning terminal and command line stuff. Need some help/advice.

What is the difference between "apt-get purge" and "apt-get autoremove" ?

I've read the command line "help" and "man" for both. The descriptions sound similar, but use slightly different wording.
[COLOR=Navy]
**What (if anything) is the difference between purge and autoremove?**[/COLOR] 

Please advise. Thank your for your help.

---

### Post by Cheesemill on 2012-05-21
They do completely different things.

**apt-get remove <package>** will un-install a package but leave all of it's configuration files in place. If you re-install the package later all your settings will still be intact.

**apt-get purge <package>** does the same as above but also removes all of the configuration files.

**apt-get autoremove** is used without specifying a package. It removes any packages on your system that are no longer needed. As an example if I install package A, it might install packages B and C as dependencies. Simply un-installing package A doesn't automatically un-install packages B and C as well, they are left installed. apt-get autoremove searches your system for packages that have been installed as dependencies but are no longer used and removes them.

This is one of the reasons that I use the aptitude command instead of apt-get, it automatically takes care of this for you whenever you un-install packages.

---

### Post by charleswb on 2012-05-23
Thanks for your help above.

Could you provide an example of using aptitude?

I tried man aptitude, but got nothing.

I tried aptitude help, but got nothing.

Confused.

---

### Post by oldos2er on 2012-05-23
aptitude is no longer installed by default, you need to install it yourself: ```
sudo apt-get update && sudo apt-get install aptitude
```

---

### Post by charleswb on 2012-05-23
Got it installed, but no idea what to do with it now. I guess search the web for documentation or instructions about aptitude?

---

### Post by childe joseph on 2012-05-23
> **charleswb said:**
> Got it installed, but no idea what to do with it now. I guess search the web for documentation or instructions about aptitude?

You use it in the terminal in place of "apt-get". For example:

user@ubuntu:~$ sudo aptitude install <package>

and now that aptitude is installed on your system you should

user@ubuntu:~$ sudo aptitude --help

---

