---
title: "Understanding sudoers/sudo effect"
date: 2009-06-29
forum: General Help
---

### Post by HavocXphere on 2009-06-29
I want to remove the password prompt for certain applications (truecrypt in this case) and sudoers seems to be the way to go. I'll hopefully manage the details by myself...I'm just trying to understand things atm.

I don't want to run the commands *as* root. I only want temporary full privileges for the current user. i.e. ~  should still point to the current user's home and any files created should have all the permissions set as if created by the normal user.

As far as I can tell sudo runs the command *as* root...and sudoers will probably do the same. Thats what it sounds like in "man sudo":
> The real and effective uid and gid are set to match those of the target user

Any ideas on how to get temporary full privileges without completely changing user?

I hope the above makes sense.:oops::redface:

---

### Post by kerry_s on 2009-06-29
nope, don't make sense. sounds like your trying to bypass the way truecrypt works, then what would be the purpose of encryption.

---

### Post by beastrace91 on 2009-06-29
As far as I am aware there really is not a way to do what you want, the super user is there for a reason. There is how ever a way you can set it up so certain applications can be run as root with out a password prompt (how ever this is not recommended) but you will loose this effect doing this:> i.e. ~ should still point to the current user's home and any files created should have all the permissions set as if created by the normal user.

~Jeff

---

### Post by HavocXphere on 2009-06-29
> **kerry_s said:**
> bypass the way truecrypt works, then what would be the purpose of encryption.
No, truecrypt was just an example. I choose it because that is what I'll be using it for. But the question is the same for Gedit etc.

> **beastrace91 said:**
> There is how ever a way you can set it up so certain applications can be run as root with out a password prompt
Thats the plan. (Script to back-up into a truecrypt container)

> **beastrace91 said:**
> but you will loose this effect doing this:[snip]
So effectively I'd have to chown any files afterwards to fix any ownership issues? urgh

---

### Post by kerry_s on 2009-06-29
i think i see what your trying to do, use the "NOPASSWD" then just use sudo in your script.
example:

**%users ALL=NOPASSWD: /sbin/truecrypt**

i did "%users" for you that will allow any user in the users group to run it.
check the path, i don't have true crypt, so i'm not sure where its installed.run in terminal> **whereis truecrypt**

i use a couple on mine for the main programs. you can put it all on 1 line, but i like to separate it by location on mine. "user" is my log in name, i'm the only 1 that uses this pc.

---

### Post by whitethorn on 2009-06-29
If you use a script with tar to backup and archive your data , there's an option to keep the user ownerships.  So all you need to do afterwards is to unpack it to the same location and everything should be as b4.

---

### Post by HavocXphere on 2009-06-30
Apologies to all for the vagueness of this thread.:redface:

> **whitethorn said:**
> If you use a script with tar to backup and archive your data , there's an option to keep the user ownerships.  So all you need to do afterwards is to unpack it to the same location and everything should be as b4.
I'm using a mixture of rdiff-backup and rsync. I'll investigate whether they support this keeping ownerships thing too.

> **kerry_s said:**
> **%users ALL=NOPASSWD: /sbin/truecrypt**

i did "%users" for you that will allow any user in the users group to run it.
Thanks.

Looks like I'll fix sudoers as suggested for the truecrypt and then use chown to fix any permission damage done.

EDIT: cr*p. New problem: sudo chown needs a sudo too and I can't sudoers the chown command. Catch 22.

---

