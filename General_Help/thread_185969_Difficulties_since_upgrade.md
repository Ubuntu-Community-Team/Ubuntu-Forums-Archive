---
title: "Difficulties since upgrade"
date: 2006-06-01
forum: General Help
---

### Post by Freddie.Ruddick on 2006-06-01
Hi all,

I dist-upgraded from Breezy to Dapper this morning. During the installation, it asked something about a login file, something like:

"The login file has been modified (either by you or by a script). Would you like to kepe your version (Default) or use the installation version."

Not understanding it, I accepted the default (keep my version) and the install continued. After it finished, it rebooted to the GNOME login screen. 

I entered my username and password. It didn't make any noises, just went a blank brown screen with a mouse cursor on it. When I first got Ubuntu, I added a keyboard shortcut to gnometerminal, with this, I could open a terminal. I tried a sudo apt-get update, which returned ```
Dpkg was interrrupted, you may want to manually run dpkg --configure -a
```, which I did. This seems to have fixed the problem, as gnome-panel et al now launch correctly at logon.

However, I still have a problem. If I try to log on via CTRL-ALT-F1, after I enter my username, it returns:```
configuration error - unknown item 'QUOTAS_ENAB' (notify administrator)
configuration error - unknown item 'NOLOGIN_STR' (notify administrator)
configuration error - unknown item 'ENV_HZ' (notify administrator)
configuration error - unknown item 'CHFN_AUTH' (notify administrator)
configuration error - unknown item 'CLOSE_SESSIONS' (notify administrator)
```
before prompting for my password. Other than that, the terminal seems to work correctly, am I right to be worried by these messages?

Thanks,

Freddie

---

### Post by Ramses de Norre on 2006-06-01
I've got the same errors but I haven't found a solution for it yet. I've got them since beta 2 and they didn't cause any problems I noticed yet. So don't worry about it=) Maybe someone will find a fix.

---

### Post by Freddie.Ruddick on 2006-06-01
OK, thanks

---

### Post by Aeon17x on 2006-06-16
I'm also getting the same errors when logging in from tty1-tty6. I could still do sudo tasks and I haven't noticed anything odd, I just find it annoying that everytime I try to log in the configuration errors show up.

---

### Post by WildPenguin on 2006-06-16
This is likely to be caused by a problem with the configuration used in /etc/login.defs. To fix the problem, you should need only to comment-out the lines causing the errors.

---

### Post by miniluvr on 2006-06-23
[QUOTE=WildPenguin]This is likely to be caused by a problem with the configuration used in /etc/login.defs. To fix the problem, you should need only to comment-out the lines causing the errors.[/QUOTE]
Great -- that worked for me!

Thanks!

---

### Post by Ramses de Norre on 2006-06-23
A more safe way I found on the gentoo forums is this: ```
sudo mv /etc/login.defs /etc/login.defs.bak
sudo cp /etc/login.defs.dpkg-dist /etc/login.defs
```

---

