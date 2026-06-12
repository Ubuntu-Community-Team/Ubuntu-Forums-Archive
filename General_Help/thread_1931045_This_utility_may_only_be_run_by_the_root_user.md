---
title: "This utility may only be run by the root user"
date: 2012-02-24
forum: General Help
---

### Post by netopalis45 on 2012-02-24
I have been trying to set up pm-hibernate to run without having to use sudo. I have seen several ways of doing this and none of them have worked. The one that showed up most often was to use "sudo visudo" and add the line "username ALL=NOPASSWD: /usr/sbin/pm-hibernate" so I tried it but it doesn't work at all. Any other way of doing this?
The main reason I want this to work is so I can send it as an ssh command to my server.

---

### Post by azmyth on 2012-02-24
Did you put this as the _very last line_ of the sudoers file when you did the sudo visudo?

username ALL=NOPASSWD: /usr/sbin/pm-hibernate

Also, you will still have to run the command as

sudo pm-hibernate

It just won't ask for a password.

---

### Post by netopalis45 on 2012-02-24
It is at the bottom of the file. I didn't try just using sudo without a password. I would like to use it without sudo at all because ssh doesn't like to send a sudo command.

---

### Post by azmyth on 2012-02-24
Editing the sudoers file won't help you since you still need to do sudo before the command.

Maybe you can add your user's user group (usually the username) to the group permissions of the pm-hibernate executable. I've never tried it though.

---

