---
title: "keyring breaks vnc"
date: 2010-11-20
forum: General Help
---

### Post by Cue2 on 2010-11-20
I can't remotely access my desktop when the desktop is asking for a keyring password. Why does this happen? it means that remote access is useless because you would need to enter the password locally before you can vnc to it. I do not wish to disable the default keyring but is there a way of making vnc work so I can enter the password.

---

### Post by forestG on 2010-12-02
do you mean to connect to vnc before you login? I do not think that is possible. Because in vnc you do not login as a user exactly.It is an application which just allows an already logged in user to use his desktop remotely. You have to already be logged in for the vnc to work. So you just log in and then leave your computer on.  An alternative is to log in and the lock the screen. you can unlock it remotely,

Moreover you must configure the startup applications so that vnc server should run automatically each time you login (system->preferences->startup applications).

and one more thing. If the network connection works before the log in (I really doubt it) you can login through ssh and start the whole procedure and then connect through vnc.

---

### Post by Cue2 on 2010-12-03
Hi forestG, thanks for the reply. I have automatic login. The problem is that after the auto login it sometimes asks for a keyring password. This is especially true if for example you have both a wired and wireless connection. it will ask this so that you do not have to type the WPA or WEP key each time. Even though the wired connection is fine I cannot use vnc remotely until this keyring password is entered locally. As long as there is a keyring password request, for whatever reason, I cannot connect via vnc. I can connect via ssh but I do not know how to unlock the keyring for that gnome session through ssh. How do I do that?

---

### Post by Cue2 on 2010-12-09
I just found this bug. From 2007!  Is this bug still around and does nobody else have this problem?
[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/130545](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/130545)

---

### Post by CharlesA on 2010-12-09
Did you change yer password recently, or is your keyring password not the same as your user's password?

---

### Post by Cue2 on 2010-12-09
> **CharlesA said:**
> Did you change yer password recently, or is your keyring password not the same as your user's password?

I haven't changed my password recently but I did reinstall vino a long time ago. My user and keyring password are the same.

---

### Post by CharlesA on 2010-12-09
Don't know what to say then. I've been able to connect to vino without it prompting for my keyring password.

Maybe it's prompting for it so that you'll connect wirelessly, and you can't connect until you establish a connection.

---

### Post by Cue2 on 2010-12-09
> **CharlesA said:**
> Don't know what to say then. I've been able to connect to vino without it prompting for my keyring password.

Maybe it's prompting for it so that you'll connect wirelessly, and you can't connect until you establish a connection.

Thank you anyway CharlesA. I thought so too but even when the wireless is disabled it does the same. 

As soon as I connect I get a keyring dialog box locally and the remote client never connects until the keyring password is entered. Can I ask what your vino version number is?

---

### Post by CharlesA on 2010-12-09
I'm using whatever version of vino is in Lucid.

I remember running into the same thing you are before, but I cannot recall how I solved it. I had the machine set to auto logon and used VNC to connect to vino.

It seems there is a bug reported on it: [https://bugs.launchpad.net/ubuntu/+source/vino/+bug/562423](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/562423)

EDIT: It also seems related to wireless: [http://superuser.com/questions/43132/ubuntu-enter-password-for-default-keyring-to-unlock](http://superuser.com/questions/43132/ubuntu-enter-password-for-default-keyring-to-unlock)

Maybe it's still asking to unlock the keyring, even if you've disabled wireless?

---

