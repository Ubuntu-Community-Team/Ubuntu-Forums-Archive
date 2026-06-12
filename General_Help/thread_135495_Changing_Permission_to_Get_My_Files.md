---
title: "Changing Permission to Get My Files"
date: 2006-02-24
forum: General Help
---

### Post by fishmorg909 on 2006-02-24
I'm having this terrible problem trying to get back in to my original user account. I get this messgae saying:

"Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions."

Well, nothing seems to work, no advice from any thread does anything. I did add a new user with adduser -- can I change permissions to get at my files in my default (original) user account? I'm starting to think I should get them and do a reinstall. Thanks.

---

### Post by heimo on 2006-02-24
I don't know if you already tried this. Boot to recovery mode (go to grub menu in the beginning of boot), use chown and chmod to change the files owner and permissions.

```
chown yourusername:yourusername /home/yourusername/.dmrc
chmod 644 /home/yourusername/.dmrc
```

My .dmrc is set to 600.

---

### Post by fishmorg909 on 2006-02-24
I hadn't tried in recovery mode, but that didn't work either.

Can I get my files out with the live CD or something? A reinstall is looking better and better! :neutral:

---

### Post by nanotube on 2006-02-24
hey
if you want to get access to all your files in the old user account, issue the following command:
```
sudo chmod -R 777 /home/oldusername
```
that will change permissions of all files in your old user directory for everyone to be able to access them - including your new username. :)

---

### Post by heimo on 2006-02-24
I wouldn't mess up my file permissions for backup. If you have root access using sudo, you could read those files anyway, create package (.tar.gz), burn it to CD/DVD, reinstall (if really really neccessary) and uncompress the archive back to your new system. And you wouldn't have to change all the file permissions back to what they were if you use correct flags (preserve).

---

### Post by fishmorg909 on 2006-02-24
[QUOTE=heimo]I wouldn't mess up my file permissions for backup. If you have root access using sudo, you could read those files anyway, create package (.tar.gz), burn it to CD/DVD, reinstall (if really really neccessary) and uncompress the archive back to your new system. And you wouldn't have to change all the file permissions back to what they were if you use correct flags (preserve).[/QUOTE]

That's what I'm thinking about... what's the command for opening file manager in terminal? (Noob question, but I don't know and I can't seem to find it.)

---

### Post by heimo on 2006-02-24
I believe you need to first add your new user to /etc/sudoers, or to admin group so it can use sudo. As a root (in recovery mode) you can run 
```
adduser *username* admin
```
to add *username *to admin group. Check that you have a line like
```
 %admin  ALL=(ALL) ALL
```
in /etc/sudoers file, if not, add it using 
```
EDITOR=pico visudo
```

Then you should be able to run commands in normal mode using your new user account, using [sudo and gksudo]("https://wiki.ubuntu.com/RootSudo"), for example:
```
gksudo nautilus
```

---

