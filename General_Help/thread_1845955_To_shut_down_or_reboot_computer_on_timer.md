---
title: "To shut down or reboot computer on timer"
date: 2011-09-18
forum: General Help
---

### Post by shantiq on 2011-09-18
Many of you know this stuff but others do not so here


first so you do not have to enter password each time


```
sudo gedit /etc/sudoers

```

then  add both lines at bottom of document and save

```
#includedir /etc/sudoers.d
username ALL=NOPASSWD: /sbin/halt
```

```
#includedir /etc/sudoers.d
username ALL=NOPASSWD: /sbin/shutdown
```


=============================================


**NOW** you can enter ```
sudo halt
```to turn off computer
or ```
sudo reboot
``` to reboot


============================================

**But** the good stuff is using the timer


```
sudo shutdown -h 08:48
```    will shut you down at 8:48
```
sudo shutdown -r 18:49 
```   will reboot you at 18:49


Further options found with ```
shutdown --help
```


===========================================


It means you start a download & ask your computer to shutdown 3 hours later for example

---

### Post by ajgreeny on 2011-09-18
There is no need to edit the sudoers file to do any of that.  Just issue those commands, eg ```
sudo shutdown -h 08:25
``` enter password when needed, then minimise the terminal, and shutdown will happen at 8:25, just as in your example.  You can even set up launchers for "application run in terminal" on your desktop if you want to.

Note also that to enter a time in the 24 hr time system you do not need the + that you have added; that is used for a shutdown/reboot at the current time +# minutes, not the specific time you show, though it does not seem to cause a problem if the + is also used.

I don't see why having to enter a password for this is such a problem.

---

### Post by shantiq on 2011-09-18
thanx for input greeny
was not aware of the + not being needed   
will modify in post above



as regards the password well it is mostly if one manipulates this stuff ** in a script** there is no request for password.   

see example **[here]("http://ubuntuforums.org/showpost.php?p=11260525&postcount=7")** where one would be asked for password if this was not set up and task would therefore not  be completed

---

