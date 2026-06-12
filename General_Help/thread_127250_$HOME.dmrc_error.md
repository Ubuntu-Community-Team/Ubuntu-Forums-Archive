---
title: "$HOME/.dmrc error"
date: 2006-02-08
forum: General Help
---

### Post by rawkasaurus on 2006-02-08
When I boot into Ubuntu but before I see the Gnome desktop, I get an error that says "Your $HOME/.dmrc file has incorrect permissions and is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions."

I remember messing around with some of my permissions on one of my folders but I can't remember which one.  Right now my /home directory has 777 permissions but I changed them to 644 through the gui and I couldn't run anything.  I didn't restart after I did this out of fear that I'd break my system somehow, but now I am just confused.

What can I do to fix this.

---

### Post by TrD on 2006-02-08
You must set the permissions to the file .dmrc to 644

go to your home folder, click view -> show hidden files
now search for that file click properties and set the right permissions.
hope it helps.

---

### Post by rawkasaurus on 2006-02-09
So I tried that and I still get the same error... :(

---

### Post by AndyCooll on 2006-02-09
As you may have guessed,the problem is because you've been altering the settings to your Home folder. Reset the permissions to your home folder to the default 755.

The problem with altering permissions to your home folder is that many applications settings are contained within it (usually hidden) and on boot up they need access to this folder (hence why "Group" and "Others" need read and execute access to it).

:cool:

---

### Post by rawkasaurus on 2006-02-10
Okay, that worked. :D

---

### Post by sonic808 on 2006-12-26
Hey I get this error too the only problem is I only had one log in name besides the root account (which I don't know how to access) is there a way to resets this? Please I really really need help :( ](*,)

---

### Post by bnepro on 2008-04-13
TrD. thanks for the intel, that worked like a champ.

---

