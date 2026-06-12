---
title: "Don't Have Permission?"
date: 2006-02-27
forum: General Help
---

### Post by Das Ein on 2006-02-27
I'm logged in as [name] which I set up as the root user and it says I don't have permission to write to quite a few things.

---

### Post by aysiu on 2006-02-27
For some reason, I'm not able to see your image fully. These links may help, though:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/linux/permissions](http://www.psychocats.net/linux/permissions)

---

### Post by bluevoodoo1 on 2006-02-27
if you want to be able to drag and drop things into the file systems area of nautilus, you need to open nautilus with sudo... 

```

sudo nautilus --no-desktop
```

---

### Post by uopjohnson on 2006-02-27
The root user is root.  You probably set your user up to be able to use sudo which will give you root access, but not in the gui.  If you want to open something as root search this forum and the wiki for open as root.  There are a couple of good scripts and guides out there.  There is also an item "open as" or some such in your menu that you can use to open specific programs as root.

---

### Post by taurus on 2006-02-27
In other words, jordan is NOT root.  Root is root and jordan is just a user on the system who has a privilage to run root's commands with sudo...

---

### Post by Das Ein on 2006-02-27
[QUOTE=aysiu][https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)[/QUOTE]
:$ I didn't know that. Is there a quick list of sudo commands?

---

### Post by aysiu on 2006-02-27
[QUOTE=Das Ein]:$ I didn't know that. Is there a quick list of sudo commands?[/QUOTE] Sudo itself is not a command (as far as I know). You preface other commands *with* sudo.

For example, instead of doing this (what typically happens in other Linux distributions--logging in as root and making changes, then logging out of root): ```
su
password:
apt-get update
apt-get install firefox
exit
exit
``` in Ubuntu we do this (temporarily assume root privileges for each command): ```
sudo apt-get update
password:
sudo apt-get install firefox
exit
```

---

