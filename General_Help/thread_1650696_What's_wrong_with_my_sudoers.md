---
title: "What's wrong with my sudoers?"
date: 2010-12-22
forum: General Help
---

### Post by Alcap on 2010-12-22
Hey there,
I want to run to scripts with root privileges without being prompted for a password.
This is my sudoers
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
tiago   ALL=(ALL) NOPASSWD: /home/tiago/bin/SSID.sh
tiago   ALL=(ALL) NOPASSWD: /home/tiago/bin/desmontaDiscos.sh
# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```
I can't seem to find the error... Can anyone help me out? Every time I try to run SSID.sh it prompts me for the goddamn root password.

---

### Post by polki@mac.com on 2010-12-22
I think you have to put the command inside the script in the sudoers file.
I have a script that unmounts a Novell disk and then runs shutdown for me. So I put:

%admin ALL=NOPASSWD: /sbin/shutdown -h now

in my sudoers file. Works for me.

---

### Post by Jose Catre-Vandis on 2010-12-22
You still have to type "sudo" before the command, e.g.
```
sudo ~/bin/SSID.sh
```

---

### Post by Alcap on 2010-12-22
> **polki@mac.com said:**
> I think you have to put the command inside the script in the sudoers file.
I have a script that unmounts a Novell disk and then runs shutdown for me. So I put:

%admin ALL=NOPASSWD: /sbin/shutdown -h now

in my sudoers file. Works for me.
I think that gives everyone in the admin group permission to execute shutdown. I don't want that, and I've done this on other distros. I must be missing something quite obvious!

[quote="Jose Catre-Vandis"]
You still have to type "sudo" before the command, e.g.
```
sudo ~/bin/SSID.sh
```[/quote]

I know, I've done it;)

---

### Post by MooPi on 2010-12-22
Just a guess but what ever application you're trying to start should be added instead of the actual script.

---

### Post by Jose Catre-Vandis on 2010-12-22
> **MooPi said:**
> Just a guess but what ever application you're trying to start should be added instead of the actual script.

Good point, or maybe both !

---

### Post by negativ on 2010-12-22
This is not very helpful, but I whipped up a quick script to test, and it works fine for me.  It doesn't seem to be necessary to explicitly put your command in the sudoers, e.g. my script was:

```
#!/bin/bash
# this is test.sh
echo "Test!"
cfdisk /dev/sda
```

added:

myuser ALL=(ALL) NOPASSWD: /home/myuser/bin/test.sh

to sudoers

$ sudo ~/bin/test.sh

and it worked without asking for the password.

---

### Post by Alcap on 2010-12-29
Solved it! It was a PEBKAC...

---

### Post by Jose Catre-Vandis on 2010-12-30
Good of you to admit it ;) I have about three a day :D

---

