---
title: "A Howto setup VNC with Lucid?"
date: 2010-05-07
forum: General Help
---

### Post by ksaul on 2010-05-07
I cant find one :(

---

### Post by spiky001 on 2010-05-07
there is remote desktop built in Applications accessories internet remote desktop

---

### Post by The Cog on 2010-05-07
On your server: 
System -> Preferences -> Remote Desktop
Then allow other users to view your desktop.

On your client:
Applications -> Internet -> Remote Desktop Viewer

---

### Post by spiky001 on 2010-05-07
sorry stand corrected Cog You are right

---

### Post by ksaul on 2010-05-07
I know I have the password right but keeps saying auth failure.. :(
port 22, 5900-5999 are open. username is correct I am connect via SSH no problem.

---

### Post by spiky001 on 2010-05-07
have you set up desktop sharing,allow other users to view desktop, allow other users to control desktop, configure network automatycally to accept connections, ?

---

### Post by 2hot6ft2 on 2010-05-07
> **ksaul said:**
> I know I have the password right but keeps saying auth failure.. :(
port 22, 5900-5999 are open. username is correct I am connect via SSH no problem.
I don't use VNC but you can start it in a terminal on the server with
```
x11vnc
```
assuming of course that you have that installed.
And from the client connect by entering the servers IP Address in xtightvncviewer which is also started in the terminal with:
```
xtightvncviewer
```

Personally I use FreeNX, it's faster and more secure. Since you already installed SSH you may want to check it out. There's a guide in my sig. below for it.
:popcorn:

---

