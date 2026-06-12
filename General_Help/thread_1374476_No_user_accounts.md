---
title: "No user accounts?"
date: 2010-01-06
forum: General Help
---

### Post by Nissan_370Z on 2010-01-06
I recently made a computer for someone who decided to get a new one instead.. so i thought i'd make a server out of it lk i had it before. so i deleted their account (while on their account) and made me an account.. but now when i try to login to my account it's.. not there? such as when i type my username and pass it says i entered an invalid user/pass. any idea how i can get my user accounts back or atleast logon to this system? i know the root password if there's any way i can logon under the root account. Thanks!!!

---

### Post by blueridgedog on 2010-01-06
You can try and boot into single user mode.  Here is an example, there are others if you search:

[http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

Once booted in single user mode, you will be logged in as root and can add/edit users from the command line:

```
/usr/sbin/adduser NAME
```

and

```
/usr/bin/passwd NAME
```

---

### Post by Nissan_370Z on 2010-01-06
> **blueridgedog said:**
> You can try and boot into single user mode.  Here is an example, there are others if you search:

[http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

Once booted in single user mode, you will be logged in as root and can add/edit users from the command line:

```
/usr/sbin/adduser NAME
```

and

```
/usr/bin/passwd NAME
```

okay i'll try that.. thank you i really appreciate it!!

---

### Post by Nissan_370Z on 2010-01-06
> **blueridgedog said:**
> You can try and boot into single user mode.  Here is an example, there are others if you search:

[http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

Once booted in single user mode, you will be logged in as root and can add/edit users from the command line:

```
/usr/sbin/adduser NAME
```

and

```
/usr/bin/passwd NAME
```

kk i tried it 3 times but it never went into single boot mode.. it goes right back to the ubuntu logon screen requesting a username.. any ideas? it might be something im doing wrong

---

### Post by Nissan_370Z on 2010-01-07
i found another way to get around that to get to the terminal.. but i did that command and made my account back.. but i'm not an administrator? any help would be appreciated.. thanks!

---

### Post by blueridgedog on 2010-01-07
Add yourself to the admin group...

System - Users Groups, unlock then manage groups...

Then log out and log back in.

---

### Post by michy99 on 2010-01-07
He can't unlock if he isn't in the admin group.

---

### Post by AlexandreP on 2010-01-07
> **Nissan_370Z said:**
> kk i tried it 3 times but it never went into single boot mode.. it goes right back to the ubuntu logon screen requesting a username.. any ideas? it might be something im doing wrong

You can try booting into recovery mode, if this option is available to you at the boot menu. There should be a menu entry *Ubuntu, kernel xxxxxxx **(recovery mode)*** ; select it. It acts the same as the *single* option.

Once you get to another menu, select option *root* to get access to a root shell prompt. Two possibilities:
(1) You get to the root shell / command line. From there, you can execute the two commands Blueridgedog gave you so you can create a new user account. Type *exit* to log off from the root shell, the select option *resume* to resume normal Ubuntu boot.
(2) The other possibility is the previous owner set a root password, so you need to provide the root password in order to log in the root shell. If you are in the case and you know this password, type it in. If not, well... phone your computer's previous owner to get it?

---

### Post by blueridgedog on 2010-01-07
> **michy99 said:**
> He can't unlock if he isn't in the admin group.

Opps.  Sorry.  Boot back into single user mode and 

```
/usr/sbin/useradd -G admin username
```

Where "username" is your account.

---

