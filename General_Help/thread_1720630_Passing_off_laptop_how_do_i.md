---
title: "Passing off laptop how do i??????"
date: 2011-04-03
forum: General Help
---

### Post by sosaudio1 on 2011-04-03
I want to change the user name on my old laptop for my wife. I don't want to change any settings or the contents of the home folder...nor do I want to reset any prefs...

Is this possible without major bloodshed....because anyone could just name a new user, delete the old user and then have to start with a new slate of settings, pref, etc, etc....

Thanks everyone
Rich

---

### Post by bodhi.zazen on 2011-04-03
Probably the easiest method, IMO, is to boot to recovery mode and manually edit /etc/passwd , /etc/group , and /etc/shadow , replacing the old user name with the new

Then

mv /home/Old_user /home/new_user

You can do this in a few "simple" commands (from recovery mode):

```
[FONT=monospace][/FONT]usermod -d /home/new -m old

sed -i -e 's_old_new_g' /etc/passwd

sed -i -e 's_old_new_g' /etc/group

sed -i -e 's_old_new_g' /etc/shadow
```

Where "old" is the old user name and "new" is the new user name.

---

### Post by techunit on 2011-04-03
Ok open "Users And Groups" Add a new entry for your wife. Make her admin in the permissions. Save her profile. delete your profile. If it offers to delete your home folder say no.(I forget if it does) click advanced settings and where the home directory is change it to something like home/<youroldusername>

you should be set now! Good Luck.

---

### Post by sosaudio1 on 2011-04-04
> **bodhi.zazen said:**
> Probably the easiest method, IMO, is to boot to recovery mode and manually edit /etc/passwd , /etc/group , and /etc/shadow , replacing the old user name with the new

Then

mv /home/Old_user /home/new_user

You can do this in a few "simple" commands (from recovery mode):

```
[FONT=monospace][/FONT]usermod -d /home/new -m old

sed -i -e 's_old_new_g' /etc/passwd

sed -i -e 's_old_new_g' /etc/group

sed -i -e 's_old_new_g' /etc/shadow
```

Where "old" is the old user name and "new" is the new user name.

Awesome Thanks guys for this!
It worked
Rich

---

