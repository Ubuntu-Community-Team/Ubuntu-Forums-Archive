---
title: "Logging in as root or super user, su"
date: 2010-05-23
forum: General Help
---

### Post by theKuch on 2010-05-23
How do I log in as superuser or create a root account?

---

### Post by SlidingHorn on 2010-05-23
When logged in as "root" you expose your system to great risk...yourself.  Your best bet is to use "sudo", which temporarily grants root privileges

---

### Post by lisati on 2010-05-23
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by VeeDubb on 2010-05-23
In addition to the good advice and links already posted, how about explaining why you feel the need to log in as root?

There are MANY ways to get any given job done, and it's pretty rare that actually logging in as root is your best option.

You can temporarily su to root, you can make sudo stick until canceled, you can modify group permissions to give a particular user access to specific files and folders.

Basically, you can do all sorts of stuff that is a whole lot safer than logging in as root.

Just an example of what people are concerned about, something as simple as using sudo to launch the file browser can mess up the permissions for the user who did it, making it impossible to log into a graphical desktop until you fix them.  There are simple, common and harmless commands that if entered as root can destroy your system.

In short, actually logging in as root is dangerous enough that if you have to ask how, you probably shouldn't be doing it, and most people who don't need to ask how, know better.

---

### Post by John Bean on 2010-05-23
> **VeeDubb said:**
> In short, actually logging in as root is dangerous enough that if you have to ask how, you probably shouldn't be doing it, and most people who don't need to ask how, know better.

Yes. 

To the OP: this advice always sounds condescending but it honestly isn't - it's a simple statement of fact. I think most of us have at some time been in the same situation as you are and been frustrated by the responses, but the policy of the forum not to directly answer such questions is sensible, as will be apparent to you after you burn your fingers (and you will) by ignoring the advice.

Been there, done that, fingers now healed :-)

---

### Post by Elfy on 2010-05-23
Further - [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

As it stands your immediate question has been answered - I'm closing this thread now.

---

