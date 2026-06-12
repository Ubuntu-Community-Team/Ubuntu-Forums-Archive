---
title: "No users in user settings?"
date: 2009-12-02
forum: General Help
---

### Post by Baz6359 on 2009-12-02
Hi guys I put this in the beginners section but not had any luck, when I installed ubuntu I set up 3 users and they can all log in fine, however I can't see anyone other than root in user settings. Anyone know how to sort this please?

Thanks Baz

---

### Post by viralmeme on 2009-12-02
> **Baz6359 said:**
> Hi guys I put this in the beginners section but not had any luck, when I installed ubuntu I set up 3 users and they can all log in fine, however I can't see anyone other than root in user settings. Anyone know how to sort this please?

Thanks Baz

Possible the user needs to be a member of the 'Administer the system' group ?

---

### Post by adaucourt on 2009-12-02
> **Baz6359 said:**
> Hi guys I put this in the beginners section but not had any luck, when I installed ubuntu I set up 3 users and they can all log in fine, however I can't see anyone other than root in user settings. Anyone know how to sort this please?

Thanks Baz

are you logging in with a user who has admin privs? sounds like you are logging in with a desktop user or unprivileged account

---

### Post by Baz6359 on 2009-12-02
This happens when logged in as anyone including root!

---

### Post by Iowan on 2009-12-02
Old brain is getting dense again...
Where are you checking user settings?

---

### Post by Baz6359 on 2009-12-04
> **Iowan said:**
> Old brain is getting dense again...
Where are you checking user settings?

System>Administration>Users and groups

Still can't find the answer anywhere!

---

### Post by Baz6359 on 2009-12-15
Anyone experienced this or no how I can resolve it?

---

### Post by Baz6359 on 2009-12-22
There must be some guru that knows how to sort this out?

---

### Post by QLee on 2009-12-22
> **Baz6359 said:**
> This happens when logged in as anyone including root!

And how are you logging in as root, did you modify your system to allow root login?

---

### Post by Baz6359 on 2009-12-24
> **QLee said:**
> And how are you logging in as root, did you modify your system to allow root login?

Yes so I could see if the users appeared.

---

### Post by Iowan on 2009-12-24
User directories show up under /home?

---

### Post by Baz6359 on 2009-12-30
> **Iowan said:**
> User directories show up under /home?

Yes they do, any ideas?

---

### Post by jamesisin on 2009-12-30
Sorry, man.  This is really bazaar.

You should consider filing a bug report.

What happens if you attempt to create a new user (using the Users and Groups dialog)?

---

### Post by Baz6359 on 2010-01-01
> **jamesisin said:**
> Sorry, man.  This is really bazaar.

You should consider filing a bug report.

What happens if you attempt to create a new user (using the Users and Groups dialog)?

I can create a new user and log in as them but they don't appear users and groups really strange this!!

---

### Post by Leppie on 2010-01-01
> **Baz6359 said:**
> I can create a new user and log in as them but they don't appear users and groups really strange this!!

try re-installing gnome-system-tools from synaptic.

---

### Post by Baz6359 on 2010-01-01
> **Leppie said:**
> try re-installing gnome-system-tools from synaptic.

Tried still no joy.

---

### Post by jamesisin on 2010-01-02
You could try running users-admin as root to see what root sees.  I wouldn't recommend jumping in and making changes but I think this will make that happen:

gksudo users-admin

Which reminds me to ask: is this behavior consistent for all users?

---

### Post by Baz6359 on 2010-01-04
> **jamesisin said:**
> You could try running users-admin as root to see what root sees.  I wouldn't recommend jumping in and making changes but I think this will make that happen:

gksudo users-admin

Which reminds me to ask: is this behavior consistent for all users?


Tried and still the same, yes it's consistent no matter who you are logged in as.

---

### Post by jamesisin on 2010-01-04
Sorry, man.  I'll keep following this thread and I'll let you know if I have any other ideas.

---

### Post by Baz6359 on 2010-01-05
Thanks mate, got the same version of ubuntu installed on another PC a laptop and a net book and there fine, at a loss now!!

---

### Post by polki@mac.com on 2010-01-05
I may be very wrong but I think I read something about user id being lower than 1000 made them invisible in the login window, could that be the case here as well?

---

### Post by Baz6359 on 2010-01-05
> **polki@mac.com said:**
> I may be very wrong but I think I read something about user id being lower than 1000 made them invisible in the login window, could that be the case here as well?

Thanks but it's not that first user ID is 1000 then 1001 an so on.

---

### Post by geebrz on 2010-02-12
Hi Baz,

on the up side you're not alone.  I'm having exactly the same problem on my 9.10 (64bit) install, on the down side I've not managed to do anything about it.
Have you had a result since your last post?
I was suffering from a locked password file which I fixed yesterday,  I don't think it is related but then someone reading this may know better.

How do you check the users ID?  I want to make sure my users are all over 1000 as suggested.

---

### Post by Baz6359 on 2010-02-20
Not managed to get anywhere with it at all put up with it now, if you list all users in a terminal it will have the numbers next to them.

---

### Post by geebrz on 2010-02-21
OK,  I've listed my users in terminal and they all have IDs over 1000.
Looks like the same issue,  no solution as yet...

---

