---
title: "changed user /home location - can't login"
date: 2009-12-02
forum: General Help
---

### Post by scotc on 2009-12-02
Dear Ubuntu people

I wanted to change the name of my login user and thus the name of it's home directory.  (It is "scot")

What I did:
Using system/admin/users and groups/properties/advanced, I changed the location of the /home from "home/scot" to "home/admin-scot-home".
I used gksudo nautilus to change the name of the home directory from "home/scot" to "home/admin-scot-home".

I can't login on reboot.  I get the splash sound then error message something like "the /home directory was set to 'admin-scot-home' but that it doesn't appear to exist."

I have tried to undo my mistakes via recovery mode.  I CAN change the name of the user home directory back to plain "scot", but I can't get ubuntu to stop looking for "admin-scot-home".

I have edited the /etc/passwd file and removed the "home/admin-scot-home" reference to replace it with "home/scot".
I have tried to chown a few times, probably incorrectly.
I tried to adduser to give me another admin user, again, probably made mistakes.

Help please.  I will need exact commands for the recovery mode because I am not a skilled user yet.

Using ubuntu 7.10 gutsy
/home is on a separate partition.

---

### Post by Kilz on 2009-12-02
Sounds like a good time to update to a new version, Gutsy isnt even supported any more.

---

### Post by scotc on 2009-12-02
I have considered upgrading, but the last time I did, my system was unusable for a year (8.04 LTS). 
I have looked at the "known issues" etc for Karmic, Jaunty and so on.  I can't see any reason to risk an upgrade (apart from the ongoing repository support etc).
I can see MANY reasons not to risk an upgrade.  Like being able to use my computer afterwards, for one.

---

### Post by renkinjutsu on 2009-12-02
to change the home directory of a username, use usermod ```
sudo usermod -d /home/<blah> <username>
```

---

### Post by scotc on 2009-12-02
Thanks for that, but it made NO difference.

I have also added through recovery mode a new user.
Unfortunately, it had no admin privs.
I then tried to add another, with admin privs, but it would not allow me - "user does not exist".

I don't know how to give a basic user admin privs, so I am just going to give up.

Thanks to those who offered help and to the many whose "how to"s I read.

---

### Post by gwpritch on 2009-12-02
I'm wondering if it doesn't like the '-' in th username.
Try changing to something like scotadmin then run

```
sudo chown -R scotadmin:scotadmin /home/scotadmin
```

To give any user admin privilages just add them to the sudo group.

---

### Post by StuartN on 2009-12-02
> **scotc said:**
> Thanks for that, but it made NO difference.

I have also added through recovery mode a new user.

You should be able to reinstate your own home if you boot up using the Live CD, when you will be logged in as root. The home directory location is stored in /etc/passwd, but I have no idea how many other places it is stored, and which is definitive.

---

### Post by Iowan on 2009-12-02
> **scotc said:**
> I can see MANY reasons not to risk an upgrade.  Like being able to use my computer afterwards, for one.How usable is it in it's present configuration? ;)
I recently upgraded this machine from Gutsy to Hardy.  

> I don't know how to give a basic user admin privs You'd add them to the **admin** group.

---

