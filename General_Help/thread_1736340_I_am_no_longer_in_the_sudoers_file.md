---
title: "I am no longer in the sudoers file"
date: 2011-04-22
forum: General Help
---

### Post by v0idnull on 2011-04-22
I don't know why, but within the past 48 hours, something happened that caused my main account to not access to sudo.

I noticed the problem when trying to update through the update manager ui and it complained that my root password was incorrect, even thought I could do sudo su in terminal and run apt-get upgrade through there.

I did some googling, and some people had this problem and they ended up adding their user name directly into the sudoers file and said that fixed it.

But I just want to report that what I noticed was that my main account was no longer part of the admin group. In fact, /etc/group had been changed, and a backup file was made at /etc/group-

restoring the group- file to group and now everything works again. I have no idea what caused this change, but it had to have happened within the past 2 days.

Just a heads up...

---

### Post by v0idnull on 2011-04-25
Yeah I'm bumping this.

It's no longer solved as it happened again in the past 12 hours. The group file was changed to something vanilla,a  backup made to /etc/group- . I have no idea what's do this or how to figure out who is doing it.

Any advice?

---

