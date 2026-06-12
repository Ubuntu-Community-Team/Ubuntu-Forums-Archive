---
title: "xrdp doesn't visually show updates"
date: 2011-07-01
forum: General Help
---

### Post by Kissell on 2011-07-01
I can use the Remote Desktop Client from a windows machine to connect to a Ubuntu 10.10 server, it works great...  I can login, see the screen, see the mouse move around, and click on things.  The only problem is that after I click on something, like I minimize a window, I don't see the result.  However, if I close the RDP session and connect again, I see that window has been minimized.  

Any ideas!?

sudo netstat -anpt | grep -E "vino|vnc|xrdp"
> 
tcp        0      0 127.0.0.1:3350          0.0.0.0:*               LISTEN      1842/xrdp-sesman
tcp        0      0 0.0.0.0:3389            0.0.0.0:*               LISTEN      1840/xrdp       
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN      2112/vino-server
tcp6       0      0 :::5900                 :::*                    LISTEN      2112/vino-server


This is my xrdp.ini
> 
[globals]
bitmap_cache=yes
bitmap_compression=yes
port=3389
crypt_level=low
channel_code=1

[xrdp1]
name=Active Local Login
lib=libvnc.so
username=ask
password=ask
ip=127.0.0.1
port=5900

[xrdp2]
name=Clean Session
lib=libvnc.so
username=ask
password=ask
ip=127.0.0.1
port=5901


---

### Post by Kissell on 2011-07-01
I took a windows laptop over to the server's monitor, and did the RDP from the laptop...  sure enough, every movement I make on the windows laptop is happening on the ubuntu server, but I'm not seeing any of those changes reflected on my laptop's screen, only on the server screen.

---

