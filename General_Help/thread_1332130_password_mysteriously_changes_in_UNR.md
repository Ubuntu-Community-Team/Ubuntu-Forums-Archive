---
title: "password mysteriously changes in UNR"
date: 2009-11-20
forum: General Help
---

### Post by nova3k on 2009-11-20
Hello, im sort of an Ubuntu noob. I decided to give it a try since i got an eePc netbook.

The netbook originally came with XP on it, but i decided to split the HDD and dual boot with ubuntu NBR

So i set it up, set a password, and was able to use it normally for about a week. Then all of a sudden its no longer accepting my password. I didnt set it for password at login, but it asks for one for pretty much everything else. It started giving me the following popup:

Enter password for default keyring to unlock

The application 'NetworkManager Applet' (/usr/bin/nm-applet) wants access to the default keyring, but it is locked

Password:

so i entered the admin password and it wouldnt accept it. So i clicked on deny and it went away.

I tried doing other things such as updating or reading the partition that windows was installed on, and it asks for the admin password. Which isnt particularly an issue because before i would enter it and get access, but now its telling me the password is invalid.

Nobody but me has used this system since i installed ubuntu NBR and i havent changed the password since its install. So is there a bug that changes passwords, and is there some sort of program i can run to reset the password?

Thanks for any help.

---

### Post by wilee-nilee on 2009-11-20
You can reset the password in about me in preferences, and also with this method.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by P4man on 2009-11-20
The keyring password is not the same as your login password! I mean its not the same thing, by default it will be the same password. If you change your login password however, the keyring password does not change automatically. You can change it manually using applications > accessoiries > passwords. Right click the "passwords" folder and select change password. The old password is probably the password you created for you account initially

The keyring is used to store passwords for things like email, wireless networks, IM etc. If you log in to ubuntu normally ( so no autologin), *and* the keyring password is the same as your login password, then it is unlocked automatically when you log in. But when you set autologin, or you changed only the login pw, then the keyring remains closed, and upon starting an application that uses it, you will be prompted to open it.

---

