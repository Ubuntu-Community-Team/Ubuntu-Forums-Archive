---
title: "Accidentally changed CHGRP on my user account, now can't sudo. Any hope?"
date: 2010-03-10
forum: General Help
---

### Post by supergrover1981 on 2010-03-10
Hi folks,

I was recently messing around learning chgrp commands, and set my (only) user account to a different group. Now whenever I try to sudo a command, I get

'john is not in the sudoers file. This incident will be reported' message.

I *seem* to have a root account (one is listed in System->admin->users and groups), but I'm almost certain that the password for it would be one of 3 things, and it's none of them.

Any suggestions? Am I doomed to a complete reinstall or is there something else I can do?

Cheers,
        - SuperGrover

---

### Post by ciscosurfer on 2010-03-10
I believe you'll find this page helpful at solving your issue:

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by supergrover1981 on 2010-03-10
Hi folks,

Sorry - I explained this a little poorly. All fixed now, but in case anyone stumbled onto a similar thing:

The problem: I usermodded my only account to another chgrp, but forgot to add the --append switch, which means my (only) user account no longer had the ability to run sudo commands

The solution: Reboot the machine, press 'e' to jump into edit mode in the grub screen, append 'single' to the end of the kernel loadup. This should give the option of logging into root, even if this option is disabled on your ubuntu install. Once logged in as root, run the line "adduser [username] admin", then reboot. You should have sudo access once more. (Note: you probably want to add your user account to a bunch of other groups as well - eg cdrom, sambashare, etc)

---

