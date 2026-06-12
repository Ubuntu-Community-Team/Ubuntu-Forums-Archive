---
title: "ssh port forwarding: bind cannot assign requested address"
date: 2012-05-22
forum: General Help
---

### Post by ianc1 on 2012-05-22
Hi all

I have a problem I don't understand while trying to port forward over ssh.

I wish to remote desktop to a Windows machine at work from my home Linux box.  I can do this through an ssh gateway using:```
ssh -L port:windows_machine:3389 username@ssh_gateway -p ssh_port
```Doing this I can then connect to the windows machine using Remmina via localhost and the appropriate port from the command above.

So all appears to work.  However when I execute the ssh command I get the following error```
bind: Cannot assign requested address
```Using netstat I can tell I'm not already using the port on my local machine.

Any ideas what's wrong.  Thanks in advance.

Ian

---

### Post by ianc1 on 2012-05-23
I've managed to try this on a Mint 12 machine ie one based on Ubuntu 11.10.  I got no error message using that machine.

Mint 12 has openssh version 5.8 while 12.04 has 5.9.  Is this a bug I should be reporting?  How do I tell?

Thanks

---

### Post by papibe on 2012-05-23
Hi ianc1.

That kind of forwarding is working for me on 12.04.

The error looks more like a DNS error to me. Could you post the log using the extra verbose option while trying to connect using the forwarded port?
```
ssh -vvv ...
```
Regards.

EDIT: To start, I imagine you have some sort of sshd service on the Windows machine isn't it?

---

### Post by ianc1 on 2012-05-23
Hi papibe

Thanks for the reply.  The host I ssh into is a Linux machine and it is on the same network as the windows machine and easily connects to it.  I know there are no problems there.

I ran the command as suggested and the output is attached with some bits starred out for security reasons.  I hope they weren't the relevant bits but as far as I could see they were info only.

Thanks in advance

---

### Post by papibe on 2012-05-23
```
debug3: sock_set_v6only: set socket 5 IPV6_V6ONLY
debug1: Local forwarding listening on ::1 port 9999.
bind: Cannot assign requested address
```
The only difference that I see is that you are using IPv6 only? Any reason? May be allowing regular IPv4 would work. 

Regards.

---

### Post by ianc1 on 2012-05-23
Thanks papibe.  That's odd as I thought I had disabled IPv6 on my machine as most firewalls ignore it (I have been led to believe) and I don't have an IPv6 enabled router.

I set:```
net.ipv6.conf.all.disable_ipv6=1
```in the file sysctl.conf.

Should I revert this?  Is this error coming from my local machine (the one I issue the SSH command on) or the remote machine I SSH into?

Thanks again.

---

### Post by papibe on 2012-05-23
Let's try force the use of IPv4 on both ssh commands: the one creating the tunnel, and the one using it:
```
ssh  -4  ...
```
Regards.

---

### Post by markbl on 2012-05-23
Login to your server first then try telneting to that port on the windows box. Then you can tell which step is failing. Note that the name "windows_machine" must be resolvable by the ssh_gateway machine.
```

ssh username@ssh_gateway -p ssh_port
telnet windows_machine 3389

```

---

### Post by ianc1 on 2012-05-24
Thanks papibe and markbl.

Before I got the replies I enabled IPv6 in sysctl.conf again and tried.  Success.  When I got the replies I tried again with IPv6 disabled and using the ssh - 4 option as you suggested.  Again success.  Hoorah.

What puzzles me is why this is an issue.  As far as I am aware the router I use only uses IPv4.  Any ideas?

Thanks again for the help.

---

### Post by papibe on 2012-05-24
It could be in the configuration of ssh itself.

Could you post the content of this command on both the client and the server?
```
grep -i address /etc/ssh/ssh*config
```
Regards.

---

### Post by ianc1 on 2012-05-26
Hi papibe

Sorry for the delayed response to your post.  The output is as follows:```
#   AddressFamily any
```Thanks Ian

---

### Post by papibe on 2012-05-26
I think that's from the client, right?

How about the same command on the server (what you called ssh_gateway)?

Regards.

---

### Post by ianc1 on 2012-05-27
Sorry Papibe.  I missed the key point in your penultimate response - "on the client and server".

Your correct the results posted were from my home machine - the client.  The server (or ssh-gateway as my employer calls it) gives the same response for the ssh_config file but unfortunately I get permission denied for the sshd_config file.

I suppose this prevents further diagnosis on this?

Thanks again, and once again apologies for not ready your penultimate response fully.

Ian

---

