---
title: "Can't Log In any accounts, gets back to log in screen"
date: 2012-01-16
forum: General Help
---

### Post by belkinsa on 2012-01-16
I was working on getting Samba to have the shares working the way that I  want them via the GUI program (forgot what it was).  I was in root and I  think I have deleted some important folders while trying to get it  work. After I closed out of it, I needed to restart.  After I restarted  and wanted to log in into my account.  I found it coming back to the log  in screen.  I have tried many times and even with the "guest" account  and I keep on getting the same problem.

---

### Post by maverickaddicted on 2012-01-17
I also faced this problem in one of my desktop machines, but the problem came after updating the system. I haven't deleted anything. Just give a try to this, if it works or not.

I logged in my admin account using TTY terminal (CTL + ALT + F1). Before doing anything, I first ran this command-
```
sudo fsck -y /
```
Since it was doing disk checking in each restart. After that I rebooted my system. Then I again try to login into my account and it was successful.

There was one more problem I faced related to login process on other machine, which was not allowing me to enter password. That time, I logged in to TTY terminal and reinstalled the Gnome Display manager.

```
sudo apt-get --purge remove gdm
``` 
```
sudo apt-get install gdm
```
Reboot the machine or run directly
```
sudo service gdm start
```

I don't know if it is a good solution.

---

### Post by belkinsa on 2012-01-17
How to log into the admin account?  Or is it the account that you have the admin power too?

---

### Post by maverickaddicted on 2012-01-19
I was having admin account details. When you press CTL + ALT + F1 in the login screen. It goes to the TTY terminal screen where it asks for the username and password. You have to provide the root or admin account login credentials. OR you can login with normal user and can use "su <adminuser>" command to login to admin account.

---

### Post by belkinsa on 2012-01-19
I see.  Thanks for the help and I will try this this weekend.  If doesn't work, I will post what happened that made it to fail.

---

