---
title: "Start-up Script Won't Run"
date: 2011-07-11
forum: General Help
---

### Post by deckerry on 2011-07-11
[COLOR="Red"]**_BACKGROUND_**[/COLOR]
I am trying to get Ubuntu 10.04 to access my Windows filesystem on start-up.

I made a script that works in the terminal, but it will not work automatically after logging in.

I added the file to the Startup Applications here (but it won't start):
System > Preferences > Startup Applications > Add
Then I found the file with the browse button.

Here is the file's information:
-rwxr-xr-x 1 ryan ryan 140 2011-07-11 14:12 mount_windows

Here is the file's code:
```

#!/bin/bash
# mount windows
echo "Mounting Windows..."
cd /mnt/windows
sudo mount -t ntfs /dev/sda1 /mnt/windows -o "umask=022"
echo "Done"

```

[COLOR="red"]**_PROBLEM_**[/COLOR]
I think that my script will not run at startup because the sudo command (sudo mount -t ntfs...) requires a password and it does not prompt the user to authenticate without using the terminal.

Does anybody know how to make this work automatically after login?

---

### Post by cdtech on 2011-07-11
Maybe a dumb question but why not add it to your fstab file? Just curious

---

### Post by deckerry on 2011-07-11
The only one asking dumb questions around here is me. (I forgot to mention that I am a total noob!)

What is the fstab file?/Where is it?

---

### Post by deckerry on 2011-07-11
By the way, I just tried to add a line in the script to open a terminal (gnome-terminal) so the startup would provide users a place to input a password but apparently simply adding "gnome-terminal" in my script just opens a terminal separately.

---

### Post by nothingspecial on 2011-07-11
> **deckerry said:**
> The only one asking dumb questions around here is me. (I forgot to mention that I am a total noob!)

What is the fstab file?/Where is it?

Hi, it's the file that is read at boot to mount partitions, exactly the thing you want.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by cdtech on 2011-07-11
Thank you nothingspecial for the link help, I'm a little slow right now at work, lol.

---

### Post by Rakeshvijayan on 2011-07-11
This may help you to know about fstab 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by deckerry on 2011-07-11
> **Rakeshvijayan said:**
> This may help you to know about fstab 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

What I really wanted to do was make myself look cool by writing a program, but I just found out that the function of my program was obsolete/unnecessary.

Before checking the link above, I managed to mess up the /etc/fstab file which caused Ubuntu to be unbootable. After the GRUB menu and before login, I received an error message something along the lines of "The disc drive for / is not ready yet or is not present..." and it gave the choice to skip or manually recover. It turns out that typing "s" for skip did nothing. So I tried "m" for manually fixing the problem.

After selecting "m" I got another error message (really sorry but I forgot what the error said) but it gave me a command line interface anyway. I tried to edit the /etc/fstab with vi using ```
sudo vi /etc/fstab
```, since I was stuck in the command line interface, but after making changes, I was unable to fix fstab. After trying to save changes to the edited fstab file, a new error said something like "read-only filesystem." To overcome the read-only obstacle I used ```
mount -n -o remount /
``` (I got that code here: [http://forums.fedoraforum.org/archive/index.php/t-144176.html](http://forums.fedoraforum.org/archive/index.php/t-144176.html)) this allowed me to edit /etc/fstab and reboot the system successfully.

The link up in the quote was extremely helpful in showing me the correct way to mount my Windows filesystem.

THANK YOU VERY VERY MUCH EVERYBODY!!!!!!:KS

---

