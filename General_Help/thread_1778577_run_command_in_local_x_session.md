---
title: "run command in local x session"
date: 2011-06-09
forum: General Help
---

### Post by gregology on 2011-06-09
Hello cleaver people :)

I have a laptop running as a TV server running Ubuntu desktop with ssh server installed. I would like to remotely login to the TV server and run commands like VLC in the TV servers local environment as a local user. Does anyone know how I would go about doing that?

I eventually want to make my TV server a LAMP server and write a php script that opens media content so any web browsing device (iPad, phone etc) can be used as a remote control.

Thanks,

Gregology.

---

### Post by Peter09 on 2011-06-09
Not sure if this is what you want.
 
on the server
 
```

sudo apt-get install xauth

```
 
then install the application that you want - say
 
```
sudo apt-get install nautilus
```
 
this will bring in a load of other dependencies.
 
now on the client try the command
 
```
ssh -X <your userid>@<server name/ip> nautilus
```
 
this should bring up a window with the filebrowser which is based on the server.
 
You can run most applications in a similar manner.
 
NOTE ---- reading your post again I'm not sure if you have a headless server. If your server has a desktop environment already installed then the ssh command will work with no further effort.

---

### Post by gregology on 2011-06-16
Thanks mate, much appreciated :)

---

