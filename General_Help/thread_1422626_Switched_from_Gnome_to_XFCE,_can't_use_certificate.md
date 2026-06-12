---
title: "Switched from Gnome to XFCE, can't use certificate login to ssh"
date: 2010-03-05
forum: General Help
---

### Post by charonn0 on 2010-03-05
So I installed xubuntu-desktop and have been using XFCE as my desktop and everything's groovy except for one thing.

In Gnome, I created a certificate in order to allow me to login to my web host over SSH without requiring the SSH password (which is very long and complex, for good reason). It worked fine under Gnome but now in XFCE when I attempt to SSH to the server, my keyring password is not recognized.

```
andrew@guardian:~$ ssh <hostname of server>
Enter passphrase for key '/home/user/.ssh/id_dsa': 
Enter passphrase for key '/home/user/.ssh/id_dsa': 
Enter passphrase for key '/home/user/.ssh/id_dsa': 
*****@*******.net's password:
```
(Note: I redacted the server name and username.)

A few weeks before switching to XFCE I changed my local username from *user* to *andrew*, which is why my home directory is called user, but it didn't break the keyring in Gnome.

How can I fix this? The certificate still works properly in PuTTY under Windows, so it's not the cert.

Edit: Using (X)Ubuntu Karmic.

---

### Post by pbrane on 2010-03-05
Have a look at this:
[http://www.xfce.org/documentation/4.2/manuals/xfce4-session]("http://www.xfce.org/documentation/4.2/manuals/xfce4-session")

You might need to run the GNOME keyring daemon. It's an option under Advanced preferences.

---

### Post by charonn0 on 2010-03-05
Thanks for the suggestion, but the gnome-keyring-manager is already running:

```
andrew@guargian:~$ ps aux|grep -v grep|grep keyring
andrew    2560  0.0  0.1  15996  2440 ?        Sl   19:37   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
andrew@guardian:~$ 

```

---

### Post by pbrane on 2010-03-06
Sorry, I would have thought that was it. I used XFCE a month ago and was able to login to my server using keys then. I've since removed XFCE though. If I come across anything I'll post back.

---

