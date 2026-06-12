---
title: "Best way to secure remote desktop?"
date: 2010-10-18
forum: General Help
---

### Post by Lucky75 on 2010-10-18
Hey,

I was wondering what the best way to secure RD would be? What's the best one to use? I'd prefer a method that isn't always active, so maybe something that I need to enable via ssh first?

Any suggestions?

Thanks!

---

### Post by spikoley on 2010-10-18
I recommend using an SSH tunnel.  Run these commands to connect to the remote computer.

```
ssh -L 5900:localhost:5900 user@myserver
```

```
xvncviewer localhost:5900
```

---

### Post by Lucky75 on 2010-10-19
I suppose I could just run the standard VNC client then, yeah. I guess if I don't open the port on my router that would be fine ;)

---

### Post by JoelOl75 on 2010-10-19
I love NoMachines NX.  It's much faster than vnc and tunnels over ssh... Which is nice as any more ports to forward adds more security concern.  I usually change my sshd.config file to run ssh on a non-default port which keeps script kiddies from brute forcing port 22.  Also disable root logons (You can su or sudo anyway).  After you get ssh set up goto [http://www.nomachine.com/](http://www.nomachine.com/) and download the free edition in .deb packages. You need all three (Server, Node, and client) 

There's also a NX Windows, Mac OS, and Solaris client so it's completly cross platform and features highly compressed and cached remote desktop which is snappy, even tolerable on dial up.

If you don't use the standard port make sure to change the settings in the config files in /usr/NX/etc directory (Easiest to grep 'em for 22... make sure to uncomment the line as well) and issue a 

sudo service nxserver restart

---

### Post by Lucky75 on 2010-10-19
Yeah, NX is great, but I find that there is very little documentation. If you know how to get it working with multiple monitors and logging into the correct session (i.e. :0) then please let me know :)

---

