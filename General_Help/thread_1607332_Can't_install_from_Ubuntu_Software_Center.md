---
title: "Can't install from Ubuntu Software Center"
date: 2010-10-27
forum: General Help
---

### Post by stat30fbliss on 2010-10-27
So I turned on my comp today and went to install a new app with Ubuntu Software Center and got a notification box saying:

**The package system is broken**

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

Under the details it says:

**libdesktop-agnostic-vfs-gio libdesktop-agnostic-cfg-gconf libdesktop-agnostic-fdo-glib**

When I ran the **apt-get install -f** in my terminal I received this response:
```
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

Any help?

---

### Post by efflandt on 2010-10-27
You generally need to precede commands that update or modify with **sudo** to do them as root.  So try: **sudo apt-get install -f**

And make sure that **nothing** else that installs packages is open at the time (like Synaptic, Software Center, Update Manager, etc.) because then it may still be locked.

---

### Post by TeoBigusGeekus on 2010-10-27
Try 
```
sudo apt-get install -f
```

---

### Post by sikander3786 on 2010-10-27
> **efflandt said:**
> You generally need to precede commands that update or modify with **sudo** to do them as root.  So try: **sudo apt-get install -f**

And make sure that **nothing** else that installs packages is open at the time (like Synaptic, Software Center, Update Manager, etc.) because then it may still be locked.
To the OP:

And I guess you haven't used **sudo** before. In that case, just to mention that password will not show up as any asterisks or characters in the terminal. Just type and hit Enter. That will do it ;-)

---

### Post by stat30fbliss on 2010-10-27
Ok, so I did the **sudo** command, and here is what my terminal read

```
rob@ubuntu:~$ sudo apt-get install -f
[sudo] password for rob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdesktop-agnostic-fdo-glib fortune-mod libdesktop-agnostic-vfs-gio
  libdesktop-agnostic-cfg-gconf librecode0 fortunes-min
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

My sotware center seems to be running just fine.  Thanks for the Newbie Help!  :)

---

