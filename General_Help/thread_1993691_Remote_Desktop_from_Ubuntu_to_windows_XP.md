---
title: "Remote Desktop from Ubuntu to windows XP"
date: 2012-06-02
forum: General Help
---

### Post by codingman on 2012-06-02
I'm trying to get my ubuntu system to remote desktop to a windows XP machine, and I was wondering what I should put in as the server to connect to the system. It's a local system too.

Any help is appreciated!
Codingman

---

### Post by steeldriver on 2012-06-02
from Vinagre? just the local IP of the windows box works for me - should be good unless you have changed from the default port I think

obviously you need to allow remote connections from the windows side (System -> Remote -> Allow users to remotely connect to this computer)

---

### Post by inashdeen on 2012-06-02
Why dont you use teamviewer :) ? its easier. trust me

---

### Post by scottbomb on 2012-06-02
I use the free service from logmein.com. The host software is installed on the Windows machine. I can access the Windows desktop from any PC, anywhere, regardless of the OS that PC using. The client runs in a browser so there is no software to install on the client machine.

---

### Post by inashdeen on 2012-06-02
thanks for the tip :) wow. never thought it can also be this simple

---

### Post by codingman on 2012-06-02
What route should i use? VNC? When i do this with vnc it gives up after a short period of time, and doesn't connect.

---

### Post by steeldriver on 2012-06-02
you mean protocol? that would be RDP

to use VNC you would need a 3rd party VNC server running on the Windows box - with RDP it is built in (just the same as using the Windows Remote Desktop client from Windows to Windows)

---

### Post by codingman on 2012-06-02
> **steeldriver said:**
> you mean protocol? that would be RDP

to use VNC you would need a 3rd party VNC server running on the Windows box - with RDP it is built in (just the same as using the Windows Remote Desktop client from Windows to Windows)

It then says it can't find the server of ___.___._.___

---

### Post by codingman on 2012-06-02
bump.

---

### Post by steeldriver on 2012-06-02
if you are on a newer Ubuntu that has UFW enabled, you may need to open an *outgoing* port:

[http://ubuntuforums.org/showthread.php?t=1932667](http://ubuntuforums.org/showthread.php?t=1932667)

 iirc only XP XP Pro includes the RDP server component (aka terminal services) - XP Home doesn't, although that  should be obvious when you try to allow remote access

---

