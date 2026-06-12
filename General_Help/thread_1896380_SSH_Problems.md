---
title: "SSH Problems"
date: 2011-12-16
forum: General Help
---

### Post by cuberts on 2011-12-16
Recently I set up an SSH server, and I am not very experienced with this. I have a few questions about this.
FIrst, when I try to stop my SSH server, it does work but outputs things when I type the following command:
```

sudo /etc/init.d/ssh stop

```Rather than invoking init scripts through /etc/init.d, use the service(8   )
utility, e.g. service ssh stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop( 8 )utility, e.g. stop ssh
ssh stop/waiting

It may not be a big issue, I just find it very annoying to have that pop up, if you see what I mean.

Also, could someone tell me what the difference is between the previous command, and
```
sudo service ssh start
```To my understanding, the only difference is that it doesn't output that annoying message, however am I doing something fundamentally wrong by typing that command?

Lastly, I have tested my ssh server from another computer on the same network, and I have confirmed that the computer I want to access is accessible internally. How can I now access it from the outside world?

---

### Post by squaregoldfish on 2011-12-17
The script messages are fine. Not long ago, Ubuntu changed its preferred method of starting and stopping services from the init.d scripts to the service stop/start method. All the message is telling you is that Ubuntu would prefer you to use the new system. (Presumably init.d will be removed altogether at some point in the future.)

As for getting SSH access from the outside world, you have to configure your router to forward all traffic on the SSH port (22) to your SSH server machine. This should be pretty simple to set up - there'll be a port forwarding section in your router's configuration. Check your router's manual if you're not sure where to look.

Steve.

---

### Post by The Cog on 2011-12-17
Note that once your SSH server is accessible to the outside world, you will have dozens of password-guessing bots connected to it all day every day. You should consider disabling SSH use of passwords and using password-less keys instead, and using deny-hosts or a firewall rule to block repeated connections.

---

### Post by squaregoldfish on 2011-12-17
If it's only you who's going to be SSHing into your box, I'd recommend configuring an alternative port for the SSH server (somewhere in the 10000 range). You can easily reconfigure the SSH server and your router, and any SSH client worth the name will allow you to change the port it sends requests to.

Since I did it, I haven't had a single attempt to break into my SSH server, because the bots can't find it!

(Remember to close down port 22 on your router!)

Steve.

---

### Post by perspectoff on 2011-12-17
Most cracking bots scan for open ports as the very first step anyway, and port scans usually indicate what type of service is running on that port. If it is always left open, using a non-standard port doesn't offer much added security in the long run, therefore.

There's a lovely utility called knockd that requires a pre-determined series of port attempts (a "knock") before the SSH (or other service) port will actually be opened. 

Because without the correct knock all ports remain closed, to a cracker bot it just looks like all ports are closed and they move on.

That particular tool has speeded up remote access to the server (because a certain amount of server time is used when there are constant port probes by bots, and this gets rid of that nuisance).

---

