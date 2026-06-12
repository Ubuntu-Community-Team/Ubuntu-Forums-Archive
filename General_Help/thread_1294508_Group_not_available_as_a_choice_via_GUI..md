---
title: "Group not available as a choice via GUI."
date: 2009-10-18
forum: General Help
---

### Post by Roasted on 2009-10-18
I know how to do this in terminal, but I couldn't help but to wonder why it didn't work in the GUI when you right click a folder and hit the permissions tab.

I created a bogus user called "user" to have as a generic samba account. I (jason) own the folder in question. I want the permissions to be 775 with jason:user owning the folder.

I can do this in terminal. But I tried to do it in the GUI real quick since I knew I owned the folder and I wouldn't need the root PW to do it. But when I hit the group list, there's no option for "user". I thought at first maybe it was because nobody was part of the generated "user" group.

So, I added the user "user" to the group "user." But even still, it's not an option.

Yet, "sambashare" is an available group, which has users assigned to it. I just don't know what's different from sambashare versus user, besides the fact user has 1 member and sambashare has 3 members.

What's up?

---

### Post by sisco311 on 2009-10-18
You have to add your user to the group, logout and log back in.

---

### Post by Roasted on 2009-10-18
> **sisco311 said:**
> You have to add your user to the group, logout and log back in.

I don't mean to ask a stupid question but I just have to clarify:

By logging out and back in, that's just to MY account "jason." Correct? There's no logging in/out that is required with user, is there?

EDIT - I just tried that. "user" is a member of the group "user" and I logged out (on my acct - jason) and back in. It's still not an option.

EDIT AGAIN - So I think I misunderstood. I added "jason" to the group "user", so therefore user + jason is a member of the group "user" and now it's an option and worked. Thanks!

---

### Post by sisco311 on 2009-10-18
> **Roasted said:**
> I don't mean to ask a stupid question but I just have to clarify:

By logging out and back in, that's just to MY account "jason." Correct? There's no logging in/out that is required with user, is there?

If you want to change the group of a file to the group "user" as user "jason", you have to add the user "jason" to the "user" group, log out "jason" and log back in.

EDIT: too late, you figured it out :)

---

### Post by Roasted on 2009-10-18
> **sisco311 said:**
> If you want to change the group of a file to the group "user" as user "jason", you have to add the user "jason" to the "user" group, log out "jason" and log back in.

EDIT: too late, you figured it out :)

Haha yeah, I got it :P. I had just always assumed that when you created a user, it automatically added them to the group. That was confusing when user itself couldn't access the stuff that the group "user" had access to. But if the user "user" isn't a member of the group "user" then it makes sense why that happened.

So, good tip. And I guess it's good security, that Linux will add the group for convenience, but adds no members to the group unless otherwise specified.

---

### Post by CharlesA on 2009-10-18
Stupid question, but how do you add an existing user to an additional group?

Example:

I want to add "user" to the "test" group, but user is already created and in the group "user."

From command-line please.. since I have issues with the GUI over SSH.

---

### Post by sisco311 on 2009-10-18
> **CharlesA said:**
> Stupid question, but how do you add an existing user to an additional group?

Example:

I want to add "user" to the "test" group, but user is already created and in the group "user."

From command-line please.. since I have issues with the GUI over SSH.
```
sudo adduser username group
```

---

### Post by CharlesA on 2009-10-19
Thanks, I guess I was using the wrong command since I used useradd -G group username.

---

