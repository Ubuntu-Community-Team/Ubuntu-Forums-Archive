---
title: "Synaptic"
date: 2011-05-19
forum: General Help
---

### Post by northwestern on 2011-05-19
Whenever I open the the SYNAPTIC command I get the message "**Starting Without Administrative Privileges**"**-you will not be able to apply changes.**
How do I get permission to apply changes.
Regards
Northwestern

---

### Post by sj1410 on 2011-05-19
you have to launch it with "gksudo synaptic", just type in the password & goooooo


----------------------------------------
[Keeping Children Safe Online]("http://blog.swapnil.me/2011/05/keeping-children-safe-online.html")

---

### Post by Mr. Shannon on 2011-05-19
I think you are using the command

```
synaptic
```

in the command line.  You are probably getting this message because you did not give the command root privileges.  There are two ways to do that.

1. Go to ** System->Administration->Synaptic Package Manager**.  This will open up a window that will ask for your user password, after entering it synaptic will start up with root privileges allowing you to change what packages are installed.  Note: The method obove is for the GNOME desktop, if you are using the Unity desktop then you can click on the button on the right of the top bar and then choose **System Settings**, this will open up the **Control Center**, now choose **Synaptic Package Manager**.  You can probably get to synaptic through the search in Unity as well but I don't use Unity so I am not certain.

2. In the command line use
```
gksudo synaptic
```
this will open up to a window that will ask for your password just like method 1.  Note: gksudo (kdesu if using Kubuntu/KDE) is is for giving root privileges to applications that run in a window and sudo is for giving root privileges to command line applications.

---

### Post by garvinrick4 on 2011-05-19
> **northwestern said:**
> Whenever I open the the SYNAPTIC command I get the message "**Starting Without Administrative Privileges**"**-you will not be able to apply changes.**
How do I get permission to apply changes.
Regards
Northwestern Any applications to make changes to system if you use the terminal
to invoke will need root privileges. In other words use "sudo" a lot of times need to use "gksudo" so read up on when to use sudo and gksudo , here you go a link below.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by northwestern on 2011-05-19
Thanks for your help, easy when you know how.
Regards
Northwestern

---

