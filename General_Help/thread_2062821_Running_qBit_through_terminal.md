---
title: "Running qBit through terminal"
date: 2012-09-25
forum: General Help
---

### Post by adduds on 2012-09-25
Is it possible to ssh into another ubuntu computer and start an application and keep it running once terminal is closed?

Ie. qBittorrent?

I use the web interface, which needs the program running, but sometimes it force closes. Rather than go over to my server and start it again I'd like to ssh into my server from my terminal app on my phone android or laptop but once you exit the session it closes all running apps aswell

Thanks in advance

---

### Post by josephmills on 2012-09-25
You can install transmission-cli on to the ssh box. 
I have not used it but I am sure that it is up to par. and yes you can leave it running with adding the & at the end of the command 
example: 

```
transmission-cli -w ~/Downloads/ some_magenet &

```

you can then test this with something like ps aux 
log out and back in again 
```
ps aux | grep transmission-cli |less
```
Is it still running ? Good luck and Hope that this helps

---

### Post by LewisTM on 2012-09-25
You can install the GUI-less web backend of QBittorrent with package **qbittorrent-nox**. It works just as well as the full package and uses the same settings, including HTTP port, username, etc.

To launch it and let it run in the background, run this in a ssh session
```
qbittorrent-nox & disown
```
One disadvantage is that once you logout, you will lose any output from the server and the only way to quit it would be to kill the process with [FONT="Courier New"]pkill qbittorrent[/FONT]. You should explore the possibility of running it inside a GNU **screen** session, so you can resume it anytime. Even better, install the screen frontend **byobu** and run 
```
byobu-enable
```
That way, anytime you log in by ssh, you will be presented with a resumed, always-running, multiwindow screen session. Press F2 to add a window, F8 to rename it (e.g. Qbit), F3/F4 to navigate and F6 to log out while leaving screen running (i.e. detach).

Cheers!

---

### Post by adduds on 2012-10-01
> **josephmills said:**
> You can install transmission-cli on to the ssh box. 
I have not used it but I am sure that it is up to par. and yes you can leave it running with adding the & at the end of the command 
example: 

```
transmission-cli -w ~/Downloads/ some_magenet &

```

you can then test this with something like ps aux 
log out and back in again 
```
ps aux | grep transmission-cli |less
```
Is it still running ? Good luck and Hope that this helps

Perfect use transmission-cli all the time now thanks muchly!

---

