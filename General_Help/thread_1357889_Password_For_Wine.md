---
title: "Password For Wine"
date: 2009-12-17
forum: General Help
---

### Post by joelandsonja on 2009-12-17
I am trying to figure out how I can restrict other people who use this computer from installing programs with wine. 

Here's what I did so far:

- Clicked on 'Browse c:\ Drive' in the Wine Directory
- Right clicked on 'Program Files' 
- Clicked on The 'Permissions' Tab
- Set permissions to 'Access Only'

Now, the only problem is that anyone can just right click and reset the permissions so they can install a new program. 

What I am hoping for is to set a password for changing the Permissions ... can this be done?

Thanks for the help!

---

### Post by bodhi.zazen on 2009-12-17
Well, first that will affect only you, you will need to make changes in every users ~/.wine

Other then that, simply make each such directory owned by root, and rx by everyone else

---

### Post by joelandsonja on 2009-12-17
Hmm, thanks for the reply, although the directions are bit over my head. 

I usually have to say this every time I ask a question on here, but I am a newbie to the highest degree and would certainly appreciate step by step directions.

Thanks again for the help!

---

### Post by bodhi.zazen on 2009-12-17
Each user has a home directory

In each home directory is a "hidden" or . directory .wine

In each .wine is a c drive and Program files.

Use chown and chmod on Progarm files

Become root

```
sudo -i
```

Then

```
cd /home/user_1/.wine/dosdevices/c:
chown root.root Program\ Files
chmod 755 Progam\ Files
```

Repeat for each user.

For additional information see

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo") 

[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by joelandsonja on 2009-12-18
Excellent, thank you so much for the help!

---

### Post by bodhi.zazen on 2009-12-18
You are most welcome =)

---

