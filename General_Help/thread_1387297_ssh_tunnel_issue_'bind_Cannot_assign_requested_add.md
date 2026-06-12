---
title: "ssh tunnel issue 'bind: Cannot assign requested address'"
date: 2010-01-21
forum: General Help
---

### Post by crowds0 on 2010-01-21
From my laptop, when I execute the following command to begin a ssh tunnel:

ssh -f localhost -L 2024:someserver.net:22 -N

I get the error: 'bind: Cannot assign requested address'

'ifconfig lo' gives:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2403 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2403 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:310225 (310.2 KB)  TX bytes:310225 (310.2 KB)

/etc/hosts:
127.0.0.1       localhost

So loopback seems to be up and running, I just can't seem to bind a port to it.  I can tunnel from other machines so I must have something configured wrong.  I'm running NetworkManager and Xubuntu 9.10 2.6.31 under Karmic. I've Googled this quite a bit and looked around on the forum to no avail so any suggestions or help would be most appreciated.  Thanks!

---

### Post by Brandon Williams on 2010-01-23
First, I'm confused by your command line. With that command, your local machine will be both sides of the tunnel, since the target host for the ssh command is localhost. Maybe this is what you intended:
```
ssh -f someserver.net -L2024:localhost:22 -N
```

That's not the cause of your problem. It just looks strange to me.

As for the bind, are you certain that you don't already have a process bound to port 2024 on localhost? Run 'sudo netstat -lnp | grep :2024' Is anything listed? And if so, do you recognize the pid/command of the binding process (it's the last field in the line)?

---

### Post by crowds0 on 2010-01-23
Thanks Brandon for the reply. I tried both our commands on a different computer and they both seemed to do what I wanted, 'ssh localhost' puts me on the remote machine.  This is strange, i'm probably doing something wrong.  

Anyhow, on my computer I try using your command and I still get the same error.  I ran netstat and it doesn't show anything on that port, so it seems to be free.  I also tried some arbitrary ports as well, and still have the problem.  

Any more suggestions would be most welcome.

---

### Post by pbrane on 2010-01-23
I can't get your command line to work, but Brandon's does work for me. Not much help but it seems that it's something on that particular machine.

You might try 'sudo netstat -lnp | grep 127.' That will show you what ports are bound to localhost (127.0.0.1)

---

### Post by Brandon Williams on 2010-01-23
When it comes down to it, neither one of the commands is particularly meaningful, since it doesn't make sense to open an ssh tunnel to another machine in order to communicate with that machine via ssh. Since you have direct ssh access to the remote machine, both command lines will appear to work. You would get a better idea of which one of the command lines is correct if you were attempting to tunnel to a service that you can get to from the remote machine but not the local one.

As for the bind failure, I tried a few different things, and the only way I could find to generate that particular error was to provide an invalid bind address to the -L flag. In other words, if I do this:
```
ssh -f someserver.net -L192.168.2.2:2024:localhost:22 -N
```
The command will fail with that specific bind error code, since 192.168.2.2 is not configured on my local machine. This makes it seem like sshd is using a bad default bind address for the tunnel. Try this command line:
```
ssh -f someserver.net -L127.0.0.1:2024:localhost:22 -N
```
This will explicitly tell it to bind using IP address 127.0.0.1, which is what it should already be doing by default. Does it work if you do that?

---

### Post by crowds0 on 2010-01-24
That was really helpful, your command does what I want it to - enable me to start a vnc session with a host computer over ssh.  

So it seems I need to specify 127.0.0.1 as the IP of localhost.  In /etc/hosts I have the line:

127.0.0.1       localhost

which would lead me to believe that this is not necessary.  Is there something i'm missing? Is there somewhere else I need to assign the IP 127.0.0.1 to localhost? 

Also, the ssh command I have above does not work for what I had intended it to do, thanks for the correction.

---

### Post by pbrane on 2010-01-24
I use a command like to create a dynamic port forward to my server. It allows me to access my router which is not accessible from the internet otherwise. I don't use port 22 for ssh either, too many port sniffers hitting on that.

```
ssh -D2024 user@someserver.net
``` This allows any protocol to work over that tunnel.

---

### Post by Brandon Williams on 2010-01-24
I don't think that the issue is in your /etc/hosts file, unless there's more than one listing for localhost there. The other one would have to be invalid _and_ it would have to be the one selected by ssh for this purpose, which seems unlikely.

Try running the ssh command without explicitly specifying 127.0.0.1 as the binding for the -L flag, remove the -f and -N flags, and include -v to get debug output. In other words:
```
ssh someserver.net -v -L2024:localhost:22 -o ExitOnForwardFailure=yes
```

Look for the line that starts with: 'debug1: Local connections to <somevalue>:2024 forwarded'. What do that line and the next few say? The 'Local connections ... forwarded' line should say LOCALHOST where I've marked out <somevalue>. The next line or two should indicate good addresses for LOCALHOST. Do they?

---

### Post by crowds0 on 2010-01-26
So this is the output from the command, after the point you specify:

debug1: Local connections to LOCALHOST:2024 forwarded to remote address localhost:22
debug1: Local forwarding listening on 127.0.0.1 port 2024.
debug1: channel 0: new [port listener]
debug1: Local forwarding listening on ::1 port 2024.
bind: Cannot assign requested address
debug1: channel 1: new [client-session]
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8

Clearly it doesn't like '::1' 

/etc/hosts/ has the ipv6 line:
::1     localhost ip6-localhost ip6-loopback

But I tried commenting that out and running your command again and it still gave the same results as above.  Any ideas?

---

### Post by Brandon Williams on 2010-01-27
Hmmm ... the only thing I can think of is that you don't have an IPv6 localhost address configured on your system. The problem should still clear up by removing localhost from that line in /etc/hosts, though, which should cause the resolver to stop returning that address when you lookup localhost.

To work-around the problem, you've got two choices: explicitly specify 127.0.0.1 as the bind address for every portforward, as in comments 5 and 6 above, or add the -4 flag to every ssh command line so that it uses IPv4 only, e.g.:
```
ssh -4 -f someserver.net -L2024:localhost:22 -N
```

To continue diagnosing, the next step is to determine whether the IPv6 localhost address is configured on your system. What is the output from this command line?
```
ip add show | grep inet6
```

---

### Post by crowds0 on 2010-01-27
Forcing ipv4 (-4) seems to work too, so I would think that the issue would be ssh trying to assign the inet6 address to localhost, but running the commands:

```

ip add show | grep inet6

```

```

ip addr show | grep inet6

```

don't return anything.  Any ideas?

---

### Post by Brandon Williams on 2010-01-29
Have you previously done something to disable IPv6 on your system? 9.10 will configure localhost ipv6 addresses by default, so if they aren't there, my best guess is that IPv6 has been disabled.

I suggest that you comment out all lines related to IPv6 in /etc/hosts, reboot, and try again without either the IPv6 related work-arounds (i.e. use your original command line). It could be that when you removed the IPv6 localhost entry previously that there was some cache somewhere continuing to screw things up. That seems unlikely, but it's my best guess at the moment.

---

### Post by hackerb9 on 2011-02-19
> **crowds0 said:**
> running the command: "ip addr show | grep inet6" didn't return anything.  Any ideas?

A ha! That's the problem.  The loopback device "lo" should be set to [FONT="Fixedsys"]::1[/FONT].

Try this,

```

sudo ip addr add ::1 dev lo

```

I'd bet dollars to donuts that ssh tunneling will work after that.  Of course, you'll need to figure out where to put that so that it gets set automatically when you boot up.  I can tell you how my machine works, but unfortunately it might not help you much. Network Manager always mangles my network, so I disabled it.  Instead of nm, I use the following in [FONT="Fixedsys"]/etc/network/interfaces[/FONT],

```

# The loopback network interface
auto lo
iface lo inet loopback

```

If you change that file, you can use ```
sudo ifdown lo
sudo ifup lo
``` to make it take effect without having to reboot.  Let us know if that solves the problem.

---

