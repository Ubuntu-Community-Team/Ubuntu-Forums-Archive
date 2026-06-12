---
title: "default route ssh -D"
date: 2010-01-30
forum: General Help
---

### Post by Psycho.mario on 2010-01-30
When i am away from my home network;  i always use an ssh socks tunnel with the command 'ssh -D <port> <server>'. This is very easy for firefox, normal web browsing. But for other web traffic, i tried to use the tun0 device ([https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)) but this didnt work for me (The error was: channel 0: open failed: unknown channel type:). So i was wondering if i could set the default route (with the route command?) through this command, so ALL my network traffic goes through it.

Thanks

---

### Post by pbrane on 2010-01-30
I use ssh -D<port> to login to a remote server like you. the -D is a "dynamic" port forwarding. Any protocol should work through that tunnel. If you set firefox to use a SOCKS proxy given the port you choose only firefox will use the proxy. You should be able to set a system wide SOCKS proxy that all your apps will use. In GNOME on Karmic it would be set in System->Preferences->Network Proxy. 

Is this what you are asking?

---

### Post by Psycho.mario on 2010-01-30
I knew about that; but i think that there might be some programs that wouldn't use gnome proxy settings. I think for example, without changing a setting in firefox, the DNS doesnt go through the proxy. I wanted to know if you could either: create a tun0 device as the main network device, or change the default route to utilize this tunnel.

Thanks

---

### Post by pbrane on 2010-01-30
I have never done what you're asking. But here is a link that might help.
[http://ubuntuforums.org/showthread.php?t=564538]("http://ubuntuforums.org/showthread.php?t=564538")

So far everything I have seen uses the network proxy settings.

Another link:
[http://ubuntuforums.org/showthread.php?t=12088]("http://ubuntuforums.org/showthread.php?t=12088")

---

### Post by Psycho.mario on 2010-01-30
I read that, didnt really give me any answers, thanks though.
The current command i'm trying to use is:
```
sudo ssh -vvv -wany:any root@192.168.2.1 -p 8080

```
i think the reason it isn't working is because the target is a dd-wrt router, which doesn't have the usual /etc/ssh/sshd_config so i cant add PermitTunnels.
I might look into it tomorrow on my other Ubuntu machine with the ssh server on it. But ideally i would want to be able to use this tun0 from this (my netbook) to my router at home, for travelling etc.

Thanks

---

### Post by Psycho.mario on 2010-01-30
Is it not possible to create a tunnel from an existing connection?

---

### Post by Psycho.mario on 2010-01-31
Bump

---

### Post by pbrane on 2010-01-31
From *man sshd_config*:
```
PermitTunnel
             Specifies whether tun(4) device forwarding is allowed.  The argu&#8208;
             ment must be &#8220;yes&#8221;, &#8220;point-to-point&#8221; (layer 3), &#8220;ethernet&#8221; (layer
             2), or &#8220;no&#8221;.  Specifying &#8220;yes&#8221; permits both &#8220;point-to-point&#8221; and
             &#8220;ethernet&#8221;.  The default is &#8220;no&#8221;.

```

Not sure if you have already seen this

---

### Post by Psycho.mario on 2010-02-01
Yeah, i read through the whole of the ssh man, and ssh_config man, but the server is dropbear it turns out, with no option for openssh as its a (ddwrt) router with no storage, and i cant even edit the config file, because dropbear doesn't seem to have one. It may be that i can't do this, which is a shame, because the router is only dropbear. Theoretically i could use one of my other computer as a ssh server, and start it with wakeonlan, but that isn't as easy.
Any more ideas anyone?

---

### Post by Jarige on 2011-01-31
I'm trying something similar (VPN over SSH) but having exactly the same error. Have you already figured it out? And if you do, how did you?

---

