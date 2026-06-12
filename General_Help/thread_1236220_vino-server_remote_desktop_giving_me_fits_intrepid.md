---
title: "vino-server remote desktop giving me fits intrepid"
date: 2009-08-10
forum: General Help
---

### Post by Fanless_Puppy_Fan on 2009-08-10
If I turn off Remote Desktop Sharing through the default Intrepid menus, I can install krfb and access it with krdc from another computer on the lan. When I do so, it works, but terribly. 

If I remove krfb and enable desktop sharing through the Remote Desktop icon in the menu, I cannot connect to the server. I have a default intrepid install and didn't have this problem at all in hardy.

I am sorry to post such little detail. It appears that the vino-server is not allowing any connections. Is this a permissions issue? I have tried all the permutations of the settings in the gui, but is there a config file that needs tweaking? 

Like I said, krfb is working (poorly), but the vino-server is not. I am asking for pointers in the right direction. 

I can telnet in when krfb is running, but netstat doesn't seem to see the open port:

chris@chris-desktop:~$ netstat -lnp | grep 5900
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
chris@chris-desktop:~$ 
chris@chris-desktop:~$ 
chris@chris-desktop:~$ telnet 192.168.0.122 5900
Trying 192.168.0.122...
Connected to 192.168.0.122.
Escape character is '^]'.
RFB 003.008
^ exit
Connection closed by foreign host.
chris@chris-desktop:~$ 

When running the default vino-server:

chris@chris-desktop:~$ netstat -lnp | grep 5900
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
chris@chris-desktop:~$ telnet 192.168.0.122 5900
Trying 192.168.0.122...
telnet: Unable to connect to remote host: Connection refused
chris@chris-desktop:~$ 

When I try to connect the default Remote Desktop View to:192.168.0.122:5900, the error is:
Connection to host "192.168.0.122:5900" was closed.

Thanks for any help.

---

### Post by Fanless_Puppy_Fan on 2009-08-10
Don't know why, but changing to a nonstandard port in the Remote Desktop Configuration Advanced settings made it all start working.

---

