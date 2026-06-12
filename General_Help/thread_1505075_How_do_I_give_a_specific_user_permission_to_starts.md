---
title: "How do I give a specific user permission to start/stop a specific service?"
date: 2010-06-08
forum: General Help
---

### Post by TheForumTroll on 2010-06-08
As the topic says:
How do I give permission to a logged in user to stop/start a specific service without entering a root/sudo password?

So they can do a simple "service SomeService stop|start"


It is for a headless Ubuntu server.

---

### Post by Serpher on 2010-06-08
I'm not sure...but I have an inkling if you read up on visudo ('man visudo') you'd probably find what you're looking for.

---

### Post by davidmohammed on 2010-06-08
probably not a good idea to let all users access to root commands.

Suggest [this article]("http://www.cyberciti.biz/faq/use-sudo-or-sudoers-to-start-stop-restart-apache/") is something like what you want - effectively it gives certain users access to sudo but for specific services.

---

### Post by TheForumTroll on 2010-06-08
No, access to root services for everyone is defenitly NOT what I want :eek:

I'll try to clarify it a bit:
I want to allow a user to run a command that will stop/start a specific service. I do not want users to have access to anything else than that without using sudo as they normally would. I have had a look at the sudoers file already and it does look like the correct way but I'm not sure how to accomplish it and I might accidentally allow more than what I'm looking for without some guidance :)

---

### Post by TheForumTroll on 2010-06-08
It does seem that sudo is the correct way to accomplish what I want. I had a look at sudo's homepage and found some good examples.

I'll mark the thread as solved and post the answer if it works out :)

---

### Post by TheForumTroll on 2010-06-08
Okay i found a way :)

Edited the sudoers file ("sudo visudo") and added something like this:
```

USER        ALL = NOPASSWD: /usr/sbin/service ServiceName *

```

This will allow the user to run "sudo /usr/sbin/service ServiceName" with any or zero following attributes (ie. start|stop).
I also learned something new:

```

service ServiceName --full-restart

```

This will first run "service ServiceName stop" and then "service ServiceName start". Nice :)

---

