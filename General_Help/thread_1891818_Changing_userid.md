---
title: "Changing userid"
date: 2011-12-06
forum: General Help
---

### Post by eks on 2011-12-06
Hello,

I just did a clean install of 11.10, but preserving /home on another partition (and deleting all the .config directories). But my user had a 1001 ID, whereas the new user is 1000. How do I change my user ID?

The new User Account Settings is HORRENDOUS. There's NOTHING there, how can I configure something? I remember it was quite easy before.

Why hide out these stuff? Why not leave that under an advanced settings somewhere?? I can't even configure what a "standard" or "administrator" account is!

---

### Post by Lars Noodén on 2011-12-06
One way is with the GUI:

Dash->Users and Groups->Advanced Settings->Advanced->User ID

Another is with [usermod](http://manpages.ubuntu.com/manpages/precise/en/man8/usermod.8.html).

```

sudo usermod --uid 1001 eks 

```

Either way it's probably best if you are not logged in to the account to be changed at the time you make the change.

Edit: You'll probably also want to change the group, too.  Assuming that it is also 1001:

```

sudo usermod --uid 1001 --gid 1001 eks 

```

---

### Post by eks on 2011-12-06
Thanks for the answer Lars!

I'll read usermod man's page and try it out.

Because I don't have a "Users and Groups", just a "User Accounts" that basically just lists users on the system with a couple of options. And no "Advanced Settings" in sight... :(

Is there any other gui program with that? That Users and Groups you mentioned is anywhere in any repository?

---

### Post by Lars Noodén on 2011-12-07
The 'Users and Groups' should have an equivalent on your system, somewhere.  I got the instructions from looking at Precise, so it looks like it might have changed since Oneiric.

---

