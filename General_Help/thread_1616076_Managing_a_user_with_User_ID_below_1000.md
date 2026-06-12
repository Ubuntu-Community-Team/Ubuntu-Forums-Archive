---
title: "Managing a user with User ID below 1000"
date: 2010-11-07
forum: General Help
---

### Post by rasfl3 on 2010-11-07
Hello. I set a User's ID below 1000 because I did not want it to show in the login screen as an option and the Other User option would have to be used. I can login into that account using the Other User option, although, when I go to Users and Groups, the account doesn't show up there. How can I get it to show up there or how can I manage this user account. Thanks in advanced!

---

### Post by blueridgedog on 2010-11-07
User ids below 1000 are system ids and therefore don't show up in the standard user tools.  You will need to manage it using command line tools and/or editing user and group files directly.  If you share what you want to do with the account, I can suggest a tool or a process.

---

### Post by rasfl3 on 2010-12-07
I lowered the User ID below 1000 purposely so it wouldn't show up in the login screen and I'd have to use Other User and type in the Username. If I needed to, how could I change it's ID to be over 1000? Thanks and sorry for the late response!

---

### Post by sisco311 on 2010-12-07
You can use the **usermod** command.

From **man usermod**:
>       -u, --uid UID
           The new numerical value of the users ID.

           This value must be unique, unless the -o option is used. The value
           must be non-negative. Values between 0 and 999 are typically
           reserved for system accounts.

           The users mailbox, and any files which the user owns and which are
           located in the users home directory will have the file user ID
           changed automatically.

           [b]The ownership of files outside of the users home directory must be
           fixed manually.[/b]


If you want to hide a user from GDM's user list, then check out [thread=1576883]this[/thread] thread.

---

### Post by rasfl3 on 2010-12-12
Thanks! I appreciate it. I will give this a try.

---

