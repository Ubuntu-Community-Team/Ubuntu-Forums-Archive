---
title: "No unity"
date: 2012-10-01
forum: General Help
---

### Post by adduds on 2012-10-01
I don't have any unity no side bar or top bar

To get unity I have to 

```
unity --replace
```

I've tried this

```


sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity

```

and basically I just run firefox from terminal as of right now

Any help would be appreciated. Thanks

---

### Post by Frogs Hair on 2012-10-01
You can try unity reset from tty. 

Login to Ubuntu use Ctrl + Alt + F1 to enter TTY. Next enter user name, password, and run the following command.

Code:
unity --reset

Wait until the process is complete and your user name appears again. Use Ctrl + Alt + F7 to renter the desktop environment.

If there is error reporting wait until finished. If Unity doesn't appear within a minute or two restart and login to Ubuntu.

---

