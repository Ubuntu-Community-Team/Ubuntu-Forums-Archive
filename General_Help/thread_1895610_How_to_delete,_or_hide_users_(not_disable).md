---
title: "How to delete, or hide users (not disable)"
date: 2011-12-15
forum: General Help
---

### Post by barnabas02 on 2011-12-15
Hello, I have created a test user in Ubuntu 11.10, and now, I want to delete, or hide it, because I don't want to see it on the login screen.
I have administrator privileges, and all of permissions to users.

---

### Post by Lars Noodén on 2011-12-15
You can use [deluser](http://manpages.ubuntu.com/manpages/oneiric/en/man8/deluser.8.html).

```

sudo deluser *foobar*

```

Or in Unity, go to System Settings->User Accounts

---

### Post by drmrgd on 2011-12-15
I think that solution will actually delete the users from the system, though, and that may not be what the OP is looking to do.  I think there is a way to change the users list in the gconf editor.  Doing a quick Google search turned up [this tutorial]("http://ubuntu-tutorials.com/2010/07/03/disable-login-screen-user-list-ubuntu/").

---

### Post by barnabas02 on 2011-12-16
The delete is good too thanks, I can try it in the evening, or tomorrow.
I will send feedback. Thank you again.

---

### Post by barnabas02 on 2011-12-16
Works perfectly thank you very moch.

---

