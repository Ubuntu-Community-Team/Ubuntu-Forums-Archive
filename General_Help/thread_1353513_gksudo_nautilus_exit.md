---
title: "gksudo nautilus exit"
date: 2009-12-12
forum: General Help
---

### Post by tsucol11 on 2009-12-12
I am using ubuntu 9.04 64 bit

Using gksudo nautilus + password I am able to manage my file systems as root (multiple users), everything works fine.

Problem occurs when I want to leave Nautilus. I close Nautilus using File/close and get the following error in the terminal "(nautilus:6746): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time" (or other similar errors). I then either type Exit in the terminal or click on the X and the terminal closes.

Problem is that if I retype gksudo Nautilus in a new terminal it no longer asks for my password, it goes directly to root. The only secure way is to reboot the system.

[COLOR="Red"]Are there any settings to force gksudo Nautilus to always request the password?[/COLOR]

I don't remember having this problem in the past.

Thank you

Brian

---

### Post by NoaHall on 2009-12-12
Sudo remembers your password for about 15 minutes. Try leaving it for about 20 minutes and try.

---

### Post by tsucol11 on 2009-12-12
> **NoaHall said:**
> Sudo remembers your password for about 15 minutes. Try leaving it for about 20 minutes and try.

This causes security issues, as the computer is shared. I need to know that when I leave Nautilus as root no one else has access .

Thanks for the quick reply

Brian

---

### Post by kaibob on 2009-12-12
> **tsucol11 said:**
> Are there any settings to force gksudo Nautilus to always request the password?

I've never done it, but you could change the passwd_timeout option to zero in the sudoers file.

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

You need to be careful when editing the sudoers file:

[http://ubuntuforums.org/showthread.php?t=229309](http://ubuntuforums.org/showthread.php?t=229309)

---

### Post by NoaHall on 2009-12-12
> **tsucol11 said:**
> This causes security issues, as the computer is shared. I need to know that when I leave Nautilus as root no one else has access .

Thanks for the quick reply

Brian

Try gksudo -K nautilus

---

### Post by tsucol11 on 2009-12-21
Thanks to all who responded. I was away on business and could only respond today.
NoaHall & kaibob I will check into your suggestions asap.

Thanks
Brian

---

### Post by tsucol11 on 2009-12-27
After reading various info given, this is the process I used:

1- changed the permission of etc/sudoers to read & write (from read only)
2- added to the default line in sudoers the line->  timestamp_timeout=0
     Complete line in etc/sudoers looks like-- > 
     Defaults env_reset,timestamp_timeout=0
3-changed the permission of etc/sudoers to read only (from read & write).

So far working great. Used Gedit as text editor.

Brian

---

