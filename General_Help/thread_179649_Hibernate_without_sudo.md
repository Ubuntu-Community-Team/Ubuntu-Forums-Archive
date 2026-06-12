---
title: "Hibernate without sudo?"
date: 2006-05-20
forum: General Help
---

### Post by Erik Trybom on 2006-05-20
Hello everyone, 

I use a laptop, and often run it on batteries only. Sometimes I forget it for a while, go to lunch or something, and loose all my data when the battery dies. So far I haven't lost anything important but I guess it's only a matter of time before I do.

Therefore, I was thinking about making it hibernate when it reaches critical power status. Hibernation works using "sudo /etc/acpi/hibernate.sh". I suppose I could tell the battery monitor application to run that command when it reaches critical status, but it would only ask for a password and then die anyway since I'm not there to type it.

Do you think it's possible to run that command without sudo? I'm running Xubuntu Breezy right now if it makes any difference.

---

### Post by Ramses de Norre on 2006-05-20
sudo gedit /etc/sudoers
add line ```
username ALL= NOPASSWD: /etc/acpi/hibernate.sh

```

And replace username by our own. Running the command won't ask your password nomore then.

---

### Post by Erik Trybom on 2006-05-25
Thanks a lot for answering, but strangely it didn't work. It still asks for password when running the command.

Here's my /etc/sudoers file:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL
erik ALL = NOPASSWD: /etc/acpi/hibernate.sh

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL

```

Have I done something wrong?

---

### Post by Lomz on 2006-05-25
Tried installing the Gnome-Power-Manager?

---

