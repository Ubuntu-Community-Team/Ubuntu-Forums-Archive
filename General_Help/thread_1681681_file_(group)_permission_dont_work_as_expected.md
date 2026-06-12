---
title: "file (group) permission dont work as expected"
date: 2011-02-04
forum: General Help
---

### Post by Matpen on 2011-02-04
Well, this is a problem that keeps on coming, and I never found a solution:
```

matteo@matteo-laptop:~$ cat /etc/lsb-release 
[...]
DISTRIB_DESCRIPTION="Ubuntu 10.10"
matteo@matteo-laptop:~$ uname -a
Linux matteo-laptop 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux
matteo@matteo-laptop:~$ groups matteo
matteo : matteo adm dialout cdrom plugdev fuse lpadmin admin sambashare
matteo@matteo-laptop:~$ ls -l /etc/fuse.conf 
-rw-r----- 1 root fuse 216 2010-09-27 11:20 /etc/fuse.conf
matteo@matteo-laptop:~$ cat /etc/fuse.conf 
cat: /etc/fuse.conf: Permission denied

```
Maybe it is just me misunderstanding how it should work, but:
1) do you confirm that, as a member of the group "fuse", I should be able to read the file?
2) of course, I could change the permission of the file, or read it as sudo, but sometimes this is not possible. how to achieve it then?

Thank you in advance for any help!

---

### Post by cogier on 2011-02-04
I do not pretend to know the answer to your problem but it would help if you explained in more detail exactly what you are trying to achieve. 

The problem that keeps coming up is when ".........".

I think you will get more help if you explain yourself better.

Best of luck.

---

### Post by coffeecat on 2011-02-04
Edit - posted in error. Didn't read your post closely enough. Sorry.

---

### Post by coffeecat on 2011-02-04
Apologies. Now that I've got my brain in gear...

> **Matpen said:**
> 1) do you confirm that, as a member of the group "fuse", I should be able to read the file?

I agree but I cannot explain why your system is behaving as it is. I am getting the expected behaviour.

```
$ groups
coffeecat adm dialout cdrom plugdev fuse lpadmin admin sambashare
```and

```
$ ls -l /etc/fuse*
-rw-r----- 1 root fuse 216 2010-10-15 01:48 /etc/fuse.conf
```and

```
$ cat /etc/fuse.conf
# Set the maximum number of FUSE mounts allowed to non-root users.
# The default is 1000.
#
#mount_max = 1000

# Allow non-root users to specify the 'allow_other' or 'allow_root'
# mount options.
#
#user_allow_other
```Puzzling.

---

### Post by Rocket2DMn on 2011-02-04
Did you just recently add yourself to that group?  You will need to logout and log back in for the group changes to take effect on your user.

---

### Post by Matpen on 2011-02-05
> **Rocket2DMn said:**
> Did you just recently add yourself to that group?  You will need to logout and log back in for the group changes to take effect on your user.
THAT was it!

You indeed have to log out, and then back in. It is not enough to just close the terminal and start a new one, apparently.

Is there another way to do it quickly (i.e. without logging out)? I had the very same problem once, while trying to make apache understand, that it indeed had the permission to read a directory.

In such a case, the solution is probably to restart apache or what?

Thanks again!

---

### Post by Rocket2DMn on 2011-02-05
Permissions are independent of the applications or files in question, it is strictly a user permission thing.  If you modified permissions for the apache user, the Apache web server would have to be restarted (assuming a root privileged command kicked off apache using the apache user).  If you were logged in with the apache user, a new login would be required before restarting apache.

If you start a new login shell in a terminal, the new privileges should take effect within that shell.  gnome-terminal does not create a new login shell by default, but it can be configured under Edit->Profile Preferences, Title and Command tab.  It may also work if you su with the -l switch:
```
su -l *username*
```

---

### Post by Matpen on 2011-02-06
Thank you for the fantastic support!
> **Rocket2DMn said:**
> If you modified permissions for the apache user, the Apache web server would have to be restarted (assuming a root privileged command kicked off apache using the apache user).
Yes, this is the scenario I was referring to, where apache is started by root on startup or via the start-stop-daemon, and acts as the www-data user.
> **Rocket2DMn said:**
> If you start a new login shell in a terminal, the new privileges should take effect within that shell.  gnome-terminal does not create a new login shell by default, but it can be configured under Edit->Profile Preferences, Title and Command tab.  It may also work if you su with the -l switch.
This is also very interesting, thank you!

---

