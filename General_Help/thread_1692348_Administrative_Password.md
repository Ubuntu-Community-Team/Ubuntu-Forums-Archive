---
title: "Administrative Password"
date: 2011-02-21
forum: General Help
---

### Post by eipapp on 2011-02-21
I'm installing a printer and in the process it's asking me for an administrative password to continue the installation. I type in the only password I always use but it says it is incorrect. What am I missing ???

Regards,
Bruce

---

### Post by Grenage on 2011-02-21
> **eipapp said:**
> What am I missing ???

Probably the right password; sorry, I couldn't resist.

The admin password will be your normal password.  Do you have more than one account on the machine?

---

### Post by eipapp on 2011-02-21
No I only use one.
Is there a setting I can change or something because I'm at a stalemate with this password thing.

thanks for your reply............

---

### Post by Grenage on 2011-02-21
Hi there,

As a curious test, can you run this from a terminal?

```
gksu gedit
```

When it asks for your password, is it accepted?

---

### Post by eipapp on 2011-02-21
Yes, it was.

---

### Post by sisco311 on 2011-02-21
In Ubuntu, by default, the root account password is disabled. You have to use sudo/gksu to run applications as root. Some printer drivers are not designed for Ubuntu and if you run them as a non-root user, they prompt you for the root password. As a workaround, you have to run the installer as root:
```
sudo -i /path/to/installer
```

See: [uhelp]community/RootSudo[/uhelp]

---

### Post by eipapp on 2011-02-21
Did as you said & got the message "no such file or directory"

---

### Post by sisco311 on 2011-02-21
> **eipapp said:**
> Did as you said & got the message "no such file or directory"

You have to replace /path/to/installer with the actual path to the file. If you don't want to type in the path manually, just type **sudo -i**, then a space, drag the file in the terminal window and press enter.

---

### Post by eipapp on 2011-02-21
Did as you said and it worked just like it's supposed to "until" I got to the part that said I need root privileges and to enter my administrative password and I found myself back at square one again.
It just won't accept my password.......... boy this is frustrating !!!!

---

### Post by eipapp on 2011-02-23
Success !!!
Went into Terminal and typed in Sudo passwd root. It then asked me for a root password which I did.
I then proceeded to install printer again and when it asked for root password I gave it and it took.
Printer is now installed and working.

---

