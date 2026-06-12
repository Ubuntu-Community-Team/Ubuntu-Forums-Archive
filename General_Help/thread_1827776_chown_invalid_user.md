---
title: "chown: invalid user"
date: 2011-08-18
forum: General Help
---

### Post by ysuluhan on 2011-08-18
hi all... this is my first time here, hopefully not the last...

i have a problem with changing file permissions on ubuntu server 10.10

i was installing asterisk 1.8 to the system. for that i created a user named asteriskpbx and added a group named asteriskpbx under sudoers file. added the user to the group in the group and gshadow files..

after that, tried:

$ sudo chown -R asteriskpbx:asteriskpbx /usr/lib/asterisk/

which returned something like:

chown: invalid group something something... (i really dont remember)

after seeing that, i thought maybe users and groups should have different names and changed the asteriskpbx group' s name to pbx in the gshadow, group and sudoers files.

now the command:

$ sudo chown -R pbx:asteriskpbx /usr/lib/asterisk/

returns:

chown: invalid user: `pbx:asteriskpbx`

what should i do to solve this...

thanks in advance...

---

### Post by dino99 on 2011-08-18
be sure of user/group names as they are case sensitive

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by ysuluhan on 2011-08-18
> **dino99 said:**
> be sure of user/group names as they are case sensitive

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

i'm sure of that...

---

### Post by Habitual on 2011-08-18
```
sudo grep asteriskpbx /etc/group /etc/passwd
```

to verify that user.

---

### Post by ysuluhan on 2011-08-18
@Habitual...

it verified.. was still no luck...

but after i tried: $ sudo groupadd -f pbx

it worked as a charm...

thank you for your answer...

---

