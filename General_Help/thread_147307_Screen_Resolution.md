---
title: "Screen Resolution"
date: 2006-03-19
forum: General Help
---

### Post by castusalbuscor on 2006-03-19
I installed Ubuntu on my Dell Inspiron 1100, all was perfect, including the dual boot.

**BUT** the screen resolution is on the smallest possible scale 640X480, I tried to change it from the screen resoultion setting but alas I had one setting on there and it was 640X480.

I thought I made a mistake while installing Ubuntu so I reinstalled it the next day, but the problem remained...

I know my BIOS is up to date as I installed the new BIOS a couple of months back.


Any idea what the problem could be?

---

### Post by henriquemaia on 2006-03-19
Try this:

open a terminal and there type:
```

sudo dpkg-reconfigure xserver-xorg
```

Follow the steps you get there. In the end of it, restart your X (CTRL+ALT+Backspace).

---

### Post by IYY on 2006-03-20
Yes, do that and if it doesn't work you'll need to manually edit /etc/X11/xorg.conf and add the resolution you want.

---

### Post by castusalbuscor on 2006-03-20
Thanks henriquemaia for the help, sadly it didnt work...

Ivy, inorder to change the xorg.conf file I need to be in root and when installing Ubuntu I was not prompted to enter a root password, and I dont think I know the default password for the root account.

Any idea?

---

### Post by MJSOnline on 2006-03-20
Have you just tried pressing enter at the password prompt?  Or "ubuntu" ? M

---

### Post by MichaelZ on 2006-03-20
[quote=castusalbuscor]Thanks henriquemaia for the help, sadly it didnt work...

Ivy, inorder to change the xorg.conf file I need to be in root and when installing Ubuntu I was not prompted to enter a root password, and I dont think I know the default password for the root account.

Any idea?[/quote] 
Hello,

Have a look here:

[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

Best wishes,
Michael

---

### Post by castusalbuscor on 2006-03-20
[QUOTE=MJSOnline]Have you just tried pressing enter at the password prompt?  Or "ubuntu" ? M[/QUOTE]

I tried Ubuntu, and my FirstName FamilyName, FirstName, FirstNameFamilyName... I havent tried enter.

MichaelZ I will attempt to try it again... otherwise I must call in reinforcements

I will attempt to do so.

---

### Post by MichaelZ on 2006-03-20
[quote=castusalbuscor]
MichaelZ I will attempt to try it again... otherwise I must call in reinforcements
[/quote] 
Did you create/modify a root password?

As root password I use the password of the first user account (mine :)) created when installing ubuntu the first time. E.g.: first user account create when installing ubuntu:

username: **myUsername**
password: **myPassword**

I login with **myUsername** and **myPassword**.

When I use sudo and ask me for the password, I just give **myPassword**

Best wishes,
Michael

---

### Post by IYY on 2006-03-20
You should have entered your root password during installation. It's the same one as the password of the first user you added to your system. You can't "log in as root", but you can use "sudo" to execute commands in root mode, or "sudo bash" to enter a root shell.

For example, if you want to edit xorg.conf as root, type sudo nano **/etc/X11/xorg.conf**.

---

### Post by test on 2006-05-28
[http://www.ubuntuforums.org/showthread.php?t=183285]("http://www.ubuntuforums.org/showthread.php?t=183285")

---

