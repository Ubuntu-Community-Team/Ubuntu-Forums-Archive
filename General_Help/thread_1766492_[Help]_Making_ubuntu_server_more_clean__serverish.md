---
title: "[Help] Making ubuntu server more clean / serverish"
date: 2011-05-24
forum: General Help
---

### Post by mac666 on 2011-05-24
Hello
I need help to get ubuntu nighty more clean / serverish. 
right now, it pretty hard to vnc to the server since all the desktop / window effects with fade, shadow et c are slowing things up. how to remove these? 

how can i enable ssh access to the server, so that i can telnet / ssh to the server? 

how can i remove the keyring prompt? Right now i cant VNC to the server without unlocking the keyring (localy on the server)

---

### Post by hwttdz on 2011-05-24
Well, you don't even need to have a graphical environment.  Or if you have one you can use one of the lighter weight window managers xfce, openbox, lxde... Or you can use metacity instead of compiz.  

You'll need openssh-server to ssh to your server.  You may also need to enable port forwarding on your router.  

I have no idea what you're talking about with vnc/keyring, I always use ssh.

---

### Post by ph3d on 2011-05-24
1. System -> Administration -> Login screen -> Set Auto login and ubuntu classic (no effects)

2. sudo apt-get install ssh 

3. Go click[B] Applications > Accessories > Passwords and Encryption keys ->

[/B]4. Enter old password, leave new one blank.

Enjoy :)

---

### Post by mac666 on 2011-05-25
Thanks you guys! :-) havent had time to try everything but i hope this works!

<3

---

