---
title: "Sudoers Woes"
date: 2009-10-06
forum: General Help
---

### Post by nix-idioteque on 2009-10-06
Ok, so recently my default user name lost it's sudo access and was taken off the sudoers list (somehow, I don't know)

so googling brought up a tutorial: [http://www.ubuntu-inside.me/2009/07/howto-add-user-to-sudoers-list-on.html](http://www.ubuntu-inside.me/2009/07/howto-add-user-to-sudoers-list-on.html)

Now when I typed in the beginning steps I get:
```

joel@joel-linux:~$ su
Password: 
su: Authentication failure
joel@joel-linux:~$ 

```

Help me Obi Wan

---

### Post by minigeek on 2009-10-07
> **nix-idioteque said:**
> Ok, so recently my default user name lost it's sudo access and was taken off the sudoers list (somehow, I don't know)

so googling brought up a tutorial: [http://www.ubuntu-inside.me/2009/07/howto-add-user-to-sudoers-list-on.html](http://www.ubuntu-inside.me/2009/07/howto-add-user-to-sudoers-list-on.html)

Now when I typed in the beginning steps I get:
```

joel@joel-linux:~$ su
Password: 
su: Authentication failure
joel@joel-linux:~$ 

```

Help me Obi Wan


Hi

If you are using the following in /etc/sudoers

```
user ALL=(ALL) ALL
```

change the above to this 

```
%user ALL=(ALL) ALL
```

then you will need to add your user name to that group

usermod -G user joel

Hope this helps.

:popcorn:

---

### Post by nix-idioteque on 2009-10-07
how would I go about opening / editing it?

---

### Post by bigboy_pdb on 2009-10-07
You may want to look at [this article]("http://www.cyberciti.biz/tips/ubuntu-admin-group-permissions.html") instead.

You won't be able to edit the /etc/group file without root privileges. Since you're not a member of the sudoer groups, you can boot from the live CD and re-add yourself to the group from there. You'll need to mount your drive and use 'sudo' or 'gksudo' with a text editor (such as nano, vim, or gedit) or nautilus to open the file.

---

### Post by nix-idioteque on 2009-10-07
well throw me in a dress and call me Linus...

---

### Post by abhilashm86 on 2009-10-07
> **nix-idioteque said:**
> well throw me in a dress and call me Linus...

hi linus, for editing sudoers file, use this command, its default command and cannot be opened other way........
```
sudo visudo
```
then edit, for quitting ctrl-x

---

### Post by bigboy_pdb on 2009-10-07
> **abhilashm86 said:**
> 
for editing sudoers file, use this command, its default command and cannot be opened other way........
```
sudo visudo
```
then edit, for quitting ctrl-x


If you're editing the file for an Ubuntu installation that's running then yes, that's true. However, if it isn't running (such as when you edit files for an Ubuntu installation using a live CD), editing those files using other means should be fine.

**EDIT**: As a side note, the reason why sudo/gksudo is needed for the live CD is because it doesn't let you modify files on hard drive partitions by default (most likely as a security and safety measure).

**EDIT**: Actually, I didn't know that [visudo checks for syntax errors]("http://www.gratisoft.us/sudo/man/visudo.html"). That means that it might be slightly safer if you're worried about making any serious mistakes, but it isn't needed to protect the file from multiple edits since no program or person should be attempting to edit it.

---

### Post by blur xc on 2009-10-07
How did you lose sudo access?  I did once, and it was from using usermod -G and not usermod -aG (-a for append to list of groups).  The -G by itself takes removes you from every group you belong to except the one you are just adding yourself to.  To fix it, I just booted into recovery mode and added myself back to the admin group.  Easy cheesy...

Log in- got to terminal and enter "groups" and see what groups you belong to.

BM

---

### Post by renkinjutsu on 2009-10-07
you can reboot into recovery mode and have root access there ;)

---

### Post by sisco311 on 2009-10-07
> **nix-idioteque said:**
> Ok, so recently my default user name lost it's sudo access and was taken off the sudoers list (somehow, I don't know)
[/CODE]

Help me Obi Wan
[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

---

### Post by nix-idioteque on 2009-10-07
> **blur xc said:**
> How did you lose sudo access?  I did once, and it was from using usermod -G and not usermod -aG (-a for append to list of groups).  The -G by itself takes removes you from every group you belong to except the one you are just adding yourself to.  To fix it, I just booted into recovery mode and added myself back to the admin group.  Easy cheesy...

Log in- got to terminal and enter "groups" and see what groups you belong to.

BM

aha!  usermod -G is what did it!

---

