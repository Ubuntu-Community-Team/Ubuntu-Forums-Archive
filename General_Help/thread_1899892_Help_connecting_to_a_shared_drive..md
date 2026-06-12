---
title: "Help connecting to a shared drive."
date: 2011-12-24
forum: General Help
---

### Post by erbad on 2011-12-24
I am trying to connect from my Ubuntu laptop to a share that is found on my Ubuntu desktop.

On my laptop, when I go to Places=>Network=>Windows Network=>Workgroup=>Ubuntu-desktop, I can see the folder that I have shared.  When I double click on it, a dialog box comes up asking for username, domain (already filled with Workgroup) and password.

I enter my root username and root password which is the same on both computers, but I cannot connect to the share.

Would someone know what I might be doing wrong?  I know in Windows, sometimes you have to enter the username as domain/username, is there something similar in Linux.  Just as an FYI, I have never mapped drives in Linux before so I don't know if I have missed a step or not.

---

### Post by rjf1 on 2011-12-25
> **erbad said:**
> I am trying to connect from my Ubuntu laptop to a share that is found on my Ubuntu desktop.

On my laptop, when I go to Places=>Network=>Windows Network=>Workgroup=>Ubuntu-desktop, I can see the folder that I have shared.  When I double click on it, a dialog box comes up asking for username, domain (already filled with Workgroup) and password.

I enter my root username and root password which is the same on both computers, but I cannot connect to the share...

When I click on 'Network' I get an icon representing my other computer in addition to a 'Windows Network' folder icon. I ignore the 'Windows Network' icon and click the icon for my other computer, and all my shares show up.

---

### Post by erbad on 2011-12-25
> **rjf1 said:**
> When I click on 'Network' I get an icon representing my other computer in addition to a 'Windows Network' folder icon. I ignore the 'Windows Network' icon and click the icon for my other computer, and all my shares show up.

I just tried it again and this time, the folder showed up next to the Windows Network icon.

However, the key here is that I can't access the share.  I use the same username/password on both Ubuntu computers, but when I type it in, the username/password dialog box keeps popping up.

---

### Post by Morbius1 on 2011-12-25
Did you create a samba password for that user on the server?

For example:
```
sudo smbpasswd -a morbius
```

---

### Post by erbad on 2011-12-25
> **Morbius1 said:**
> Did you create a samba password for that user on the server?

For example:
```
sudo smbpasswd -a morbius
```

Thanks, I bet this is it.  I'll have to give this a try when I get back home.

Can this only be done through a terminal session or is there a GUI that I can use to set these passwords?

---

