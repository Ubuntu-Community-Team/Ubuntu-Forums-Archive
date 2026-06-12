---
title: "Root password problem"
date: 2006-04-17
forum: General Help
---

### Post by MvW on 2006-04-17
I supplied a root password during install, and this works fine in the terminal. However, any access via gnome that requires some password fails, with error messages looking like this:

Failed to run gdmsetup as user root: Wrong password.

This happens for system admin functions, update manager, etc.

I logged in as a normal user at the startup screen. Logging in as root at that point does not work. (I entered 'root' for user, then the pass)

---

### Post by nanotube on 2006-04-17
when it asks you for your password to run stuff as root, try typing in your user password, instead of the root password?

also, try checking if your username is properly listed in /etc/sudoers. if not, add it with command "visudo" while logged in as root.

---

### Post by MvW on 2006-04-17
[QUOTE=nanotube]when it asks you for your password to run stuff as root, try typing in your user password, instead of the root password?

also, try checking if your username is properly listed in /etc/sudoers. if not, add it with command "visudo" while logged in as root.[/QUOTE]

User password does not work.
No info specific to me seems to be listed in /etc/sudoers.

Where can I see what that file should look like?

---

### Post by hegenious on 2006-04-17
> I supplied a root password during install, and this works fine in the terminal. However, any access via gnome that requires some password fails, with error messages looking like this:


ubuntu does **not** ask you for a root password during install, I wonder where did you get that idea from?
Ubuntu keeps the root password hidden from you and wants you to use sudo instead. It was designed around the concept that you do not log in as root.

If you can become root in a terminal, it then should be enough to run passwd.
You can provide a new UNIX password for root and you won't be asked for the 'old' password. I must stress that this is not a good idea, security wise.

Lots of programs in ubu require you to use sudo, gksudo or kdesu and once installed by root won't run for the 'normal user' which in return forces you to login as root again. kinda catch22, isnt't it  ](*,)

---

### Post by MvW on 2006-04-17
[QUOTE=hegenious]ubuntu does **not** ask you for a root password during install, I wonder where did you get that idea from?
Ubuntu keeps the root password hidden from you and wants you to use sudo instead. It was designed around the concept that you do not log in as root.

If you can become root in a terminal, it then should be enough to run passwd.
You can provide a new UNIX password for root and you won't be asked for the 'old' password. I must stress that this is not a good idea, security wise.

Lots of programs in ubu require you to use sudo, gksudo or kdesu and once installed by root won't run for the 'normal user' which in return forces you to login as root again. kinda catch22, isnt't it  ](*,)[/QUOTE]

I ran the expert install in order to get my partitions the way I wanted it.  During that procedure I was clearly asked for the root password, and later for the user stuff.

I did change the root password with passwd before my initial post.  No difference.

It must be some real basic issue that can prevent me from even accessing the clock in the GUI sys admin, but at the same time I'm allowed to change my root password in the terminal.  Frustrated.

---

### Post by hegenious on 2006-04-17
> User password does not work.
No info specific to me seems to be listed in /etc/sudoers.

Where can I see what that file should look like?


here's mine, unedited:

> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL


Mine is default but this file is highly customizable, do 'man sudoers' for exact syntax.

---

### Post by MvW on 2006-04-17
Thanks for the efforts, but the problem was solved with this thread, particularly codejunkie's input:
[http://www.ubuntuforums.org/showthread.php?t=146859]("http://www.ubuntuforums.org/showthread.php?t=146859")

Mine was a particular problem someone doing an expert install may encounter.

---

