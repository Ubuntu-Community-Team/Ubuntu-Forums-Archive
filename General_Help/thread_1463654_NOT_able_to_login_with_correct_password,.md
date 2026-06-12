---
title: "NOT able to login with correct password,"
date: 2010-04-27
forum: General Help
---

### Post by rashid.alavi on 2010-04-27
HI Everybody,

This is Mohamed here,

here i face strange problems,

i am not able to login to ubuntu with the existing password, what is happening is once i gave password it is taking and after few seconds , getting the prompt again to login.but am not getting any authentication failure, infact i tried with wrong password it is giving authentication failure message


any help would be really appreciated

---

### Post by StuartN on 2010-04-27
> **rashid.alavi said:**
> i am not able to login to ubuntu with the existing password

If you reboot the machine and select "recovery mode" from the boot menu, then you will be taken to a root console. Type "passwd mohamed" to reset your password.

Full instructions [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by rashid.alavi on 2010-04-27
i did change the password , and i tried with new password as well, but no way out,
 
let me explain here again,
 
after giving the password , it is taking , coming back with prompt asking me to login again, but it is not giving any password failure or so, but when i give wrong password it is giving authentication failure as well.
 
thanks your reply Start.
 
any idea why it is happening?
 
do we need to change or check anything in system level

---

### Post by klemes on 2010-04-27
It would be wise to check all of your ~/.* files and see if the have correct permissions and ownership.

```
ls -al /home/your_username
```

Also have a look in the gdm.log located in the /var/log directory.:popcorn:

---

### Post by warfacegod on 2010-04-27
Can you log in as root? Go into Recovery mode> get a command prompt> type startx> hit Enter. If that works, see if you can change your password from there and be very careful with what you do. Using your system as root can be very dangerous.

---

### Post by dabl on 2010-04-27
"login loop" can be caused by:

- filesystem full.  Check it with du -h

- root permissions on ~.Xauthority and ~.ICEauthority files (caused by running X applications as root -- a no-no).  After you boot Recovery Mode, you can delete those two files.  Then reboot and login normally.

---

### Post by cdenley on 2010-04-27
In recovery mode, where you reset your password as StuartN suggested, run these commands, and post the output here.
```

lsb_release -r
getent passwd 1000
tail /var/log/auth.log
cat /var/log/gdm/:0-slave.log
tail /var/log/gdm/:0.log

```

---

### Post by rashid.alavi on 2010-04-27
thank for replying all,

i found the problem. it is related to .profile file which changed last time, system was not able to recognise as well ,

---

