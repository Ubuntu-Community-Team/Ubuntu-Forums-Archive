---
title: "Run script after domain user login"
date: 2011-05-21
forum: General Help
---

### Post by GNU/Linux_Rocks! on 2011-05-21
Hi everyone!

 Could any of you help me please? I'm trying to integrate my Ubuntu PC into an Active Directory domain using Samba, Kerberos and Winbind. The task I'm trying to accomplish now is to automatically connect user folder from DFS server when domain user logs in. I created a simple (contains one line :D) “script” to do that:
 ```

#!/bin/bash
 mount //<server.domain>/Users$/$1 /media/dfs_user -o rw,user=<domain>\\$1
 
``` I need to run this “script” with root privileges and parameter $(whoami) after domain user logs in so it results in command:
```

 mount //<server.domain>/Users$/<username> /media/dfs_user -o rw,user=<domain>\<username>
 
``` What should I do? Is there any other better way (seems little unsecure like this)? I was thinking about adding this into /etc/fstab file, but don't know how to tell it what is the actual name of logged in user... I'm using Ubuntu 10.04 x32.
 
 I'll be very thankful for any help. Have a nice day! :)

---

### Post by GNU/Linux_Rocks! on 2011-05-22
Ok, I tried something but it didn’t work as I need it to. Here is what I’ve tried:
   
  **1)** I went to System [FONT=Wingdings][FONT=Wingdings]-->[/FONT][/FONT] Preferences [FONT=Wingdings][FONT=Wingdings]-->[/FONT][/FONT] Startup Applications and created an entry for running: /var/mount_dfs_user.sh $(whoami). “Script” mount_dfs_user.sh contains one line as mentioned in my previous post: 
  ```

#!/bin/bash
   mount //<server.domain>/Users$/$1 /media/dfs_user -o rw,user=<domain>\\$1
 
```The script was run with user and not root privileges, parameter $(whoami) was not processed so the result was:  
```

mount //<server.domain>/Users$/$(whoami) /media/dfs_user -o rw,user=<domain>\$(whoami)

```  **2)** I placed the script called mount_dfs_user.sh to /usr/local/bin/ and created file /etc/xdg/autostart/mount_dfs_user.desktop to run it. The content of that file was: 
  ```

[Desktop Entry]
Type=Application
Name=Mount user dfs
Exec=/usr/local/bin/mount_dfs_user.sh $(whoami)
X-GNOME-Autostart-Delay=10
NoDisplay=true

```The script was run with user and not root privileges, parameter $(whoami) was not processed so the result was:
```

mount //<server.domain>/Users$/$(whoami) /media/dfs_user -o rw,user=<domain>\$(whoami)

```  **3)** I created a file in /etc/X11/Xsession.d/98mount_dfs_user. The content of that file was:
  ```

#!/bin/bash
echo "==============================" >> /var/log/mount_dfs_user.log
echo "mount //<server.domain>/Users$/$1 /media/dfs_user -o rw,user=<domain>\\$1" >> /var/log/mount_dfs_user.log

```The sript was again run as a user and not as a root.
  **4)** Finally I created a file /etc/init/mount_dfs_user.conf to run /usr/local/bin/mount_dfs_user.sh. Content of file /etc/init/mount_dfs_user.conf:
```

# script for connecting user folder on dfs server
description     "mount user DFS folder"
start on (started network-manager)
script
      # wait
      sleep 10
      /bin/sh /usr/local/bin/mount_dfs_user.sh $(whoami)
      exit 0
end script

```The script was run with **ROOT **privileges! Cool. :D But the parameter $(whoami) was processed as root to, so result was:
```

mount //<server.domain>/Users$/root /media/dfs_user -o rw,user=<domain>\root

```So I was unsuccessful again. :( :(
  So the question remains: 

[SIZE=2]**How to run script after domain user logs in and how to run it with root privileges???**[/SIZE] 
   
  Help me guys, pleeeeeeeeeeeeeeeeeease…
Nice day to everyone! [FONT=Wingdings][FONT=Wingdings]:)[/FONT][/FONT]

---

### Post by GNU/Linux_Rocks! on 2011-05-25
I have found much better solution than trying to run a script:

[http://buechse.de/HOWTO/samba_pam_mount_sshd/](http://buechse.de/HOWTO/samba_pam_mount_sshd/)

Using pam_mount everything works just as it should. Bye.:)

---

