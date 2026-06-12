---
title: "Running a 'sudo' command in a nautilus script."
date: 2009-09-23
forum: General Help
---

### Post by Karakh on 2009-09-23
Basically, all I need is a script to run the following command from nautilus and gnome-do, with or without a gui root password prompt.

```
sudo mount -t cifs //192.168.1.100/main/ /media/shared -o guest,rw,iocharset=utf8,nounix,file_mode=0777,dir_mode=0777

```

I've tried a myriad of different iterations with 'gksu' and by using a python script to automatically add the root pass (really don't want to do that), but while it works fine when run in the terminal, it never works properly in nautilus or gnome-do.

---

### Post by scragar on 2009-09-23
Could you try creating this simple bash script```
#!/bin/bash
sudo mount -t cifs //192.168.1.100/main/ /media/shared -o guest,rw,iocharset=utf8,nounix,file_mode=0777,dir_mode=0777
read -n 1
exit
```
Then run it like so from alt+f2:
```
gnome-terminal -x "/home/$USER/Desktop/script.sh"
```
It's worth a shot.

---

### Post by Karakh on 2009-09-23
Yeah, I thought of creating a second script that would launch the original script in a terminal, but it's only a last resort if I can't get it working in a single .sh file.

---

### Post by denver on 2009-09-23
Although i think its a little dangerous, you can add a sudo rule in /etc/sudoers to not prompt you for a password when executing a particular command.

Its something along the lines of:

```

Cmnd_Alias NO_PASS_COMMANDS = /path/to/your/script.sh
username ALL= NOPASSWD: NO_PASS_COMMANDS

```

NOTE: Replace "username" with your actual user.

On a side note, Gnome already has some SAMBA integration available. You might find that easyer to use.

---

### Post by Karakh on 2009-09-23
For anybody that's interested, I managed to get it working with:

```
#! /bin/bash

## requires - smbfs

foo=`gksudo -u root -k -m "enter your password for nautilus root access" /bin/echo "got r00t?"`

sudo mount -t cifs //192.168.1.100/main/ /media/shared -o guest,rw,iocharset=utf8,nounix,file_mode=0777,dir_mode=0777

exit


```

---

