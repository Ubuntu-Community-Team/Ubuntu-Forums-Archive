---
title: "Unlock the 'default' keyring at startup"
date: 2011-04-26
forum: General Help
---

### Post by lilso on 2011-04-26
Hello,

At each startup, Ubuntu asks me for the password for the keyring. ```
An application wants access to the keyring 'Default', but it is locked. 
Enter password for keyring 'Default' to unlock
```
Even if I choose:```
Automatically unlock this keyring whenever I'm logged in
```it keeps asking it to me at each startup and the connection does not establish if I don't do it. I don't see anything special in the settings for "Passwords and Encryption keys"

Is there a way to remove this?

Thanks for your help

---

### Post by KegHead on 2011-04-26
Hi!

You could try:

system...preferences..startup programs and uncheck the gnome keyrings.

KegHead

---

### Post by Horseboy on 2011-04-26
Yeah, same here, very annoying to have to enter my pass every time i want to connect to the net.

---

### Post by lilso on 2011-04-26
> **KegHead said:**
> Hi!

You could try:

system...preferences..startup programs and uncheck the gnome keyrings.

KegHead

I tried to uncheck the 2 startup programs called "Secret Storage Service" and "SSH Key Agent" as you suggested, but it still asks for the password it after reboot!

thanks for your help

---

### Post by gandaran on 2011-04-26
if the keyring is just for the wireless internet connection then put a check mark in the **for all users** box on the wireless connection setup, it wont ask you again for the password.
another way is to remove the existing keyring in Passwords and Encryption keys (clean up everything there) then next time it asks to set up the keyring password just set a blank password and the keyring will never show up again.

---

### Post by lilso on 2011-04-26
It works now. 

For the other user following this thread, what I did was to remove the "Default" keyring from the system settings. At the next startup, it prompted me for the WPA password which I entered, and then if I wanted to save the keyring. I then clicked OK, it asked me if I was sure to accept the "unsafe storage" of my passwords. Done!

Thanks KegHead, gandaran.

---

### Post by SirGe on 2011-05-04
Setting empty passwords for keyrings or storing passwords outside of keyrings is inherently insecure: anyone, that can access the machine, can get to the info. If that's OK, just skip the rest of this post.

The login keyring is unlocked when you log in. Unfortunately, gnome uses the default keyring to store passwords. The default keyring is named 'Default'. This can be fixed in the 'Passwords and Encryption Keys' applet.

1. right-click on the 'login' keyring and set it as default.
2. unlock the 'Default' keyring and make sure you have a record of all the passwords in there; note each application that needs these passwords. In my case there are passwords for wireless networks and the Ubuntu Software Center (because I left a comment on a package, which requires an identity).
3. Right-click the 'Default' keyring and delete it.
4. Go into each app, that had a password stored, and get it to ask you to enter the password. It will be stored in the new default keyring - the one named 'login'.

Done. Now your login keyring is also the gnome keyring. Sorry, there appears to be no support in Seahorse (that's the applet) to export/import or copy/paste passwords between keyrings - corresponding menu entries are disabled.

Hope this works for you as well as it did for me.

---

### Post by powerofpi on 2011-08-23
> **SirGe said:**
> Setting empty passwords for keyrings or storing passwords outside of keyrings is inherently insecure: anyone, that can access the machine, can get to the info. If that's OK, just skip the rest of this post.

The login keyring is unlocked when you log in. Unfortunately, gnome uses the default keyring to store passwords. The default keyring is named 'Default'. This can be fixed in the 'Passwords and Encryption Keys' applet.

1. right-click on the 'login' keyring and set it as default.
2. unlock the 'Default' keyring and make sure you have a record of all the passwords in there; note each application that needs these passwords. In my case there are passwords for wireless networks and the Ubuntu Software Center (because I left a comment on a package, which requires an identity).
3. Right-click the 'Default' keyring and delete it.
4. Go into each app, that had a password stored, and get it to ask you to enter the password. It will be stored in the new default keyring - the one named 'login'.

Done. Now your login keyring is also the gnome keyring. Sorry, there appears to be no support in Seahorse (that's the applet) to export/import or copy/paste passwords between keyrings - corresponding menu entries are disabled.

Hope this works for you as well as it did for me.

Very thorough answer! Fixed my annoyance, thanks!

---

