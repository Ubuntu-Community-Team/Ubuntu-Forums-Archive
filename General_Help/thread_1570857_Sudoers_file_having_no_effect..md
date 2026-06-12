---
title: "Sudoers file having no effect."
date: 2010-09-08
forum: General Help
---

### Post by pspkiller91 on 2010-09-08
I'm trying to set up a script to start various programs and perform various operations when an Ubuntu box I'm using starts up. The script (/usr/bin/customboot) is set to run at logon by adding it to the Startup Applications dialog. The box is used as a file server that's started up with Wake-on-LAN and then auto logs in to my account (let's call it dave) for various reasons. The main reason being that VNC won't work unless a user is logged in. I know it's not the most elegant solution but it's worked pretty well in the past. Security isn't a huge issue.

Here is the script itself:

```

#!/bin/sh
#
# Description: Used to run commands upon bootup.
#

#Starts Samba server because it won't start on it's own for some reason.

service smbd start

#Enables the system speaker as its disabled by default, beeps it 3 times to indicate that the system is ready, then disables it once more to minimise annoying beeps.

modprobe pcspkr
beep -f 750 -r 3 -d 50 -l 75
rmmod pcspkr

#Locks the screen as a rudimentary security feature.
gnome-screensaver-command -l

exit 0

```It works to an extent. All of the commands that need to be run as root don't work, leaving gnome-screensaver-command -l as the only working command. I've chowned the script to root and chmodded it to 4755 but to no avail. I then added my account, dave to the sudoers file allowing myself to run the script without needing to enter a password. No dice. So I took the ham fisted approach and allowed myself to run anything without a passowrd. Still no dice.

Here's my sudoers file:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
%rob    ALL=NOPASSWD: ALL



# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


```What on Earth is going on? I'm beginning to wonder if there are deeper problems here seeing as Samba won't start on it's own for some reason. I've heard that there's possibly a bug that causes problems with Ubuntu 10.04 but I can't get a definative answer.

Plese someone help. I've been trying to work this one out for days.

---

### Post by bodhi.zazen on 2010-09-08
%rob conflicts with %admin

comment out the %admin line.

---

### Post by pspkiller91 on 2010-09-08
> **bodhi.zazen said:**
> %rob conflicts with %admin

comment out the %admin line.

Damn you're a whole lot more observant than me. Not only did I miss that but I forgot to change my real name to my pseudonym dave. Oh well. Now the whole world knows who I am resulting in the emptying of my bank account and racking up of huge debts in my name.

Thanks. I'll give it a go now.

---

### Post by pspkiller91 on 2010-09-08
Right. Just tried the above and it worked a charm. Now to close the gaping security hole I've just made. I know I said that security isn't an issue but it's good to be careful.

Am I right in thinking that by adding 

```

rob     ALL=NOPASSWD: /bin/sh, /sbin/modprobe, /sbin/rmmod, /usr/bin/service

```

as opposed to the simple yet functional

```

rob    ALL=NOPASSWD: ALL

```

will enable only the listed commands to be run without a passowrd?

---

### Post by bodhi.zazen on 2010-09-08
> **pspkiller91 said:**
> Right. Just tried the above and it worked a charm. Now to close the gaping security hole I've just made. I know I said that security isn't an issue but it's good to be careful.

Am I right in thinking that by adding 

```

rob     ALL=NOPASSWD: /bin/sh, /sbin/modprobe, /sbin/rmmod, /usr/bin/service

```as opposed to the simple yet functional

```

rob    ALL=NOPASSWD: ALL

```will enable only the listed commands to be run without a passowrd?

yes, but it will disable all other commands.

---

### Post by pspkiller91 on 2010-09-08
> **bodhi.zazen said:**
> yes, but it will disable all other commands.

That's what I want. I only want the commands in the script to be able to run without a passowrd. I'm thinking now that I could go one step further and define what each individual command is allowed to do to tighten security even further. I'll test it first in its current configuration then have a go at that.

Thanks for your help!

---

