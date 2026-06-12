---
title: "sudo access lost and regained"
date: 2010-06-19
forum: General Help
---

### Post by 5circles on 2010-06-19
I don't know how it happened, but I lost access to sudo on one of my systems.  I'm using this old system with only 512M memory as an interim while I rebuild my main system.  The secondary system was running really slowly so I thought it might be worth looking at services.  I tried to turn off a few services- Bluetooth, power management, and assistive technology - there may have been a couple more.  

When I rebooted and tried to run Synaptic (GUI, but I don't think that made a difference), I got the message that 'Ubuntu failed to run /usr/sbin/synaptic as user root'.  I'd never seen this before.  I tried to sudo and then got the message that 'user is not in the sudoers file'.  Then I discovered that my user wasn't in the admin group any more.

Thanks to messages in the forums, I was able to reboot into recovery mode and use usermod to restore membership the admin group.  And then to use synaptic again.  THANKS!

It turned out that I'd lost access to all groups except my own and www-data, so I restored that.

But I'm curious as to why this happened.  Does anyone have any ideas that might help others - or me from preventing a recurrence?

Thanks
Mike
PS - this happened on 10.04

---

### Post by sisco311 on 2010-06-20
In my experience the most common cause is the inappropriate usage of the usermod command:

```
usermod -G group1[,group2...] user
```
adds the user to the list of groups and removes the user from any other group (expect the user's initial login group). You have to use the -a flag to add the user to the supplementary groups:
```
usermod -aG group1,[group2...] user
```

On a Debian based system you could use the adduser perl script to add a user to a supplementary group:
```
adduser user group
```

I prefer the gpasswd command which should work on most Linux systems:
```
gpasswd -a user group
```

Or if you understand the syntax of the /etc/group file, you can use:
```
vipw -g
```
to edit it manually.

---

### Post by 5circles on 2010-06-20
> **sisco311 said:**
> In my experience the most common cause is the inappropriate usage of the usermod command:

usermod was the solution for me, it should not have been the cause of the problem.  I'd used synaptic several times after the last reboot.  Then I just changed the startup services with bootup manager before trying synaptic again.

Thanks

---

### Post by jerome1232 on 2010-06-20
Perhaps some package you removed took your user out of some groups, without knowing exactly what you did all we can do is guess.

---

### Post by 5circles on 2010-06-20
> **jerome1232 said:**
> Perhaps some package you removed took your user out of some groups, without knowing exactly what you did all we can do is guess.

That's my guess too.   It seems odd, but that's the only explanation.  Still, I fixed it without too much panic, so that's a plus.

---

