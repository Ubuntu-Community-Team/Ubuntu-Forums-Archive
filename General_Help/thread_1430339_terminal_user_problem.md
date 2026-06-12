---
title: "terminal user problem"
date: 2010-03-15
forum: General Help
---

### Post by tommichlik on 2010-03-15
I am using the latest UBUNTU 9.10. It was working great. I logged in as Tom, put in my password and could do what I needed to do. Now when I go to the CLI through the terminal I get "Tom@new-host-2:~$ " which has no privileges. I obviously messed up something. I can't find a way to get back to my original prompt when I access the terminal.

Thanks Tom

---

### Post by Ryan Dwyer on 2010-03-15
That's the prompt you're supposed to get. Everything you do runs as a standard user unless you run sudo before the command. When you do that, you get granted temporary admin rights to do the task.

---

### Post by MelDJ on 2010-03-15
a user in linux doesn't have admin privileges. 
you must login as root to use admin priveleges by typing

```
su
```

followed by your password in terminal

---

### Post by cdenley on 2010-03-15
> **MelDJ said:**
> a user in linux doesn't have admin privileges. 
you must login as root to use admin priveleges by typing

```
su
```

followed by your password in terminal

This is incorrect for ubuntu. The correct command is "sudo -i" if you want to get a root shell. Otherwise, "sudo somecommand" to run a single command. The "su" command prompts for the root password, which should not exist.

---

### Post by slakkie on 2010-03-15
It is not correct for a default Ubuntu install, but I can run su without problems.

@OP, google for rootsudo ubuntu and have a read :)

---

### Post by cdenley on 2010-03-15
> **slakkie said:**
> It is not correct for a default Ubuntu install, but I can run su without problems.


Yes, but that is clearly not the solution to this thread since the original poster never mentioned setting a root password, setting a root password is strongly discouraged, and posting instructions for setting a root password is not allowed on this forum.

---

