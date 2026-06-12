---
title: "Getting &quot;Authentication denied&quot; when trying to enter password to change to root"
date: 2011-02-21
forum: General Help
---

### Post by dderolph on 2011-02-21
I'm running Ubuntu 10.04LTS as a virtual machine using VMware Player. I want to use Terminal to use tar to install VMware Tools for VMware Player per instructions at [http://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html#wp1127214](http://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html#wp1127214).  When I open Terminal and attempt to change to root via "su -", I get an "Authentication denied" message.  How can I resolve that?

---

### Post by 3Miro on 2011-02-21
Ubuntu doesn't use root account. You have to use "sudo"

```
sudo some_command
```

then the command will run as root.

---

### Post by coolbeans777 on 2011-02-21
You cant login as root, but what you can do is sudo every command
Eg
Instead of

Su root
Blah
Blah

You can do

Sudo blah
Sudo blah

---

### Post by sikander3786 on 2011-02-21
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

For gaining temporary root access,

```
sudo -i
```

---

### Post by coolbeans777 on 2011-02-21
You cant login as root, but what you can do is sudo every command
Eg
Instead of

Su root
Blah
Blah

You can do

Sudo blah
Sudo blah

---

### Post by dderolph on 2011-02-21
OK, thanks for all the replies.  

Now, I have another problem.  I'll start another topic.

---

