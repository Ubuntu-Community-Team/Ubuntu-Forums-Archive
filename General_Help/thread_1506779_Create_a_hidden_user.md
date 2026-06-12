---
title: "Create a hidden user"
date: 2010-06-10
forum: General Help
---

### Post by pepsifx357 on 2010-06-10
Is there a way to create a user that will not show up in the GDM login screen?  This user also needs to have sudo access.

Thanks.

---

### Post by KeyserSoze93 on 2010-06-10
Try giving the user a UID below 1000. This makes Ubuntu treat the user as a system user, which then won't show up on the login screen.

Add the user in whatever way you prefer, and then run:

```

sudo usermod -u 599 newuser

suder usermod -a -G admin newuser

```

Where 599 is an unused UID below 1000, and newuser is your new user. The first command changes the UID and the second adds the user to the admin group, granting them sudo rights.

---

### Post by pepsifx357 on 2010-06-10
So inputting 

```
sudo usermod -u 999 ben
```

Would work?  Also, lets say I already have a user named ben, would that matter?

and the second code puts the user in the sudoers file correct?

I tried the first command with user name "tech" and got:

```
usermod: user 'tech' doesn't exist
```

---

### Post by KeyserSoze93 on 2010-06-29
Neither of the commands create a user. You need to do that first. You can give the user a < 1000 UID at the time of creation too. Try consulting the manual for adduser.

---

### Post by xenosaga456 on 2010-06-29
im pretty sure u have to log in as root to do this

---

### Post by KeyserSoze93 on 2010-10-01
> **xenosaga456 said:**
> im pretty sure u have to log in as root to do this

sudo does the job on my servers.

---

### Post by XBMC old School on 2011-02-13
> **KeyserSoze93 said:**
> Try giving the user a UID below 1000. This makes Ubuntu treat the user as a system user, which then won't show up on the login screen.

Add the user in whatever way you prefer, and then run:

```

sudo usermod -u 599 newuser

suder usermod -a -G admin newuser

```Where 599 is an unused UID below 1000, and newuser is your new user. The first command changes the UID and the second adds the user to the admin group, granting them sudo rights.

Hey Keyser,

Your tip worked well. Almost too well. When I go into users/groups my hidden account doesn't show up. So i can't mod or delete it (sorry not an uberTERMINAL user). Though i can see in the /home folder. I gave it a user# under 1000 and group# under 1000. 

How do i get it back in the user/group and maintain it as hidden on the loggin? Do i just give the account a user# greater than 1000? If so, how can I do that?

---

