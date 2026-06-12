---
title: "restart service without root privileges"
date: 2012-01-14
forum: General Help
---

### Post by rama00 on 2012-01-14
I want a certain user to allow to restart a certain service, and only that particular service;

Normally I would do this myself with: 

sudo service "servicename" restart

However, this user has no sudo rights at the moment; what are my options to accomplish this ?

---

### Post by Karlchen on 2012-01-14
Hello, rama00.

You will have to add the user in question to the sudo configuration file. But do not allow him to run any command. Instead allow him to run only the commandline needed to restart the service, i.e. **sudo service "servicename" restart**
Check out whether 
[LIST]
[*]man sudo
[*]man 5 sudoers
[*]sudo cat /etc/sudoers
[/LIST]
 provide sufficient understandable pieces of information in order to achieve this task. Else, do not hesitate to ask.

Kind regards,
Karl

---

### Post by Lars Noodén on 2012-01-14
You can add something like the following to [sudoers](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sudoers.5.html)

```

%somegroup ALL=(ALL) /path/to/startup/script

```

Obviously, you'll want to substitute "somegroup" and "/path/to/startup/script" with the relevant values for your system.

---

### Post by Karlchen on 2012-01-15
Hello, rama00.

Let us try to translate Lars's instruction a little bit closer to your example:

[LIST]
[*]Let us assume that the unprivileged user is name "siggi", just because we do not know the name.
On Ubuntu each user will be a member of a group having the same name as the user himself, i.e. there is a group "siggi" having just one member, user "siggi"
[*]Let us assume that the service is named "DangerousService".
[*]The executable named "service" which we need to restart "DangerousService" is actually located in /usr/sbin, so the fully qualified name is /usr/sbin/service.
[*]Let us assume that you use the sudo standard installation and that the sudoers file is located in the folder /etc.
[*]We will add a line to the sudo config file which is /etc/sudoers.
 As the sudo manpages tell us we will use the command **sudo visudo -f /etc/sudoers** to do so. 
We have to prefix the "sudo" command which will prompt you to enter your password, because we need root privileges in order to modify the file "sudoers".
We will add this line: ```
%siggi ALL:(root) /usr/sbin/service "DangerousService" restart
``` Save the modified sudoers file and quitt. Unless visudo complains about an error in the line which you have just added, the job has been accomplished.
[*]Now, what does the line tell "sudo"?
**%siggi **members of the group "siggi", i.e. only user "siggi" in our case, may ...
**ALL** on all computers, but this is irrelevant because the entry only exists on this machine
**(root)** with root permissions
**/usr/sbin/service "DangerousService" restart** run exactly this one commandline, nothing else.
[*]So what does siggi have to do in order to restart the service "DangerousService"? - Run this commandline ```
sudo **service "DangerousService" restart**
```The shell will prompt siggi to enter his password. Once this has been done, the service will be restarted.
[/LIST]
Kind regards,
Karl

---

