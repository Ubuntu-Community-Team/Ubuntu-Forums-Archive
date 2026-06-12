---
title: "permissions"
date: 2011-02-20
forum: General Help
---

### Post by puding69 on 2011-02-20
I hate ubuntu because EVERYTHING i need a permission. How can i edit an stupid file? Said i have no permission. **** IM THE ADMINISTRATOR, HOW CAN I HAVE TOTAL CONTROL ON MY COMPUTER -.-' ?

---

### Post by Syed75 on 2011-02-20
Log in as root. But that'd be a mistake.

---

### Post by puding69 on 2011-02-20
And how can i do that? I have tried to login as root, but nothing happens.

---

### Post by Syed75 on 2011-02-20
What version do you have?

---

### Post by Syed75 on 2011-02-20
[http://www.ubuntugeek.com/how-to-disable-password-prompts-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-password-prompts-in-ubuntu.html)

Check this out.

---

### Post by puding69 on 2011-02-20
Ubuntu 10.10

[http://www.ubuntugeek.com/how-to-disable-password-prompts-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-password-prompts-in-ubuntu.html) doesnt work for me. Keep saying im not the owner and i cant edit the file.

---

### Post by Syed75 on 2011-02-20
sudo passwd root

It's dangerous to go root. 

[http://blog.sudobits.com/2010/10/19/how-to-login-as-root-in-ubuntu-10-10/](http://blog.sudobits.com/2010/10/19/how-to-login-as-root-in-ubuntu-10-10/)

But go root then edit that file and then undo root.

---

### Post by puding69 on 2011-02-20
Thanks! Its working.:D

---

### Post by jiminoregon on 2011-02-20
I feel your pain.  Recently asked for help and this helped me. Hope it helps you.

	Nullifying login for admin stuff:


To disable password protected screensaver:

System -> Preference -> Screensaver
Uncheck "Lock screen when screensaver is active".

To disable password protected login:
System -> Administration -> Login Screen
"Unlock" the window, then select the user you want to log in as automatically.

OR
System -> Administration -> Users and Groups
Click "Advanced Settings", highlight your user account, next to password click "Change". Check the box that says, "Don't ask for password on login".

This may cause issues with your encrypted passwords so you may have to go clear the password or set up unencrypted storage of passwords.

To disable password protection for executing administrative tasks: (NOT RECOMMENDED)
Edit /etc/sudoers with:
Code:
sudo gedit /etc/sudoers
Scroll down until you see:
root ALL=(ALL) ALL

Enter a new line below that and enter the following:
username ALL = NOPASSWD: ALL

Where username is your username. Reboot your computer and you should be able to execute root commands without prompting. However please note that this is VERY dangerous, as in Windows XP virus dangerous. If you happen to contract some funky malware it would have full rights to execute any command as root without prompting you. There are other ways to make it a little easier, you can google sudoers for more information.
_

---

### Post by Syed75 on 2011-02-20
> **puding69 said:**
> Thanks! Its working.:D

No prob.

---

### Post by bronquel on 2011-02-20
jiminoregon - fascinating!  never knew you could do that.

puding69 - I'd be careful running everything as root - as jiminoregon said, you do drop your security level down.  sudo is the recommended method - what vista was trying to mimic with its user account control.  Ubuntu does take some getting used to, but then again you switched from your olf OS to ubuntu for a reason, right?

PS - remember to mark the tread as solved!

---

