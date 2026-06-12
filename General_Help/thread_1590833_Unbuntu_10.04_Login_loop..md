---
title: "Unbuntu 10.04 Login loop."
date: 2010-10-08
forum: General Help
---

### Post by Fazbot on 2010-10-08
Basically I can't log in with the GUI. I've looked around found various different solutions and none of them have worked. I can still log in through the terminal.

[http://ubuntuforums.org/showthread.php?t=1507373](http://ubuntuforums.org/showthread.php?t=1507373)
[http://ubuntuforums.org/showthread.php?t=1433987](http://ubuntuforums.org/showthread.php?t=1433987)

These are two of the threads I tried to follow no avail.

When I put in
grep -i gnome /var/log/daemon.log
grep -i gnome /var/log/syslog
It says a few times over: WARNING: Could not launch 'quitcount.desktop' unable to start application Failed to execute child process "quitcount" (No such file or directory)

But these were all from before the problem started and I tried installing quitcount again and it doesn't work(I think I tried unistalling it and all associated as well which didn't help either)

I thought it might be the path as it happened when I was trying to get suns java. When I put in echo $PATH it came back showing my Java path twice so I changed the bash_profile to include

PATH = $PATH:usr/java/jdk1.6.0_21/bin:/bin:/usr/bin:/usr/sbin
export PATH

When I type echo $PATH

it shows

:usr/java/jdk1.6.0_21/bin/:usr/java/jdk1.6.0_21/bin:/bin:/usr/bin:/usr/sbin
(yes with the extra / at the end of the first Java path I don't know where this is set and could be the problem)

When I first log into the terminal it tells me
-bash: getent: command not found
-bash: cut: command not found
-bash: expr: command not found

So I think this might be the problem but I'm a Linux newbie so I'm not sure

I also tried installing upgrading gnome-session and gnome-desktop-environment and uninstalling and re-installing gdm

All to no avail.

If anyone has any suggestions please let me know, thanks in advance. And all of this is copied by hand so there might be something missing in mine that would look like it would cause the problem but was my mistake.

Regards
Fazbot

---

### Post by UnterUn on 2010-10-08
Hey! I've had a [similar ]("http://ubuntuforums.org/showthread.php?t=1589984&highlight=fataL")problem lately and after countless attempts and reinstall i found this to work:
```
sudo apt-get install ubuntu-desktop
```
which i believe reinstalls ubuntu over what you already have but I'm not completely sure (Kind of a last effort) But i kept my documents intact and gained the programs that i had deleted that came with the distro. - Either way might be worth a try if you can't figure out anything else (Like before you re-install Linux).

---

### Post by dabl on 2010-10-08
#10 on these FAQs provides some guidance that might help: [http://kubuntuforums.net/forums/index.php?topic=3099811.0](http://kubuntuforums.net/forums/index.php?topic=3099811.0)

Read "gksudo" instead of "kdesudo", and "gnome" instead of "KDE".

---

### Post by Fazbot on 2010-10-10
> **UnterUn said:**
> Hey! I've had a [similar ]("http://ubuntuforums.org/showthread.php?t=1589984&highlight=fataL")problem lately and after countless attempts and reinstall i found this to work:
```
sudo apt-get install ubuntu-desktop
```which i believe reinstalls ubuntu over what you already have but I'm not completely sure (Kind of a last effort) But i kept my documents intact and gained the programs that i had deleted that came with the distro. - Either way might be worth a try if you can't figure out anything else (Like before you re-install Linux).

Thanks for the reply no dice with that I'm afraid. Will try your solution dabl as soon as I can, thanks.

---

