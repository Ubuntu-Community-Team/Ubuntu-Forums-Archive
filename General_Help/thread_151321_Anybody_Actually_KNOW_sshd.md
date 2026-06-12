---
title: "Anybody Actually KNOW sshd?"
date: 2006-03-27
forum: General Help
---

### Post by AllBuntu on 2006-03-27
Hi,

I see a lot of advice on sshd. Let's be scientific, and I (who don't know) will put down what I figured out:

[http://openssh.com](http://openssh.com) provides tunneling software for which ssh is the client (where you sit) and sshd is the daemon (that receives and forwards connections)

ssh is a regular command and comes default in Ubuntu 5.10

sshd has to be installed: sudo aptget openssh-server
(or System > Administration > Synaptic Package Manager)

sshd is controlled via the text file /etc/ssh/sshd_conf
I think changes to this file are applied via
ps -ef | grep sshd <note the pid for sshd>
sudo kill -SIGHUP pid

Is this all correct?

My issue is I want to enter my subnet via OpenSSH on the Ubuntu machine, and then continue and do VNC and remote desktop to Windows on the same subnet. There are a number of settings to be made to bypass "safe" settings for this, and I do not know what they are.

Anybody can help to use Ubuntu as a gateway?

Thanks, Harry

---

### Post by majikstreet on 2006-03-27
I don't know about the gateway thing, but I know you can do sudo /etc/init.d/ssh restart to restart the daemon..

i think you would tunnel the VNC port to the windows machine. but I really don't know.

---

### Post by Barrakketh on 2006-03-27
[QUOTE=AllBuntu]I think changes to this file are applied via
ps -ef | grep sshd <note the pid for sshd>
sudo kill -SIGHUP pid[/quote]
As opposed to using:
```
sudo /etc/init.d/ssh reload
```
?
> My issue is I want to enter my subnet via OpenSSH on the Ubuntu machine, and then continue and do VNC and remote desktop to Windows on the same subnet. There are a number of settings to be made to bypass "safe" settings for this, and I do not know what they are.
What?  If you have a VNC server running on the Windows box (such as TightVNC) then you can just use the Linux TightVNC client to connect.

If you're saying that you have an box running OpenSSH (the server) that is accessable from the outside world (example: your router has port 22 forwarded to an Ubuntu box behind a NAT) and you wish to connect to the Windows boxen that aren't accessable from the ouside world, then it sounds like what you're interested in is SSH port forwarding/tunneling.

So...can you be a bit more clear about exactly what you want to accomplish?

---

### Post by harisund on 2006-03-27
Could you be a bit more clear as to what exactly is it that you want to get done?

---

### Post by Jason_25 on 2006-03-27
I think you want to do ssh port forwarding which is easy to do.

On the pc that you want to be the ssh server
```

sudo apt-get install openssh-server

```
Then from a remote pc
```

sudo ssh -L 5901:vncserverip:5900 yourusername@sshserverip 

```
Optionally you can put 
```

-pxx 

```
at the end, with xx being your custom ssh port number.

Finally, on the remote machine connect vnc to localhost:5901

---

### Post by digimatic on 2006-03-27
What you really want here is a VPN...using ssh to do this is a bit like using a Mini for a road trip across the states...sure it's possible but there are more comfortable ways of doing it.

ssh can be used to forward ports...but generally you do this on the same machine that is running the ssh server.

I'd suggest doing some searches on Linux VPN's or find a copy of the definitive book

"Building Linux Virtual Private Networks (VPN's)" by Oleg Kolesnikov and Brian Hatch
ISBN 1-57870-266-6

If you really want to do it with ssh then you need to set up a ssh tunnel on your linux box using the -L option (take a look in the ssh man file) and then point that at the vnc port (5900 in the case of windows) of the windows machine...but it's going to be a bit of a challenge to get working.

---

### Post by digimatic on 2006-03-28
[QUOTE=Jason_25]I think you want to do ssh port forwarding which is easy to do.

On the pc that you want to be the ssh server
```

sudo apt-get install openssh-server

```
Then from a remote pc
```

sudo ssh -L 5901:vncserverip:5900 yourusername@sshserverip 

```
[/QUOTE]

Not sure that will do what he wants..it's close but that will tunnel VNC over ssh from the client  to a remote machine...This guy wants the VNC host to be a different machine to the SSH server.

<remote>---[internet]-----<Ubuntu SSH server>--<Windows box with VNC>

At least I think that's what he wants.

---

### Post by Jason_25 on 2006-03-28
That's exactly what the command does.  If you want to forward to the same machine as the ssh server, just specify localhost in place of vncserverip.

---

### Post by digimatic on 2006-03-28
[QUOTE=Jason_25]That's exactly what the command does.  If you want to forward to the same machine as the ssh server, just specify localhost in place of vncserverip.[/QUOTE]


ooops my mistake...you're right, don't know what I was thinking this morning :D

---

### Post by AllBuntu on 2006-03-28
Thanks fort all help, somebody does know sshd!

You got it right, I have an Ubuntu box with an open port that I want to use both with VNC and as a bastion-computer to access other computers on the same firewalled subnet, a mixture of Windows and Ubuntu.

I will try the excellent advice given, and later post a summary how I got it to work (a little self-confident here)!

---

