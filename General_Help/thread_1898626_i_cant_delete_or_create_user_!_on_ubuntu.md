---
title: "i cant delete or create user ! on ubuntu"
date: 2011-12-21
forum: General Help
---

### Post by Discorief on 2011-12-21
i got this message when i want to delete user acount on ubuntu .... 

[http://i655.photobucket.com/albums/uu277/Carl24_2009/Screenshotat2011-12-22075136.jpg](http://i655.photobucket.com/albums/uu277/Carl24_2009/Screenshotat2011-12-22075136.jpg)

so try to create another user account and i got this message

[http://i655.photobucket.com/albums/uu277/Carl24_2009/Screenshotat2011-12-22075223.jpg](http://i655.photobucket.com/albums/uu277/Carl24_2009/Screenshotat2011-12-22075223.jpg)

sorry for my bad english ... need help :confused:

---

### Post by LowSky on 2011-12-21
create a new user from a terminal.

the arch linux guide should work.. read carefully, its better than the Ubuntu guide, but a more technical

[https://wiki.archlinux.org/index.php/Users_and_Groups#User_management](https://wiki.archlinux.org/index.php/Users_and_Groups#User_management)


basically you will do this (change ***_username_*** to what you wish it to be)

```
sudo useradd -m -g users -G audio,lp,optical,storage,video,games,power,scanner -s /bin/bash _***username***_

sudo passwd ***_username_***
```

---

### Post by Discorief on 2011-12-21
but how about to delete user acount ? 

i need help ... should i reinstall ?

---

### Post by drmrgd on 2011-12-22
I don't think you need to reinstall.  Looks like it's a permissions issue, but I'm not sure why you're not getting asked for admin password.  

You can remove users from the system through the command line by:

```
sudo userdel -r username
``` 

The "-r" part also removes the user's home directory.  If you don't want to do that, then you can remove the "-r" from the command.  Also, be sure the user is logged out when you try this.

---

### Post by MartijnNL on 2011-12-22
Reinstallation should not be necessary.

The second error seems to indicate that you are trying to create a username with unusual characters in it. A space perhaps? The best is to use only lowercase letters, and perhaps numbers. But start with a lowercase letter. There's also a separate field for the full name which is used in the login menu for example. There you can use spaces and such.

---

### Post by emmomalick on 2011-12-22
First of all make sure that you're logged out of the account which you're trying to remove, and, You must be an administrative user to delete user accounts. 

Open a terminal window.

2. First, you&#8217;ll need to delete the user account. Input the following command and hit Enter (change to the name of the user account that is to be removed):

```
sudo userdel
```

3. Now you&#8217;ll want to delete the Home directory for the deleted user account. Input the following command and hit Enter (change to the name of the user account that is to be removed):

```
sudo rm -r /home//
```

---

### Post by Discorief on 2011-12-22
run the terminal and put the command , but i get this

sarief@arief-AO722:~$ sudo userdel zezee
[sudo] password for arief: 
userdel: cannot lock /etc/passwd; try again later.

what should i do ?

---

### Post by drmrgd on 2011-12-22
That is the error you get from inadequate permissions.  First, to be sure, does the account "arief" for which you were asked a password have administrative rights?  I'm a little confused, because in the first screenshot the system administrator was listed as "Pepey".  

If "arief" does have admin rights, I also want to be sure that you entered the password for "arief" and not for "zezee".

With your admin account, can you also type in:

```
id
```

into the terminal and post back the results.

---

### Post by Discorief on 2011-12-22
no, i want to delete zezee user not pepey/arief user

---

