---
title: "trouble with .bash_aliases"
date: 2009-11-04
forum: General Help
---

### Post by jbrown96 on 2009-11-04
I'm trying to up my Linux-fu, but I'm having some difficulty. I have added some aliases to .bashrc before, but I want to do it right this time, so I want to create a .bash_aliases file. Here's my .bash_aliases > alias upgrade='sudo apt-get update && sudo apt-get upgrade'
alias off='sleep 2 && xset dpms force off'
alias ssh-turing='ssh [email]jbrown96@host[/email]'
alias emacs='emacs -nw'
alias install='sudo apt-get install'
alias save-power='sudo echo min_power > /sys/class/scsi_host/host0/link_power_management_policy && sudo echo 12000 > /proc/sys/vm/dirty_writeback_centisecs && sudo hal-disable-polling --device /dev/cdrom && sudo echo 5 > /proc/sys/vm/laptop_mode'


if [ -f ~/.bash_aliases ]; then
   . ~/.bash_aliases
fi
[/QUOTE]
to > if [ -f ~/.bash_aliases ]; then
    ~/.bash_aliases
fi

Now the file is being read, but I get > bash: /home/justin/.bash_aliases: Permission denied
 when bash is first opened. There don't appear to be any problems with the permissions -- they are the same as .bashrc. > -rw-r--r-- 1 justin justin  458 2009-11-04 14:31 .bash_aliases
-rw-r--r-- 1 justin justin  457 2009-11-04 14:28 .bash_aliases~
-rw------- 1 justin justin 2753 2009-11-04 14:34 .bash_history
-rw-r--r-- 1 justin justin  220 2009-10-12 19:52 .bash_logout
-rw-r--r-- 1 justin justin 3178 2009-11-04 14:34 .bashrc
-rw-r--r-- 1 justin justin 3180 2009-10-12 19:52 .bashrc~


Does anyone know the problem? Thanks.

Update: Not sure why it didn't work the first time, but I reverted the changes to .bashrc, and it works now. I also don't need any special permissions to it (just rw-rw----).

---

### Post by hwttdz on 2009-11-04
You're attempting to execute the file and it's not an executable file.  There are a few options, one add a shebang to the top (#!/bin/bash) and change the permissions so it's executable and execute the file.  Two source the file ( ". ~/.bash_aliases" or "source ~/.bash_aliases").  I think sourcing it would be convention.  By the way this is a great idea, I'm moving my aliases to a separate file.

---

### Post by redmk2 on 2009-11-04
> **hwttdz said:**
> You're attempting to execute the file and it's not an executable file.  There are a few options, one add a shebang to the top (#!/bin/bash) and change the permissions so it's executable and execute the file.  Two source the file ( ". ~/.bash_aliases" or "source ~/.bash_aliases").  I think sourcing it would be convention.  By the way this is a great idea, I'm moving my aliases to a separate file.

Sourcing the file is the correct way to do it.  No shbang and eXecute perms needed.  Obviously you can use any name for the file (i.e. *.aliases* will work too.)

---

### Post by hwttdz on 2009-11-04
Yeah, I suppose I should have put those in the opposite order.

---

### Post by redmk2 on 2009-11-04
> **hwttdz said:**
> Yeah, I suppose I should have put those in the opposite order.

Another thought -- when you source the file it is only when you FIRST open the shell (CLI) or you explicitly call: "source file" at the CLI.  I bet the OP did not close and reopen the terminal.

---

