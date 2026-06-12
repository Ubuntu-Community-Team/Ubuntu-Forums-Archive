---
title: "Hide user from login screen"
date: 2009-12-02
forum: General Help
---

### Post by Vishnu V on 2009-12-02
hai

i have 2  user accounts .I want only one of them in the login screen.I want to access the second one by typing user name and password in the other (like root login)

please help 

Thanks

---

### Post by michaelzap on 2009-12-02
I don't know if you can do that with the new Karmic GDM. You can hide all of your user accounts by default so that you need to type in either user name, however. Just enter this one command into a terminal:
```
sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list true
```

---

### Post by wojox on 2009-12-02
[Like This ?]("http://ubuntuforums.org/showthread.php?t=1321845")

---

### Post by Vishnu V on 2009-12-03
Thanks 
Problem Solved

---

### Post by allCuExpMa on 2009-12-21
Hi Guys,

I've got 3 users n I wanna hide just one of them, is there a way to do that?

thx T[m]

---

### Post by Vishnu V on 2010-01-01
> **allCuExpMa said:**
> Hi Guys,

I've got 3 users n I wanna hide just one of them, is there a way to do that?

thx T[m]
Set uid of the user (you want to hide )to any number which is less than 1000

---

### Post by djtarki on 2010-06-15
Thanks very much. It worked!!

---

### Post by Ambious on 2010-08-25
,Doesn't work for me
After I change the user ID, it just changes back to it's original UID by itself.
Strange.

---

### Post by Tony_Harrison on 2010-12-21
I have the same problem. I change it to 999, reboot, and it is back to 1001.

*EDIT*

I jumped the gun a bit there. I used the console and entered:
```
usermod -u 999 username 
```

This seemed to do the trick. I would still be curious why this sticks after a reboot but the System->Administration->Users and Groups method does not.

---

### Post by bertd2 on 2011-01-08
FYI: The accounts shown (and hidden!) on the login screen are controlled by [FONT="Courier New"]/etc/gdm/custom.conf[/FONT]. In earlier versions of Ubuntu, a control panel was available to hide users from the login screen (I recall that it was possible in System->Administration->Login Screen, but I'm not positive).

If you're comfortable editing files, you can edit [FONT="Courier New"]/etc/gdm/custom.conf[/FONT]. Look for the [FONT="Courier New"][greeter][/FONT] section. If there's an entry that reads [FONT="Courier New"]Exclude=nobody[/FONT], change it to [FONT="Courier New"]Exclude=nobody,admin,reception[/FONT]. If the Exclude line doesn't exist yet, then add it:

```

[greeter]
Exclude=nobody,admin,reception

```

You will need to restart gdm, which will log you out, so the easiest way of effecting the change is to simply reboot.

---

### Post by aksshay on 2012-12-13
Open the file /etc/lightdm/users.conf :

# # User accounts configuration # # NOTE: If you have AccountsService installed on your system, then LightDM will # use this instead and these settings will be ignored # # minimum-uid = Minimum UID required to be shown in greeter # hidden-users = Users that are not shown to the user # hidden-shells = Shells that indicate a user cannot login # [UserAccounts] minimum-uid=500 hidden-users=nobody nobody4 noaccess hidden-shells=/bin/false /usr/sbin/nologin   Append the users you want hidden to the hidden-users=line there.

---

### Post by howefield on 2012-12-13
Old thread back to sleep.

---

