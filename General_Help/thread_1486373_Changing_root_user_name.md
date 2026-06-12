---
title: "Changing root user name??"
date: 2010-05-17
forum: General Help
---

### Post by Autodave on 2010-05-17
I often put together complete computers from spare parts.  When I do, I put Linux on them and put my name as the root user.  However, I don't build these to keep them for myself.....I usually end up giving them away to someone who needs one and can't afford to buy one.  What I would like to do before givi9ng them away is to change the root user name to their name.  How can I do that?  CAN I do that?

---

### Post by CharlesA on 2010-05-17
You don't change the root user name on Ubuntu. You can do an OEM install if you want to give it away. That way the user can add whatever username they want to use.

---

### Post by Autodave on 2010-05-17
> **CharlesA said:**
> You don't change the root user name on Ubuntu. You can do an OEM install if you want to give it away. That way the user can add whatever username they want to use.

No way at all?  I like to get everything loaded onto the machine: programs, plug-ins for Firefox, etc to make sure everything works.  Only when I know that I have a good, working machine will I offer it to someone.  That means a few hours of work that I would have to repeat to get their name on it instead of mine......

---

### Post by CharlesA on 2010-05-17
I guess you could add a user and then delete the one you have, but idk how well that would work, since most user settings are stored in your home directory.

---

### Post by warfacegod on 2010-05-17
root is not your username. root is the system's username (sort of). Doing things in your account "as root" isn't the same as being the root user.

Bearing that in mind, have you considered creating another user account for the person you give the computer to and then using that account to delete yours?

---

### Post by Dayofswords on 2010-05-17
> **Autodave said:**
> No way at all?  I like to get everything loaded onto the machine: programs, plug-ins for Firefox, etc to make sure everything works.  Only when I know that I have a good, working machine will I offer it to someone.  That means a few hours of work that I would have to repeat to get their name on it instead of mine......

you could clone the drive and then turn it on and enter recovery mode to edit the user names when in the root shell

---

### Post by warfacegod on 2010-05-17
> **CharlesA said:**
> I guess you could add a user and then delete the one you have, but idk how well that would work, since most user settings are stored in your home directory.

Then change the name of the Home folder.

---

### Post by wojox on 2010-05-17
I don't really think you changed root's name did you? If you are then stop. 

I believe what you mean is when you first load the OS on to the computer, you assign dave as admin which has root privileges. So all you need to do when your done is create your new user with full privileges and delete your account.

---

### Post by Autodave on 2010-05-17
> **warfacegod said:**
> Then change the name of the Home folder.

OK.....when I have the machine running, my name appears in the top corner and I would like it to have their name there.  Is this something different?  Is this easy to accomplish?

---

### Post by warfacegod on 2010-05-17
If you create a new account, their name will be there instead of yours.

---

### Post by louieb on 2010-05-17
Not quite  that easy - but dooable. See discussion here 			 			[how to rename username]("http://ubuntuforums.org/showthread.php?t=1164657")

---

### Post by marshmallow1304 on 2010-05-17
Here's my suggestion.

Do the oem install as described [here]("https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview") (the screenshots are old, but the process is the same).  Stop just before running 
```
sudo oem-config-prepare
```
Now customize the machine as desired by adding/removing/upgrading packages and setting up settings.  When you're done, copy everything in /home/oem/ (remember hidden files/folders) to /etc/skel using
```
gksudo nautilus
```
Now you can run the prepare command, or more easily, run the "Prepare for shipping to the end user" on the Desktop.  Shutdown, and the next time the machine boots, your user will be able to set up his/her own account and still have the default settings and programs you chose.


If you want subsequent users to have default settings instead of the ones you created, put a script in /etc/skel/Desktop containing
```
gksudo rm -rf /etc/skel/*
```
and tell the user to run it.

---

