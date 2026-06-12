---
title: "Allow a regular user to run root apps?"
date: 2009-07-14
forum: General Help
---

### Post by falkTX on 2009-07-14
Hi there, I have a simple question

I want to be able to launch a program (let's say "startupmanager") as a regular user, without need to run 'sudo startupmanager'. Or maybe create a rule file somewhere that will automatically run the app as root (without asking for a password)

I've been searching for policy kit rules, but they don't seem to support application launch (just triggers like 'mount', 'eject', 'load')

So, is there a way for this?

---

### Post by Finalfantasykid on 2009-07-14
I've never really used this very much so I might be wrong about this, but if you go to System > Administration > Authorizations...you might be able to change which features require a log in from root.

---

### Post by swisstone198 on 2009-07-14
You can edit /etc/sudoers with a line as follows:

user ALL=NOPASSWD: /path/command 

that will allow you to run sudo without having to enter a password, then you can just create a launcher somewhere to run the command. Or you can alias the command to sudo command.

---

### Post by SunnyRabbiera on 2009-07-14
Just remember:
Running as root is dangerous, having no admin password is also dangerous.
Wonder why Windows has a million security flaws?
Thats right, no admin passwords/

---

### Post by rampageoberon on 2009-07-14
Hi there, yes you can allow some commands to work without a password when using sudo. You need to set this up in your sudoers configuration file.

Please see this for an example
[http://www.sudo.ws/sudo/sample.sudoers](http://www.sudo.ws/sudo/sample.sudoers)

Hope that helps.

---

### Post by falkTX on 2009-07-15
Thanks all. I'll try this now

---

