---
title: "Ftp DISconnect"
date: 2006-04-08
forum: General Help
---

### Post by ncappel1 on 2006-04-08
After going into Places-->Connect to Server, selecting "ftp (withlogin)" and typing inthe correct info, I have succesfully created a bookmark in the "Places" and mountable desktop item to my schools personal webspace server.

The problem is that after I connect once (without checking the "use password for this session" or "save passowrd to key ring" boxes), even after I close nautilus and/or unmount the volume, all I have to do is click "connect to server" from the pulldown menu and after inputing the server address (without a username) I am immediately connected again to the previously logged in user. This is done without prompting me for a name or password! I suspect that this is some kind of courtesy that Ubuntu does for me, remember the last login and password, how can I tell it to "forget" this info or to force a prompt for a name and password everytime?

after searching the forums, I found many threads telling me about how to connect to an FTP server, but none tell me how to disconnect from it-permanantly.

any help is appreciated.

---

### Post by dcstar on 2006-04-08
[QUOTE=ncappel1]After going into Places-->Connect to Server, selecting "ftp (withlogin)" and typing inthe correct info, I have succesfully created a bookmark in the "Places" and mountable desktop item to my schools personal webspace server.

The problem is that after I connect once (without checking the "use password for this session" or "save passowrd to key ring" boxes), even after I close nautilus and/or unmount the volume, all I have to do is click "connect to server" from the pulldown menu and after inputing the server address (without a username) I am immediately connected again to the previously logged in user. This is done without prompting me for a name or password! I suspect that this is some kind of courtesy that Ubuntu does for me, remember the last login and password, how can I tell it to "forget" this info or to force a prompt for a name and password everytime?
......[/QUOTE]
It may also be the server you are connecting to caching the connection details and not bothering to require an additional login.

You many need to install a packet capture tool and analyse the traffic from your Ubuntu system to determine exactly what is happening - you could be wasting your time on the wrong end of the problem otherwise!

---

