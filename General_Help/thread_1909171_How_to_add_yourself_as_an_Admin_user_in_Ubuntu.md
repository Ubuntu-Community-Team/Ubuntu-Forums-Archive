---
title: "How to add yourself as an Admin user in Ubuntu"
date: 2012-01-14
forum: General Help
---

### Post by chad.a.byrd on 2012-01-14
I have a Sony Vaio laptop running Ubuntu 11.10.  Enjoyed my experience so far, but I've run into a small but persistent problem.  I downloaded Spotify, and when I tried to install it, a window popped up telling me I couldn't install this program as an Administrator.  I needed to install it as a regular user.  

So...I went to my User Accounts settings and changed my account from Admin to Standard (I'm guessing this was a BAD idea).  Now, whenever I try to connect to a new wifi network, like at school, a window pops up saying that authentication from a Super User is required, and asks for a root password.  I tried to use my account password, but to no effect.  The same thing happens when I try to install updates.

What do I need to do to change my user privileges?

---

### Post by Dangertux on 2012-01-14
> **chad.a.byrd said:**
> I have a Sony Vaio laptop running Ubuntu 11.10.  Enjoyed my experience so far, but I've run into a small but persistent problem.  I downloaded Spotify, and when I tried to install it, a window popped up telling me I couldn't install this program as an Administrator.  I needed to install it as a regular user.  

So...I went to my User Accounts settings and changed my account from Admin to Standard (I'm guessing this was a BAD idea).  Now, whenever I try to connect to a new wifi network, like at school, a window pops up saying that authentication from a Super User is required, and asks for a root password.  I tried to use my account password, but to no effect.  The same thing happens when I try to install updates.
to
What do I need to do to change my user privileges?

You need to boot to recovery mode, drop to the root shell and add yourself back to the admin group.

by doing the following

```

usermod -a -G admin username

```Once you do this you should be able to sudo again.

Hope this helps.

---

### Post by chad.a.byrd on 2012-01-14
> **Dangertux said:**
> You need to boot to recovery mode, drop to the root shell and add yourself back to the admins group.

by doing the following

```

usermod -a -G admins username

```Once you do this you should be able to sudo again.

Hope this helps.

I booted into Recovery Mode.  Entered the command above.  The next command stated that the group "admins" does not exist...:confused:

---

### Post by Dangertux on 2012-01-14
Yeah sorry I typoed, you will notice the above post was edited by me a few minutes ago.

It should be admin not admins.

Sorry for the confusion.

---

### Post by chad.a.byrd on 2012-01-14
That worked!  Thanks so much!

---

