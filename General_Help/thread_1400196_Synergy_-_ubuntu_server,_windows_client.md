---
title: "Synergy - ubuntu server, windows client"
date: 2010-02-06
forum: General Help
---

### Post by trailofdead on 2010-02-06
I've been using synergy on Ubuntu 9.04 and windows xp.  Synergy 1.3.1 on both machines.  

My problem is that the server keeps cutting out.  It seems to happen a lot when I watch flash videos on the server machine (ubuntu).  This is what the server side looks like: 
```
NOTE: synergys.cpp,500: started server
INFO: CServer.cpp,1141: screen "server" shape changed
NOTE: CClientListener.cpp,127: accepted client connection
DEBUG: CClientProxy1_0.cpp,404: received client "client" info shape=0,0 2560x960
NOTE: CServer.cpp,278: client "client" has connected
NOTE: CClientProxy1_0.cpp,221: client "client" is dead
NOTE: CClientListener.cpp,127: accepted client connection
DEBUG: CClientProxy1_0.cpp,404: received client "client" info shape=0,0 2560x960
NOTE: CServer.cpp,278: client "client" has connected
INFO: CServer.cpp,447: switch from "server" to "client" at 0,440
INFO: CScreen.cpp,116: leaving screen

```

This is the corresponding client side:
```
NOTE: connected to server
NOTE: server is dead
WARNING: failed to connect to server: server is not responding
NOTE: connected to server
INFO: entering screen
INFO: leaving screen
NOTE: server is dead
WARNING: failed to connect to server: server is not responding
WARNING: failed to connect to server: Timed out
WARNING: failed to connect to server: Timed out
WARNING: failed to connect to server: Timed out
WARNING: failed to connect to server: Timed out
NOTE: connected to server
INFO: entering screen

```

synergy.conf:
```
section: screens
        client:
        server:
end

section: aliases
        client:
        192.168.2.249
end

section: links
        server:
                right =client
        client:
                left = server
end

section: options
        screenSaverSync = false
end

```

I dont think I usually get disconnected when doing other tasks.  Mostly only when watching flash videos.  Sometimes it doesnt automatically reconnect, and I have to kill synergys and restart it.  

What's wrong??

---

### Post by trailofdead on 2010-02-10
Whenever I run synergys in the terminal, I know that the client wont reconnect when I cant break the server with ctrl-c.  That's when I have to kill it.

Anyone know what's going on here?  It's annoying to have to kill and restart synergy every time I watch a youtube video.

---

