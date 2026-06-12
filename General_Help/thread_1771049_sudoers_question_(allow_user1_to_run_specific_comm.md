---
title: "sudoers question (allow user1 to run specific command as user2)"
date: 2011-05-30
forum: General Help
---

### Post by hwttdz on 2011-05-30
I would like a given user to be able to run a specified command as another user without a password, i.e.:
user1@machine > sudo -u user2 commandname
what do I need to drop in the sudoers file to make this work out?

user1 ALL=NOPASSWD: (user2) commandname

gives me a syntax error? After some experimenting it appears that the error is because I want to only allow specific arguments (i.e. I want to allow 'echo "hello"', but not 'echo "goodbye"').

Apparently if you need to specify arguments you need to specify a command alias (Cmnd_Alias), so now I have 

Cmnd_Alias VOLUME = /usr/bin/pacmd list-sinks
user1	ALL=(user2) NOPASSWD: VOLUME

And that seems to get the job done.

---

