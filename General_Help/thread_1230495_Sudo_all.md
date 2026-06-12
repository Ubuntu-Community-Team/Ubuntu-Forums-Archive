---
title: "Sudo all"
date: 2009-08-03
forum: General Help
---

### Post by sethborders on 2009-08-03
is there some sort of sudo command that will cause all later commands to be "sudoed"?  its rather annoying to have to type sudo a bunch of times in a row. if there was some sort of way to enter a sudo "mode" it would make like a whole lot easier

---

### Post by credobyte on 2009-08-03
```
 
sudo -i

```

---

### Post by wojox on 2009-08-03
Read Carefully:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ppirilla on 2009-08-03
**su** or **sudo bash** give you a root shell (though note that you need the root password rather than your user password for the former).  The command prompt changes from ---$ to ---# to remind you that you're root.

type **exit** to exit the root shell and return to your regularly scheduled (non-superuser) computing.

---

### Post by ibuclaw on 2009-08-03
If you want to execute a series of commands in a row, (and they are always the same commands in the same order) why not just put them into a script, ie:
```
gedit myscript.sh
```
Put in everything you want to do, then save and mark it executable:
```
chmod +x myscript.sh
```
and run
```
sudo ./myscript.sh
```
Be careful though, with great power comes great responsibility. ;)

One example of such a script could be the following:
```
#!/bin/bash
apt-get update
apt-get upgrade
apt-get clean
echo "Finished"

```

Regards
Iain

---

### Post by Elfy on 2009-08-03
Let's not have this turn into a root password howto - thank you

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

