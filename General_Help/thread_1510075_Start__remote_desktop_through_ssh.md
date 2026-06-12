---
title: "Start  remote desktop through ssh?"
date: 2010-06-15
forum: General Help
---

### Post by Braveheart1980 on 2010-06-15
I have access to my linux home server , through ssh

I wanna start using now remote desktop , so i can connect to my home server through vnc.

Any ideas how I am going to do that?

I've tried this old post [here]("http://ubuntuforums.org/showthread.php?t=656129") , but I could not connect

What I did was to ssh with putty (and Xming) and X11 forwarding on , to start vino-preferences , which seemed to work BUT even though I connect with vnc to my remote server , all I see is grey stripes....

PS I have forwarded port 5500,5800 and 5900 to my home server pc of course

---

### Post by Peter09 on 2010-06-15
For a true remote desktop look at NXFREE. Look it up on the internet.
 
I presume you are thinking of a windows->linux connection.NXFREE will work for connectivity from windows to LINUX.
 
Remember you will also have to port forward your router.
 
Edit: note VNC and ssh are not the same thing.

---

### Post by anglican on 2010-06-15
> **Braveheart1980 said:**
> I have access to my linux home server , through ssh

I wanna start using now remote desktop , so i can connect to my home server through vnc.

Any ideas how I am going to do that?

I've tried this old post [here]("http://ubuntuforums.org/showthread.php?t=656129") , but I could not connect

What I did was to ssh with putty (and Xming) and X11 forwarding on , to start vino-preferences , which seemed to work BUT even though I connect with vnc to my remote server , all I see is grey stripes....

PS I have forwarded port 5500,5800 and 5900 to my home server pc of course
Try:
```
ssh -t -L 5900:localhost:5900 far-host 'x11vnc -localhost  -display :0'
```... assuming you're already logged on on "far-host". Otherwise:
```
ssh -t -L 5900:localhost:5900 far-host 'x11vnc -localhost  -auth /var/lib/gdm/:0.Xauth-display :0'
```H

---

### Post by maedox on 2010-06-15
Try FreeNX. It connects through ssh and is virtually setup free on the server side. The only thing you need to do is enter the host to connect to on the client side.

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

