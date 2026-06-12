---
title: "Sudoers File. Question."
date: 2009-11-08
forum: General Help
---

### Post by Roasted on 2009-11-08
I have 5 users on my system. I assume since jason was the first and only user created during the install that jason is the only one with sudo rights.

If I go to edit the sudoers file to add more users as having the sudo right, why is it I don't see jason already listed?

---

### Post by scragar on 2009-11-08
I think the user jason would be in the wheel group, which is listed in the sudoers file.

---

### Post by SuperSonic4 on 2009-11-08
> **scragar said:**
> I think the user jason would be in the wheel group, which is listed in the sudoers file.

I agree

you can either add the others to wheel group or mention them, by name, in sudoers

also if vi is complicated you can use nano ```
sudo EDITOR=nano visudo
```

---

### Post by scragar on 2009-11-08
Oh, just want to add, try not to break your sudoers file. It's really bad if you do, you can't use sudo afterwards, because the config file is broken, so you can't fix it.
You wind up needing to use a liveCD of some kind in order to edit the file and repair it.

The easiest way to avoid breaking the file is of course to leave it alone, and use the groups to give or remove sudo permissions.

---

### Post by Druke on 2009-11-08
I thought this exact thing is what the user settings, properties,user privileges, "Administer the system" choice was for.

---

### Post by Roasted on 2009-11-08
> **Druke said:**
> I thought this exact thing is what the user settings, properties,user privileges, "Administer the system" choice was for.

well hot damn I think you're right. I wasn't aware of that. Thanks!

---

### Post by Druke on 2009-11-08
just sayin ):P

---

### Post by Roasted on 2009-11-08
I have to ask though... what about for ubuntu server with no gui? 

Sorry - had to throw a curve ball in the situation. :lolflag:

---

### Post by Druke on 2009-11-08
A very good question... I have no idea, I'd have to analyze what "users-admin" changes exactly.

---

### Post by lavinog on 2009-11-08
add them to the admin group.
I think you can do it with:
```

sudo usermod -aG admin username

```

---

### Post by Roasted on 2009-11-08
Oh, duh. I didn't realize the admin group meant sudoers, but if it does then yeah add them to the group in terminal and everybody is happy.

Win.

):P

---

### Post by Druke on 2009-11-08
> **lavinog said:**
> add them to the admin group.
I think you can do it with:
```

sudo usermod -aG admin username

```

is that simply used by replacing username with desired username?

---

### Post by sisco311 on 2009-11-08
just add the user(s) to the admin group:
```
sudo gpasswd -a username admin
```

---

### Post by Roasted on 2009-11-08
> **sisco311 said:**
> just add the user(s) to the admin group:
```
sudo gpasswd -a username admin
```

I was just helping a buddy add users to groups on his ubuntu server, and out of all of the googling I did, I didn't see a command like this.

:confused:

---

### Post by Druke on 2009-11-08
if you're afraid he is a troll, here is [http://linux.die.net/man/1/gpasswd](http://linux.die.net/man/1/gpasswd) .

---

### Post by sisco311 on 2009-11-08
> **Druke said:**
> is that simply used by replacing username with desired username?

yep.

> **Roasted said:**
> I was just helping a buddy add users to groups on his ubuntu server, and out of all of the googling I did, I didn't see a command like this.

:confused:

there are a lot of options:

```
adduser username group
```
adduser is a scrip, it should work in most debian based distos. but for example in archlinux you can not use it add a user to a group. 

gpasswd and usermod should work in most unix/linux distros.

or you can manually edit the /etc/group file with the vipw command or with your favorite text editor.

---

