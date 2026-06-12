---
title: "root user"
date: 2010-05-02
forum: General Help
---

### Post by Muahdib on 2010-05-02
I cant seem to log in as root. how do I "enable" root in ubuntu?

sorry if this is covered somewhere else. I did use the search but was unable to find anything. 

thanks:guitar:

---

### Post by lisati on 2010-05-02
Ubuntu uses "sudo", have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Scunizi on 2010-05-02
This is an age old question.  Espicially for those coming from other distros using a root account.  In ubuntu there is no real root account.  Your user can become root.. so anything that needs root access preface with sudo.. ie... sudo apt-get install <package name> .. the system will prompt for your password and give you temporary root privilidges for that command.. The system will also remember you just used sudo so if you have another root command to issue do it with sudo and it won't ask for the password.. it will remember root access and password for about 5 minutes.

---

### Post by mcoleman44 on 2010-05-02
Its not a safe idea to use the root account. Everything can be done using gksudo.

---

### Post by Muahdib on 2010-05-02
thanks a lot guys. 

not at all use to not having root. 


so.. should my user account be in the admin group? or should have have more than one user? one that is just a normal user and one that belongs to the admin group? or can any user become "root" using sudo for the 15 minutes?

Ron

---

### Post by Muahdib on 2010-05-02
this may be a little off this topic.. but using vituralbox and installing XP do i need to worry about installing a virus scanner? or is the install of XP kind of protected being that its a program running in linux? 

thanks

---

### Post by Scunizi on 2010-05-02
You're already in the admin group.. or sudo group.. by using sudo for cli and gksudo for gui apps you'll have all the privilidges you typically need.

---

### Post by snowpine on 2010-05-02
> **Muahdib said:**
> this may be a little off this topic.. but using vituralbox and installing XP do i need to worry about installing a virus scanner? or is the install of XP kind of protected being that its a program running in linux? 

thanks

XP in VirtualBox is identical to XP not installed in VirtualBox. Your virus scanning needs are the same either way.

One benefit of Windows in VirtualBox is you can easily take a "snapshot" of a fresh install and restore this snapshot if your system gets messed up for any reason.

---

### Post by marshmallow1304 on 2010-05-02
> **Muahdib said:**
> so.. should my user account be in the admin group? or should have have more than one user? one that is just a normal user and one that belongs to the admin group? or can any user become "root" using sudo for the 15 minutes?

Only users in the admin group can use sudo, so your account should be a member.


> **Muahdib said:**
> this may be a little off this topic.. but using vituralbox and installing XP do i need to worry about installing a virus scanner? or is the install of XP kind of protected being that its a program running in linux?

The Windows install is not protected, but you can easily do a backup by copying the virtual hard drive somewhere.

---

### Post by Muahdib on 2010-05-02
thanks.

---

### Post by griso8v on 2010-06-05
I'm a bit of a novice, but dangerously so. I have a related question. I need to move a script file into a folder that is owner Root. I don't know how to do that with sudo or gksudo. I try to move it through the Nautilus windows, but don't have permissions. I am an administrator account. I'm trying to move the media server file twonkymedia.sh from my home directory, to "/etc/int.d". The idea is to test so that the media server starts automatically on boot. 
:confused:
Any help on copying the file from home directory to the root owner directory /etc/int.d would be greatly appreciated.

---

### Post by wojox on 2010-06-05
> **griso8v said:**
> I'm a bit of a novice, but dangerously so. I have a related question. I need to move a script file into a folder that is owner Root. I don't know how to do that with sudo or gksudo. I try to move it through the Nautilus windows, but don't have permissions. I am an administrator account. I'm trying to move the media server file twonkymedia.sh from my home directory, to "/etc/int.d". The idea is to test so that the media server starts automatically on boot. 
:confused:
Any help on copying the file from home directory to the root owner directory /etc/int.d would be greatly appreciated.

See here [https://help.ubuntu.com/community/RootSudo#Enabling%20the%20root%20account](https://help.ubuntu.com/community/RootSudo#Enabling%20the%20root%20account)

---

