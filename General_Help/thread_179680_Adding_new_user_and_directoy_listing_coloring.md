---
title: "Adding new user and directoy listing coloring?"
date: 2006-05-20
forum: General Help
---

### Post by Jabran Asghar on 2006-05-20
Hi,

I can add a new user from command prompt using following command:

$ sudo useradd user1 -G adm,dialout,cdrom,floppy,audio,dip,video,plugdev,lpadmin,scanner,admin -s /bin/bash

I can login as that user into linux, but the environment is felt different, i.e. when I use "ls" command, the directory listing does not showup in different colors as it does when using the root user or the user that I created during the installation. 

How can I enable colored directory listing for users added  through command prompt.

Thanks for any pointers.

Jabran

---

### Post by Fass on 2006-05-20
Copy your ~/.bashrc to the new user's home. The ls command doesn't automatically give coloured output, it's done with a switch (read about it in its man page.) The .bashrc of the user you created during install probably has an alias set so that ls='ls --color=auto'.

Aliases are otherwise pretty useful. One I always add is rm='rm -i' making rm prompt me before deleting files, and cd..='cd ..' because I hate that space.

---

