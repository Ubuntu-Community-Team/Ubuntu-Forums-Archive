---
title: "sftp through a ssh connection"
date: 2010-06-16
forum: General Help
---

### Post by swraman on 2010-06-16
Hi,

the sysadmins have a server setup that makes it difficult for me to work from home.

There are many web servers I need to connect to, but they are only accessible from certain IPs on the subdomain.

To get to these "firewalled" servers I usually have to ssh into one "main" server that permits outside connections, then ssh through that into firewalled server.

This gets me shell access, but to copy files I have to scp them from teh firewalled computer to the main server, then scp them from that to my computer.

I prefer to use a graphical sftp, is there any way to connect to the "firewalled" server through sftp by using the "main" server as a proxy server to rout my connection?

Thanks

raman

---

### Post by The Cog on 2010-06-16
SSH has a TCP forwarding capability that you should be able to use. Let's assume that the "main" server is address 1.1.1.1 and you want to proxy onwards to 1.1.1.2. This would be the procedure:

First, SSH to the main server, setting up forwarding from local port 2222 to the target server port 22 at the same time:
**ssh -L 127.0.0.1:2222:1.1.1.2:22 username@1.1.1.1**

Now you can connect to your own PC with nautilus and the connection will be forwarded to the target server:
**nautilus sftp://username@127.0.0.1:2222**

The only problem is that SSH noted the machine ID. If you try to do the same to a different target server, SSH will refuse, because the ID of 127.0.0.1 has changed. The only solution I can think of for this problem is either:

1: Edit ~/.ssh/known-hosts every time, and delete the entry for 127.0.0.1.

2: I haven't tried this but I think it should work. Instead of connecting to 127.0.0.1, create secondary IP addresses on your machine, matching the target server address, and connect to that instead. You can make one interface for each target machine, eth0:1, eth0:2 etc.
[B]sudo ifconfig eth0:1 1.1.1.2 netmask 255.255.255.255
ssh -L 1.1.1.2:2222:1.1.1.2:22 username@1.1.1.1
nautilus sftp://username@1.1.1.2:2222[/B]

Edit: You need root permissions to forward ports below 1024, so perhaps use local port 2222 instead. Have edited the above lines to reflect this. Also, the ssh connection ties up your command prompt, so you will have to launch nautilus from a different command prompt.

---

### Post by swraman on 2010-06-16
Thanks for the response.

It looks like what you gave me gives me lets me use nautilus on the "firewalled" machine to connect to the target machine; but I want to connect to the target machine (using nautilus) on my computer at home.

I may have misunderstood your directions, id appreciate another reply.

Thanks,
Raman

---

### Post by The Cog on 2010-06-17
No, what I gave you lets your home nautilus connect to the target machine. I just didn't describe it very well.

You need two command prompts open on your home machine. In the first command prompt, connect to the relay machine (10.1.1.1 in my example), using the tunneling options. After making this connection, you have a command prompt open on the relay machine. Now you leave this command prompt alone.

In a second command prompt on your home machine, launch nautilus to connect to your home machine, 127.0.0.1 (or 10.1.1.2 if you created that local secondary address). Nautilus connects to your local machine which in turn connects over the ssh tunnel to the relay machine and asks the relay machine to connect onwards to the target machine. So nautilus ends up talking from your PC to the target PC.

I forgot to mention that there is a third option, another way to do SSH tunneling, and that is by using an SSH VPN. But that would need special configuration on the relay machine and allow root access, which I guess you wouldn't be allowed to put there.

---

