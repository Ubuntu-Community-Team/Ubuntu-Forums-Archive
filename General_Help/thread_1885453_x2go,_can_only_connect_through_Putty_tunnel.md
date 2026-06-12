---
title: "x2go, can only connect through Putty tunnel"
date: 2011-11-23
forum: General Help
---

### Post by rks1789 on 2011-11-23
I had been using FreeNX for a while, but recently updated to 11.04, and the repository has not been updated for that.

I took the opportunity to try out x2go.  Install went fine, I'm connecting from a Win7 host machine.

When I'm at work I have had to set up a Putty tunnel through work's firewall to get VNC/NX/x2go to work, and it works just fine.

When I'm at home I would like to connect directly to the machine, but it does not work.  I get the "maybe your password is wrong" error after it attempts to connect.

If I open a tunnel (putty port local 22 to port remote 22) at home I can connect just fine to the machine.  Note I'm connecting with Putty through port 22 to the remote machine.

The auth.log looks ok, I connect, it accepts the password. etc. 

In a failing  .x2go/<session name>/session.log I get this output:

NXAGENT - Version 3.5.0

Copyright (C) 2001, 2011 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Agent running with pid '9524'.
Session: Starting session at 'Sun Nov 20 11:58:51 2011'.
Info: Proxy running in server mode with pid '9524'.
Info: Waiting for connection from 'localhost' on port '30001'.
Warning: Parent process appears to be dead. Exiting watchdog.
xiting watchdog.

In a working run I see the above, but instead of the parent dying:
Info: Accepted connection from '127.0.0.1'.

Any idea why this might be this way?

Rich

---

### Post by rks1789 on 2011-11-28
Bump?

---

### Post by azmyth on 2011-11-29
Are you using the Windows Client downloaded from the x2go site to connect from Win7 to Ubuntu? I just started using x2go for the same reason as you and it worked out o the box so to speak. I just setup the host, the port, then the key and I was good to go.

---

### Post by rks1789 on 2011-11-29
> **azmyth said:**
> Are you using the Windows Client downloaded from the x2go site to connect from Win7 to Ubuntu? I just started using x2go for the same reason as you and it worked out o the box so to speak. I just setup the host, the port, then the key and I was good to go.


That is exactly what I'm trying to do.  What do you mean by "set up the port"?  The documentation I read only talked about the ssh port (by default 22, I have left that alone for now).

I assume the key is the ssh key, and is optional.

Thanks!

Rich

---

### Post by azmyth on 2011-11-29
I don't have my ssh running on the standard port so I have to specify the proper port when I setup my windows x2go client.

Do you have another Linux system where you can try to ssh into the server?

---

### Post by azmyth on 2011-11-29
Yes the ssh key is optional assuming you don't have ssh set to key auth only.

---

### Post by rks1789 on 2011-11-29
> **azmyth said:**
> I don't have my ssh running on the standard port so I have to specify the proper port when I setup my windows x2go client.

Do you have another Linux system where you can try to ssh into the server?

I do not, but I can ssh into the Linux box just fine.

I can even open a putty (ssh) session from my laptop, with port forwarding enabled for localhost:22 to remotehost:22, then point x2go to localhost:22 and it works fine.... ( I have this set up for what I was using before, I have VNC port forwarded through ssh (work firewall) to make that connection...)

What I have yet to get working is connecting directly to the machine with x2go (directly connecting through port 22...

When I connect, I see the auth.log get my connection, the password works fine, but then the x2go process seems to die. (see logs above)

Rich

---

