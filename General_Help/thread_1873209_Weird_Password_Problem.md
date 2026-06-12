---
title: "Weird Password Problem"
date: 2011-11-01
forum: General Help
---

### Post by frank cox on 2011-11-01
I was playing around with the LXDE desktop in Linuxmint and tried to change the logon settings and somehow managed to change the password. How do I reset it?
I have 3 Ubuntu partitions . 
Thanks

---

### Post by papibe on 2011-11-01
If you know your new password, you can change it in a terminal with the command:
```
passwd
```
Hope it helps,
Regards.

---

### Post by mcduck on 2011-11-01
...and if you don't know the password, but th account you were playing with wasn't your admin account, then log in as the admin, and run "sudo passwd *username*" (replacing the username with the actual username of the account for which you need to change the password).

Finally, if it was your admin account, you'll need to boot into recovery mode (it's selectable from Grub menu, hold Shift while booting if the menu is hidden by default on your system). Then, when asked what you want to do, select the option for a root shell. Once there you can run "passwd *username*" to change the account's password. (once again with the correct user name, of course). When done, run "reboot" to restart the computer to get back to normal mode.

---

### Post by frank cox on 2011-11-02
Thanks!
I forgot to tell it to notify me you responded. I still wish I knew what I did. Somehow in the process of trying to make Linuxmint LXDE login automatically like I had it setup with the Gnome desktop I thought  wiped out the root password. Turns out I managed to change the user name.
Now that you reminded me I realise why my efforts to change it failed, thanks again.

---

### Post by frank cox on 2011-11-02
I spoke to soon. it worked at first but after the first reboot it seems to have lost my username . I can log in but I cannot get to my desktop or my files. I had to use sudo to open firefox.

What I need to do is change the computer name and get my old username working .

Any advice would be appreciated.

---

