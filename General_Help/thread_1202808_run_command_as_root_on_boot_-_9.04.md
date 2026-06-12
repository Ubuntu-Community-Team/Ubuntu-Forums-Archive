---
title: "run command as root on boot - 9.04"
date: 2009-07-02
forum: General Help
---

### Post by Jungle_King on 2009-07-02
i have hamachi starting automatically on boot, but it requires tuncfg to be run as root before it can load

in 8.10 this wasnt an issue, but in 9.04 you have to type in the root password before it will load.

this is fine when im at home, but if the system has rebooted and im trying to vnc over vpn im not going to be at the machine to type the root password in

does anybody know what i have to include in a script to have a command run as root when im booting?

cheers guys

---

### Post by Boondoklife on 2009-07-02
How do you have this starting? is it part of the init?

---

### Post by Jungle_King on 2009-07-02
ve worked it out! woop

ive modify the script thats on all the other guides:


[LIST=1]
[*]Create the start-up script for hamachi in your home directory, as shown below. Remember to change the user name "your name" *(line 5)* to your system user name in Ubuntu (or your linux distribution).  Call the script "hamachi."[INDENT] #!/bin/bash
###################################
### Start-up script for Hamachi ###
###################################
USER=your name
case "$1" in
start)
    /sbin/tuncfg
/bin/su - $sudo -c "tuncfg"
    /bin/su - $USER -c "hamachi start"
    ;;
stop)
    /bin/su - $USER -c "hamachi stop"
    ;;
restart|force-reload)
    /bin/su - $USER -c "hamachi start"
    /bin/su - $USER -c "hamachi stop"
    ;;
*)
    exit 1
    ;;
esac
 exit 0 
[/INDENT]
[*]Make the script executable:[INDENT]chmod +x hamachi
[/INDENT]
[*]Move the script to /etc/init.d/ directory:[INDENT]sudo mv hamachi /etc/init.d
[/INDENT]
[*]Finally, link the script to the appropriate run-level for booting up the system:[INDENT]sudo ln -s /etc/init.d/hamachi /etc/rc2.d/S99hamachi
[/INDENT][INDENT]sudo ln -s /etc/init.d/hamachi /etc/rc2.d/K99hamachi
[/INDENT]It seems **2** is the default level for Debian and Ubuntu. In most other distribution, it is **5**.
[*]Finally, reboot your system and Hamachi will be automatically loaded and connected to the server.
[/LIST]

---

