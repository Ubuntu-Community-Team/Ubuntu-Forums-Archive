---
title: "Problem accessing ftp server is it ufw?"
date: 2011-03-15
forum: General Help
---

### Post by ianc1 on 2011-03-15
I am trying to access an ftp server using gftp.  I can see from the log in gftp that I connect to the server so I've got the port and server address correct, however it just hangs and doesn't show the directory structure.  I also know the server details are correct as I can connect at work on another machine.

I wonder if the problem is ufw.  I have this enabled with defualt deny and no other options.  ufw status verbose provides the following output:```
sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip
```I thought this set up of ufw allowed in any connections instigated by me.  Is there anything else I need to allow?

Any ideas would be greatfully appreciated.  Thanks

---

### Post by 5149.5 on 2011-03-15
> **ianc1 said:**
> I am trying to access an ftp server using gftp.  I can see from the log in gftp that I connect to the server so I've got the port and server address correct, however it just hangs and doesn't show the directory structure.  I also know the server details are correct as I can connect at work on another machine.

I wonder if the problem is ufw.  I have this enabled with defualt deny and no other options.  ufw status verbose provides the following output:```
sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip
```I thought this set up of ufw allowed in any connections instigated by me.  Is there anything else I need to allow?

Any ideas would be greatfully appreciated.  Thanks 

I think you should get the directory back but FTP can and will switch ports for data transfer. I don't know if UFW can handle the port switch but I doubt it.

If you're not getting the directory back, just turn off the fire wall and retry. ????

---

### Post by ianc1 on 2011-03-15
Hi Dan.

Thanks for the reply.  Just tried with ufw disabled.  Unfortunately still no success.  I wonder if my ISP can be locking FTP?  I have limited control over my routers firewall (from ISP) other than on/off.

---

### Post by 5149.5 on 2011-03-15
I just did a quick google and an FTP server does treat a directory transfer and a data transfer the same. Therefore since UFW is not a stateful firewall, the directory transfer will fail because of the mismatch on the incoming and outgoing port numbers.

---

### Post by 5149.5 on 2011-03-15
> **ianc1 said:**
> Hi Dan.

Thanks for the reply.  Just tried with ufw disabled.  Unfortunately still no success.  I wonder if my ISP can be locking FTP?  I have limited control over my routers firewall (from ISP) other than on/off.

It is starting to sound like your ISPs firewall isn't stateful either.

---

### Post by gandaran on 2011-03-15
> **ianc1 said:**
> Hi Dan.

Thanks for the reply.  Just tried with ufw disabled.  Unfortunately still no success.  I wonder if my ISP can be locking FTP?  I have limited control over my routers firewall (from ISP) other than on/off.
try with filezilla, install from package manager, I use filezilla with the firewall enabled and with no problems.

---

### Post by ianc1 on 2011-03-15
Bingo I'm in.  Thanks Dan and gandaran.

Thanks also for the Filezilla tip it's much nicer than gftp and does the job although it may of course have been my error in gftp.

Am I correct in thinking that as I instigated the sftp connection that ufw should let it in, whereas a connection from outside to me should be dropped?  I'm now going to go away and find out what a stateful firewall is.  I suppose concerning my ISPs poor firewall I could by a better router in which I control the firewall and turn off the ISPs firewall.

Thanks again

---

