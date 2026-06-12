---
title: "Admin functions not working"
date: 2006-04-22
forum: General Help
---

### Post by vulpeso on 2006-04-22
I decided to wipe the drive removing a winblows partion and do a fresh install of Breezy. With the new install, none of the Admin functions works. When I try to invoke one, I am prompted for root password and I get a "starting..." icon on the task bar with a waiting cursor. Then both go away and nothin' happens.

When I try with the terminal using sudo, same thing; prompted for password, then just returned to the command prompt. No error but the command doesn't execute.

I'm about to try another re-install, but thought I'd run it by y'all first. Any ideas what might be wrong?

---

### Post by Qrk on 2006-04-22
[QUOTE=vulpeso]
When I try with the terminal using sudo, same thing; prompted for password, then just returned to the command prompt. No error but the command doesn't execute.
[/QUOTE]

Its possible you don't have any problem at all, at least with sudo. These symptoms are the same if you just use the wrong password. You said it prompts you for the "root" password, but sudo actually prompts you for you user password. Also, many people have been confused by the fact your password isn't shown on the screen with sudo... not even blank characters, ****.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by vulpeso on 2006-04-22
With regard to the sudo password, I have set root and user to the same password, anyway. But thanks for the info. I had assumed that sudo was prompting for root password.

---

### Post by xenmax on 2006-04-22
[QUOTE=vulpeso]With regard to the sudo password, I have set root and user to the same password, anyway.[/QUOTE]Seems like you have root account enabled, did you enable the root account yourself or did you do an expert install?

---

### Post by vulpeso on 2006-04-22
I did an expert install.

I just completed a re-install using default mode. Now everything is working correctly.

Easily importing the old home folder with all my data and email from my other machine (a winblows 9x box) is one of the things I really like about Linux systems. :-D

---

### Post by xenmax on 2006-04-22
I would have give you this link if you said yes for expert install.
[http://www.ubuntuforums.org/showthread.php?t=146859](http://www.ubuntuforums.org/showthread.php?t=146859)
Anyway, i think re-install with normal mode is probably a better solution for problem. :)

---

### Post by vulpeso on 2006-04-22
[QUOTE=xenmax]I would have give you this link if you said yes for expert install.
[http://www.ubuntuforums.org/showthread.php?t=146859](http://www.ubuntuforums.org/showthread.php?t=146859)
Anyway, i think re-install with normal mode is probably a better solution for problem. :)[/QUOTE]

Still good info. Thanks.

---

