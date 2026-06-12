---
title: "HELP!! I broke /etc/sudoers"
date: 2006-04-05
forum: General Help
---

### Post by adam.mech09 on 2006-04-05
Hi

I NEED HELP! I was modifying /etc/sudoers to allow me to start firestarter at bootup, and i forgot to make a backup (and i'm usually perfect about making backups.  I was following a thread and i copied and pasted two lines into the end of the file when i should have pasted only one.  

the pasted lines were

File:/etc/sudoers

username:something somethign somethign.....it;s the second last line that is the problem.  Now i cant use anything that would require sudo or root access

I cant even view the file, as an error occurs when i try "cat /etc/sudoers"

Can anybody help me??

I'm not even sure how to edit things if i can get a copy of a clean /etc/sudoers file, as i cant do anything involving sudo or root...

Thanks

---

### Post by aysiu on 2006-04-05
Boot into recovery mode.

---

### Post by Mustard on 2006-04-05
HowToEditSudoersCreated Sunday 26/03/2006 09:48

Use the **Recovery Mode** from the **Grub menu** at startup.

Recovery mode will drop you to a root prompt.  If you don't see the GRUB menu at startup then you probably have to press the ESC key to view it, as its sometimes hidden and only revealed when you hit the ESC key.

Once at the root prompt you can use this command to edit the /etc/sudoers file..

```
visudo  #this command does on thing.  It opens the sudoers file for editing
```

My sudoers file looks like this.  Note the last line where I give my user sudo privileges.  This is the line that would need to be added by those who, for whatever reason, don't have sudo privileges.

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

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
mustard ALL=(ALL) ALL

```

You can see my username on the bottom line.  You would need to add your username to the bottom as I have done.

Assuming your user name was "bob'', then the line that would need to be added would be..
```
bob ALL=(ALL) ALL
```

This is just one way of doing it.  Some sudoers files are set up with an admin group called 'adm'.  Users are then added to the adm group, and a line in the sudoers file that looks like this below gives members of the 'adm' group admin access.
```
%adm ALL=(ALL) ALL
```

If you decided to do it this way you would create the line above at the bottom of your sudoers file then do this command (substituting your username in the appropriate place)..

```
adduser your_username adm
```

---

### Post by phil66 on 2006-04-05
visudo returned a usage format when I tried this.
I used nano editor to make correction in /etc/sudoers and /etc/sudoers.tmp
This brought my sudo back to life

---

### Post by adam.mech09 on 2006-04-05
Perfect.  Thanks so much for the help.  Worked perfectly.

Just realised there are a couple other threads dealing with the same issue, sorry about a repost.

-Adam

---

### Post by DavidTangye on 2006-04-05
:-#

---

