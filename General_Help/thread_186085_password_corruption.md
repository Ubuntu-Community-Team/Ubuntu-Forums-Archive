---
title: "password corruption?"
date: 2006-06-01
forum: General Help
---

### Post by xpavement on 2006-06-01
My power went out during the night, and when I went to check out my system, it was at the login screen (it was logged into a gnome session last time I was using it). I attempted to login with my nromal username/password, but it wasn't letting me in. I rebooted into recovery mode and used the passwd utility to change my password. I was then able to login after another reboot into normal mode, but when I tried to login remotely via ssh, the password didn't work. I haven't had time to check out the system completely, but does anyone have suggestions on things to look at? I can still run sudo and the root password is still in tact, just logging in via ssh is the problem. I'm not using any public/private keys or anything to bypass the password prompt for ssh access. TIA.

---

### Post by mscman on 2006-06-01
Do you have a firewall on the system and/or is remote login enabled?   These are two things that can stop ssh dead in its tracks.  The power outage could have (for unknown reasons to me) reset your settings.  Also, (and I know this sounds stupid, but I have to ask) have you been able to remotely login in the past?

---

### Post by dmb on 2006-06-01
Also, remember that root login can be disabled in /etc/ssh/sshd_config . Not sure if thats what your are trying to do though.

---

### Post by xpavement on 2006-06-01
Yes, I have been able to login remotley before, my router is setup to forward port 22 to this specific box. I'm not trying to log in as root, just as the normal user I once had working. Thanks for the help, I still need to take a good look at the box and see if anything else is weird.

---

### Post by xpavement on 2006-06-02
I figured out what the problem was, user error in setting the password, and a keyboard with some non working keys. So when I typed the password on the system itself, it would skip the bad keys in the pass, but remotely, the keys were entered, so I guess I have a broken keyboard, heh.

---

### Post by mscman on 2006-06-02
That's happened to me in the lab I work in before.  At least you were able to figure it out! (keyboards are cheap anyway...)

---

