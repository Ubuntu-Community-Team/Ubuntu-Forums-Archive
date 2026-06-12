---
title: "sudoers, add specific command to run as root without password"
date: 2012-01-04
forum: General Help
---

### Post by Cool Javelin on 2012-01-04
Hello all, I have the need to run a command as root, but need the ability to do so without entering the password when starting the program.

```
sudo /path/HomeAuto

```

Actually, I have this command in my .bashrc and I won't be there to enter the password when the system boots (see specifics below.)

I understand I can enter a line in my sudoers file, but reading through the man page it seems overwhelming.

Can someone please help?

Thanks, Mark.

Specifics:
I am using Ubuntu 10.10 server,

I have a data acquisition board and the software I wrote (called HomeAuto) requires root privileges in order to access the ports on the board, thus  sudo /path/HomeAuto.

I changed the tty2.conf to automatically log me in to tty2 when the system reboots.

I added the proper command in my home .bashrc file to start my acquisition program when tty2 logs in.

All that works, except when the system boots, it asks for a password and I need to bypass the step of entering the password.

Thx

---

### Post by Buntumatic on 2012-01-04
You could use udev rules to change ownership of those ports and give your user rights to access them without being root. That's the proper *nix way.
Anyway, writing from memory something like

```
<username> localhost = NOPASSWD: /path/to/command
```

should do.

---

### Post by Lars Noodén on 2012-01-04
The syntax of /etc/[sudoers](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sudoers.5.html) is pretty simple even if the documentation is a bit abstract.

```

%autousers ALL=(ALL) NOPASSWD:/path/HomeAuto

```

That will allow members of the group "autousers" the ability to run the program without needing the password.  If you want to prohibit them adding options to the program, then add empty quotes afterward.

```

%autousers ALL=(ALL) NOPASSWD:/path/HomeAuto ""

```

---

### Post by Cool Javelin on 2012-01-04
Thanks, Buntumatic. I looked into the udev thing. It turns out Ubuntu doesn't recognize the data acquisition board and therefore doesn't make an entry in the /dev directory. (I have other posts on this matter.) As it turns out, Ubuntu (or Linux) denies non root access to any ports it does not know about.

Thanks Lars Noodén. I created a group, HOMEAUTO, then used usermod -a -G HOMEAUTO mark to add myself to that group.

Then in sudoers I added the line you suggested, and it worked.

I am so happy.

Thanks you both for your help.

Mark.

---

