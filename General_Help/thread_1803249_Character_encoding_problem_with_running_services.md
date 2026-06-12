---
title: "Character encoding problem with running services"
date: 2011-07-13
forum: General Help
---

### Post by haujobb on 2011-07-13
Hi all,

I'm on a reasonably fresh install of 11.04 (2.6.38-8) which I'm in the process of setting up and I've run into a strange problem with character encodings which I don't understand.

I'm trying to run a service and it starts with no problem. The thing is that when I start it with 'sudo service myservice start', the program cannot read special characters like åäö. But if I start it as a program from the command line in gnome everything works like its supposed to.

I've also noticed that when I ssh to the machine I cannot read or write special characters, but with the terminal in gnome it works. I don't know if this is related to my problem but I suppose that it can be.

The output of locale in ssh gives:
LANG=
LANGUAGE=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=

in gnome they all read en_US.UTF-8.

I've tried to set the LANG variable with 'sudo update-locale LANG=en_US.UTF-8' but that didn't seem to have any effect.

Grateful for any help.

Regards,

---

