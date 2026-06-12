---
title: "Create an user with limited access"
date: 2010-10-24
forum: General Help
---

### Post by karthick87 on 2010-10-24
I want to create a limited user,such that the user should only have the access to usb drives,cd drives and internet.And also i want to restrict the user from deleting the files from the system..How to do it..?

---

### Post by slush1000 on 2010-10-24
You might want to look into the gdm-guest-session package.

In the Software Centre it says:
> This package adds support for starting a guest session through gdm's flexiserver, which any already logged in user can launch.

It creates a temporary guest account with a temporary home directory and some restricted privileges (such as not being able to read any home directory or do any permanent change to the system).

I've never used it so I can't comment on it but it might be what you're looking for.

---

### Post by karthick87 on 2010-10-24
Any other way..?

---

### Post by karthick87 on 2010-10-25
Bump..!

---

### Post by nynepac on 2010-10-25
It sounds like a decent solution but can anyone speak to whether or not it works as described?

---

### Post by karthick87 on 2010-10-26
Can anyone explain me on how to use it..?

---

