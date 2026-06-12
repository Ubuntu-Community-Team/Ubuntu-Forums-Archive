---
title: "Can sudoers sudo in their crontabs? - How?"
date: 2009-07-14
forum: General Help
---

### Post by HotForLinux on 2009-07-14
If I'm a sudoer, is there a way I can execute a command (for which I'm allowed to sudo) under sudo directly in my crontab or indirectly in a script used in my crontab?

For example:
How can a ntpdate sudoer crontab an execution of ntpdate?

---

### Post by csabo2 on 2009-07-14
here you go :) 2nd post.  (note: I know the URL says macosx, read it anyway)

[http://macosx.com/forums/archive/t-284877.html](http://macosx.com/forums/archive/t-284877.html)

---

### Post by HotForLinux on 2009-07-14
OK, thanks!
Yesterday, I browsed for a solution and only found alternatives that implied giving the sudoer for a particular command much more administrative power. So I decided to ask in a more concise way.

It seems then that the 'narrowest' solution passes through the administrator removing the need for password when the mentioned sudoer issues that particular command.

So the administrator needs to visudo and add a line like:

user localhost=(root) NOPASSWD: /...path_to.../command options&parameters_list

right?

---

### Post by HotForLinux on 2009-07-14
I addedd that line to the sudoers config file.
The sudo command is in a script executed without sudo in the crontab.
But I still see in the logs that the password is requested and also, in the command line.

Does one need to reboot in order to make effective the changes in the sudoers file?

---

### Post by HotForLinux on 2009-07-15
I have tried one by one the following lines in the sudoers file (using tortuous ***visudo***) but nothing changes, except that the command **sudo -l** doesn't ask the user a passwd (only for some of them).


user localhost=(root) NOPASSWD: /usr/sbin/ntpdate
user 127.0.0.1=(root) NOPASSWD: /usr/sbin/ntpdate
user 127.0.0.1=(root) NOPASSWD: /usr/sbin/ntpdate
user ALL=(root) NOPASSWD: /usr/sbin/ntpdate
user ALL=(root) NOPASSWD: /usr/sbin/ntpdate ntp.ubuntu.com

The command executed from the command line continues to ask for 'sudo' and when sudo is prefixed continues to ask for a passwd.

Do you know what else needs to be changed?

---

### Post by Locutus_of_Borg on 2009-07-15
your syntax is wrong

```

user ALL=(ALL) NOPASSWD: /bin/bash

```

change "user" to the user's login name, and "/bin/bash" to the command in question

---

### Post by HotForLinux on 2009-07-16
No, the syntax was right, at least in some cases:

```
user ALL=(root) NOPASSWD: /usr/sbin/ntpdate
```is working. **The problem was the _order_ of the lines in the privileges specifications.**

The previous line _has to be_ after this one:

```
%admin ALL=(ALL) ALL
```I think that's because the second line one overrides the "*NOPASSWD" tag* of first one if *the user "[COLOR=Navy]user[/COLOR]"* belongs to the [COLOR=Navy]*"admin"*[/COLOR] group

I made it clear that I wanted to give the minimum privileges possible.

What is not working is the syntax that specifies from what host:

```
user 127.0.0.1=(root) NOPASSWD: /usr/sbin/ntpdate
[COLOR=Gray]or[/COLOR]
user 127.0.0.0/16=(root) NOPASSWD: /usr/sbin/ntpdate
[COLOR=Gray]or[/COLOR]
user  localhost=(root) NOPASSWD: /usr/sbin/ntpdate
```I still don't know why

---

### Post by HotForLinux on 2009-07-22
OK this issue is almost solved but there's still another different problem for which I opened another thread:

[Strange behaviour: CRON requires having logged in to do sudo commands]("http://ubuntuforums.org/showthread.php?t=1215506")

---

