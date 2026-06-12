---
title: "sudoers line so I can shutdown the computer without a password?"
date: 2009-11-23
forum: General Help
---

### Post by josephellengar on 2009-11-23
Yeah.  Anybody know one?  I know it's dangerous to edit sudoers but this is driving me crazy, and I don't like the applet.  Thank you!

---

### Post by josephellengar on 2009-11-23
bump

---

### Post by mdurham on 2009-11-23
I'm just guessing but, as the applet can shut things down without a password there must be a way of doing it without a password. What is wrong with using the applet?
Cheers, Mike

---

### Post by spiderbatdad on 2009-11-23
i think what you are seeing has to do with user privileges...possibly due to non-admin account?

---

### Post by josephellengar on 2009-11-23
> **mdurham said:**
> I'm just guessing but, as the applet can shut things down without a password there must be a way of doing it without a password. What is wrong with using the applet?
Cheers, Mike

Yeah, it's to use the sudoers file, but I can't figure that out.  I don't like the applet because you have to click on it, and then click something in the middle of the screen.  You know, it's a little inconvenience.  I'd like to just have a button I can click once with the command in it, or the old fast user switcher applet back- you know, the one with the menu that let you restart, shutdown, log out, etc.

---

### Post by Spectre5 on 2009-11-23
See the section "Shutting Down From The Console Without A Password" here:
[https://help.ubuntu.com/community/Sudoers#Shutting%20Down%20From%20The%20Console%20Without%20A%20Password](https://help.ubuntu.com/community/Sudoers#Shutting%20Down%20From%20The%20Console%20Without%20A%20Password)

---

### Post by josephellengar on 2009-11-23
> **Spectre5 said:**
> See the section "Shutting Down From The Console Without A Password" here:
[https://help.ubuntu.com/community/Sudoers#Shutting%20Down%20From%20The%20Console%20Without%20A%20Password](https://help.ubuntu.com/community/Sudoers#Shutting%20Down%20From%20The%20Console%20Without%20A%20Password)

Thanks.  lol  I went to that page to research the sudoers file but didn't notice that section.

---

### Post by josephellengar on 2009-11-23
It's not working.  Here's what I have so far:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification
Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown, /sbin/halt, /sbin/reboot
# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

#I can shutdown the computer
ross ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS

```

---

### Post by Spectre5 on 2009-11-23
You're welcome. When you've gotten this to work and if your question is fully answer, please remember to mark the thread solved (at the top, click Thread Tools and mark as solved).  Thanks.

Oops - posted at the same time.  Perhaps you need to restart?  What command are you using to try to shutdown?

---

### Post by jacobs444 on 2009-11-23
under the root   ALL=ALL(ALL)
add:  username ALL=ALL(ALL)
if you want no password sudo then uncomment (remove the pound sign from
# %sudo ALL=NOPASSWD: ALL
and add yourself to the sudoers group. If the group doesn't exist then create it. 

remember that sudo can be dangerous so think before you act.

---

### Post by josephellengar on 2009-11-23
got it.  I didn't realize that I still had to type sudo even though i was in the sudoers file for that command.  I didn't want to turn off the password requirement entirely- just for the shutdown command.

---

