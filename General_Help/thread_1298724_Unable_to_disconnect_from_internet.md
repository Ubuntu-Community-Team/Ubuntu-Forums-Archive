---
title: "Unable to disconnect from internet"
date: 2009-10-23
forum: General Help
---

### Post by anaconda on 2009-10-23
I have a huawei 3G modem e220, and if I make the internet connection using network manager, I am unable to disconnect once the connection is made.

(of course I can always unplug the modem physically)

Selecting disconnect from network manager doesnt do anything. 

I have partially solved this problem by using gnome-ppp, which can connect and disconnect, but it has its own problems. (gnome-ppp doesn't work very well with network manager.

Of course I could uninstall network manager, but lets try first to fix it.

Any ideas how to force disconnect?

---

### Post by swoody on 2009-10-23
Out of curiosity, which version of Ubuntu are you running?

Maybe this could be of use for you :)
[https://help.ubuntu.com/8.10/internet/C/networking-disable.html](https://help.ubuntu.com/8.10/internet/C/networking-disable.html)

---

### Post by anaconda on 2009-10-23
> **swoody said:**
> Out of curiosity, which version of Ubuntu are you running?

Maybe this could be of use for you :)
[https://help.ubuntu.com/8.10/internet/C/networking-disable.html](https://help.ubuntu.com/8.10/internet/C/networking-disable.html)

Oops!  Forgot to mention.
On that machine I have 9.04.

I will try the things from the link.
Thanks.

---

### Post by Anonymousable on 2009-10-23
Or, to keep it simple, you can right-click > uncheck "Enable Networking"

---

### Post by t0p on 2009-10-23
> **Anonymousable said:**
> Or, to keep it simple, you can right-click > uncheck "Enable Networking"

Indeed.  I have the precise same problem with a Huawei E160X.  I "fix" it by unchecking "Enable Networking" or, if I need network manager to remain on, I yank out the modem's extension lead.  Not very elegant, but it works for me.

---

### Post by OpenGuard on 2009-10-23
```
sudo ifconfig wlan0 down

```

---

### Post by Anonymousable on 2009-10-23
> **OpenGuard said:**
> ```
sudo ifconfig wlan0 down

```
Only if you enjoy command-line solutions. ;)

---

### Post by kanikilu on 2009-10-23
> **Anonymousable said:**
> Only if you enjoy command-line solutions. ;) True, but you can make keyboard shortcuts out of it. This is actually what I do on my netbook to save power:

- System -> Preferences -> Keyboard Shortcuts

- Add two new actions:
(use ifconfig beforehand to find the name of the adapter you have, mine is actually ath0)

Name: wlan0 up
Command: sudo ifconfig wlan0 up

Name: wlan0 down
Command: sudo ifconfig wlan0 down

- Give these two new actions keyboard shortcuts, I set mine to Super/Win+Up Arrow and Super/Win+Down Arrow.

The only catch is you have to edit your sudoers file to not require a password for the ifconfig command. This may not be desirable in all cases, but I just added the following to /etc/sudoers:

```
%admin ALL=(ALL) NOPASSWD: /sbin/ifconfig
```

Be careful editing the file, for more information, see the docs:

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by swoody on 2009-10-23
> **Anonymousable said:**
> Only if you enjoy command-line solutions. ;)

Who *doesn't* enjoy using the command line? ;)

---

### Post by OpenGuard on 2009-10-23
> **Anonymousable said:**
> Only if you enjoy command-line solutions. ;)

Everything runs based on a command - once you know it, you can use it ( hotkey, shortcut, custom launcher in C/C++, etc. ).

---

