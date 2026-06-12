---
title: "Lock up at login"
date: 2009-10-23
forum: General Help
---

### Post by EdGy28376 on 2009-10-23
I have lost the ability to login via the GUI. I can type my login name and after pushing the enter key the system locks up. This can be validated by the hum lock light. I can login via the recovery console.

This appears to have happened when the system was in the process of updating itself and I disconnected 2 USB devices. 

Any assistance would be greatly appreciated.

---

### Post by P4man on 2009-10-23
quick and dirty possible solution is to create a  new user from the root shell, then try logging in with that account. 

```
adduser testuser
passwd testuser
```

---

### Post by EdGy28376 on 2009-10-23
Ok that seems to work. I have a desktop with nothing on it. Which lends itself to your line of thinking; His [my] user account is corrupt. 

So with this how do I correct it?

Thank you for your time.

---

### Post by EdGy28376 on 2009-10-23
UPDATE- With nothing showing on the desktop. I have verified it seems to be locked up. There is no status change on the NUM lock light when the NUM lock key is taped.

---

### Post by P4man on 2009-10-23
In that case, perhaps try booting an old kernel from grub? 
Can you verify your disk is not full (```
df -h
``` from root terminal)
You can also try booting in recovery mode and running xfix 
and check your logs in /var/log/messages

---

### Post by EdGy28376 on 2009-10-23
Total percentage used is 75% Same result.

I have the following Kernels:
2.6.28-11/15/16/02062904/020630

---

### Post by P4man on 2009-10-23
TBH Im just shooting in the dark here..Well, here is two more I guess:
```
dpkg-reconfigure xserver-xorg
```
```
dpgk --configure -a
```

If that doesnt help you'll have to do some more detective work. boot from a live cd and inspect the log files, verify the harddrive..

---

### Post by EdGy28376 on 2009-10-23
No luck :( 

Where and what log files should I be looking at?

---

### Post by EdGy28376 on 2009-10-23
I am now using the live CD to navigate the file structure. 

Found the following link to assist in troubleshooting:
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by P4man on 2009-10-23
Good. I guess "messages" would be the first one to check. Just make sure you dont confuse the live cd tree with the one on your drive. make sure you are browsing /media/nameofyourdrive/var/log/etcetcet

(media could be mnt too, not too sure)

---

### Post by EdGy28376 on 2009-10-23
It seems something is hosed up with the GUI. I found this error "WARNING: gdm_slave_xio error". 

Ran from the recovery console-
apt-get install rcconf

rcconf

deselected gdm

I can know get to the server via webadmin. 
Now to backup my data, then continue to work through this problem.

---

### Post by EdGy28376 on 2009-10-26
I think I had totally removed X and anything associated with the GUI. Then I reinstalled the GUI piece. However the samething occurs.

I get a GUI login screen and can type my user name. Once I hit enter it freezes up. What log files can I look at? Is there a debug option I can envoke?

---

