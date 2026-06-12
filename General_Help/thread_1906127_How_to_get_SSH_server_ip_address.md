---
title: "How to get SSH server ip address?"
date: 2012-01-08
forum: General Help
---

### Post by Mr. ViC on 2012-01-08
So I have set up a SSH server on my Ubuntu, and now I wanted to connect it through PuTTy (Windows) from another machines, but I can't seem to get the IP address I need to connect to it.

ifconfig -a doesn't do the trick, the IP addresses it shows only provides the local ones, not the external...

So I would need some help here.

Thanks in advance.

---

### Post by pbrane on 2012-01-08
> **Mr. ViC said:**
> So I have set up a SSH server on my Ubuntu, and now I wanted to connect it through PuTTy (Windows) from another machines, but I can't seem to get the IP address I need to connect to it.

ifconfig -a doesn't do the trick, the IP addresses it shows only provides the local ones, not the external...

So I would need some help here.

Thanks in advance.
 If you are looking for your public IP address try this.
```

wget -q -O - http://automation.whatismyip.com/n09230945.asp

```
You need to do this on the ssh server machine. Or at least on the same network.

---

### Post by Mr. ViC on 2012-01-08
Can I connect to the ssh server through other machines (outside local network) using the public address?

---

### Post by Seq on 2012-01-08
> **Mr. ViC said:**
> Can I connect to the ssh server through other machines (outside local network) using the public address?

You would have to have port 22 forwarded to the Ubuntu machine on whatever handles your public IP address (such as your router).

---

### Post by pbrane on 2012-01-08
You can, but you really should change the ssh port to something above 1024 and use key authorization instead of username/password. when I had my ssh server port-forwarded on port 22 I had several password guessing attempts everyday. Most were from overseas. 

You will need to port-forward any port you choose in your router as Seq stated above.

If you just want to connect to your ssh server on the same network (LAN) then just ssh to the ip of that machine.

Here is a link that might help:
[https://help.ubuntu.com/11.10/serverguide/C/openssh-server.html]("https://help.ubuntu.com/11.10/serverguide/C/openssh-server.html")
Also:
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")

---

