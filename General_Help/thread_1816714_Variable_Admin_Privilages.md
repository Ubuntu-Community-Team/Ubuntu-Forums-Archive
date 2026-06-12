---
title: "Variable Admin Privilages"
date: 2011-08-02
forum: General Help
---

### Post by tomwjrat on 2011-08-02
Hello, i am wondering if there is a way you can limit a users right to using the terminal and still be able to install apps from the software center?

or remove their ability to do one specific task through the terminal?

i have tried to remove certain users from groups under User Accounts. but to no avail. 

Many thanks! :)

---

### Post by SeijiSensei on 2011-08-02
> **tomwjrat said:**
> Hello, i am wondering if there is a way you can limit a users right to using the terminal and still be able to install apps from the software center?

Only administrative (root) users can install software.

> or remove their ability to do one specific task through the terminal?

If you mean, you'd like to be able to put some users into a group that cannot execute a particular application, yes, that's possible.  Actually the solution is to do things the other way around.

Create a new group ("newgroup" below) and add the users who are *permitted* to run the restricted application into that group.  Next locate the application you want to restrict and change its permissions as follows:

```

chown root.newgroup /usr/bin/someapp
chmod 0754 /usr/bin/someapp
```

Now root and the members of "newgroup" can run the application, but no one else can.  You can also make the application entirely invisible to non-members by changing the permissions to 0750 instead of 0754.

---

### Post by tomwjrat on 2011-10-07
Thank you for your reply
i had no idea that i had a reply, so sorry about not thanking you sooner!
I will test it out when i can but the person has moved on to uni now.
Thanks!

---

