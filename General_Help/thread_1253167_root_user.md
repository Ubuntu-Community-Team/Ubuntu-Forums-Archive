---
title: "root user"
date: 2009-08-29
forum: General Help
---

### Post by eewoz on 2009-08-29
I just got my installation of Ubuntu running.  During the install I did not remember specifying a password for the root user.  I am trying to become the root user by using the su command in a terminal.  Is there a default password for the root user?

---

### Post by scouser73 on 2009-08-29
To become root, please go to **Terminal** & use the command: **gksudo nautilus**

Please be extremely careful when using root.

---

### Post by wojox on 2009-08-29
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2009-08-29
The root account is disabled for login in Ubuntu by default.

If you want a root file browser, make a launcher or keyboard shortcut for the command ```
gksudo nautilus
```

If you want to execute a single terminal command as root, just preface it with *sudo*. For example: ```
sudo apt-get update
```

If you want a persistent root prompt, use the command ```
sudo -i
``` With both *sudo* and *gksudo*, when prompted, enter your **user** password.

---

### Post by aysiu on 2009-08-29
The root account is disabled for login in Ubuntu by default.

If you want a root file browser, make a launcher or keyboard shortcut for the command ```
gksudo nautilus
```

If you want to execute a single terminal command as root, just preface it with *sudo*. For example: ```
sudo apt-get update
```

If you want a persistent root prompt, use the command ```
sudo -i
``` With both *sudo* and *gksudo*, when prompted, enter your **user** password.

---

### Post by phantasmik on 2009-08-29
This is probably the answer you are looking for.

Like you, I also prefer to use su do what I need to do and then exit instead of using sudo (guess its a habit I can't break from other distros)

to set the password all you gotta do is:

```
sudo passwd root
```
It'll ask you for you're password first, then prompt you to set the root password, after it says passwd: password updated successfully
you can now use the command ```
su
```and become root.

I'm sure all the long time users are going to warn against this though after this is posted, so just be careful what you do in root

---

### Post by eewoz on 2009-08-30
Thank you guys.  This has been helpful.  I have successfully used ```
gksudo nautilus
``` by opening a new terminal and then closing the resulting file browser window and the terminal window when I am done.  

Is it possible to invoke ```
sudo -i
``` or ```
gksudo nautilus
``` in a terminal and then switch back to being the normal user without closing the terminal?

---

### Post by aysiu on 2009-08-30
Well, with ```
gksudo nautilus
``` you just have to close the file browser window with your mouse.

With ```
sudo -i
``` type ```
exit
``` to get back to a normal terminal prompt.

---

### Post by aysiu on 2009-08-30
Well, with ```
gksudo nautilus
``` you just have to close the file browser window with your mouse.

With ```
sudo -i
``` type ```
exit
``` to get back to a normal terminal prompt.

---

