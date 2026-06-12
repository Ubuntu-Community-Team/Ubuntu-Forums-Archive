---
title: "Sudo on breezy server installation"
date: 2006-03-04
forum: General Help
---

### Post by mario.rimann on 2006-03-04
Hi all.
I've done a clean server install of breezy. Everything worked fine. Then I installed "openssh-server" for remote controlling. I can connect from remote.

The problem is the sudo command: I could do a "sudo apt-get update" and "... upgrade" from remote. But since then, the sudo command is not working.

If I enter "sudo <any_command>" it asks for a password and get's back to the command shell. The command that should be executed will not be executed at all.

I also had this on my notebook - there a reboot solved the problem. But on the server this doesn't help at all!

Any hint on this?

BTW: I'm not able to start in recovery mode - the server has no keyboard/screen attached at the moment.

---

### Post by knalle on 2006-03-04
when sudo ask for a password type in your user account password

you can also edit the sudo list with **sudo visudo** or log in as root and do **visudo**

---

