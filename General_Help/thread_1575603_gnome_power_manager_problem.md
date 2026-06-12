---
title: "gnome power manager problem"
date: 2010-09-16
forum: General Help
---

### Post by bboyshane on 2010-09-16
I am not able to log in and get the following message :

Install Problem
the configuration defaults for gnome power manager have not been installed correctly.
Please contact your system administrator.

I have tried apt to remove sand reinstall with no success. 
Can anyone suggest a solution? I am running lucid 10 04

thanks

---

### Post by utnubuuser on 2010-09-16
In recovery mode, (line beneath the default kernel in grub-menu), you might find an option to "fix-broken" (not sure for 10.04 - haven't used recovery in quite some time).

Or, from the recovery console, (with networking), try:> sudo apt-get install --reinstall gnome-power-manager

---

### Post by bboyshane on 2010-09-16
apt-get reinstall did not work, if you had read my post, I indicated I had tried that to no avail.

Does anyone have any further ideas on possible solutions?

thanks in advance

---

### Post by sikander3786 on 2010-09-16
Hit Ctrl + Alt + F1 at you login screen. Log in using your credentials and try,

```

sudo apt-get clean

```

```

sudo apt-get update

```

```

sudo apt-get install -f

```

And if that doesn't fix the problem, try,

```

sudo dpkg --configure -a

```

Post back any error messages encountered during the process.

---

### Post by bboyshane on 2010-09-17
thanks for the suggestions sikander3786, but I am still getting the same error, and unable to log in. No error messages other than the initial message.

thanks..... any other ideas anyone?

---

### Post by sikander3786 on 2010-09-18
In the end, reinstalling the whole desktop might help. But you may want to wait for some other replies also.

```

sudo apt-get --reinstall install ubuntu-desktop

```

Also I have seen some threades stating that the problem was because there was very little space left on some partitions. See the following link.

[http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/](http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/)

---

