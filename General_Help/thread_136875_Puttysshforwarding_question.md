---
title: "Putty/ssh/forwarding question"
date: 2006-02-26
forum: General Help
---

### Post by jenkins_t on 2006-02-26
I am using putty as my ssh client on Ubuntu and Mepis and XP. I have all 3 configured same. Under putty config, goto "ssh->tunnels" I add this data (w/o comments):

Source port: 7779     # used this port b/c I know its not being used
Destination: 192.168.0.34:80      #forward this ip's port 80 data

With XP and Mepis, I can open browser, type following in address bar...

[http://localhost:7779](http://localhost:7779)

and see what I normally see when I use direct IP, [http://192.168.0.34](http://192.168.0.34) , but with Ubuntu, I get a "Connection refused" message. 

I have tried disabling firewall using Firestarter. Is there anything else I can check?

---

### Post by pestilence4hr on 2006-02-26
In ubuntu, you don't need to use putty.  Just open up a terminal and type
```
ssh -N -n -L 7779:localhost:80 username@remotehost.com
```

In fact, if you use cygwin in windows, you can use this exact same procedure to establish the tunnel.  If you drop the -N -n you will get a shell, if you want that too.

---

### Post by bucksgt on 2006-02-27
that's true. however, in my particular situation, i need to send my ssh connections over a proxy on port 80 to an outside ssh server accepting connections on port 80.

the proxy setup in putty works great and i can get a shell on the remote server; however, i can't get the tunnel to work (as stated by the user above).

i know that i am configuring putty correctly, as the exact same setup works with putty on windows.

i have also tried to use proxy chains to 'proxify' native ssh, also to no avail. so, anyone have any idea on:
  -how to get ssh tunnels to work in putty?
  -how to proxify ssh?
  -any other ideas?

thanks.

---

### Post by jenkins_t on 2006-02-27
I got the shell working as per pestilence4hr's post, Thanks. 

But like bucksgt stated, why won't putty work? Now its not just the fact I have another way to go w/o putty, but WHY? :)

Edit:
I've compared the /etc/hosts files <> Ubuntu and Mepis and they are essentially the same. Also I cannot find anything in logs to point me in a direction concerning error.

---

### Post by jenkins_t on 2006-02-27
Bump

---

### Post by pestilence4hr on 2006-03-03
jenkins_t, I'm confused.  What command exactly did you use for ssh?  To connect to a server on port 80, you only need to do ssh -p 80 remotehost, so if you want to establish the tunnel as above, do 

```
ssh -N -n -L 7779:localhost:8080 -p 80 username@remotehost.com
```

Or am I not understanding something?

---

### Post by pornmetheus on 2006-11-07
Hello All.

I am familiar with this problem.  I am a long time fan of Putty, since I used it lots under windows before I moved to Linux.  I have used Linux as my workstation since the release of Mandrake Linux 9.0 and not long after I started using Linux (almost) exclusively, I found a *nix port of putty and had used it daily up until a year or so ago when it suddenly broke, following a security update that was applied to Mandrake (Mandriva) 2005. (It may have even been a kernel upgrade, can't remember.) It remained broken through Mandriva 2005 and 2006.  When I moved over to Kubuntu 6.06 I found that Putty (located in one of the dapper repositories) was still broken (ie: Putty started fine, would SSH/telnet into a variety of different hosts but wouldn't tunnel local ports over SSH).  Putty "Unidentified build, May 10 2006 23:17:22" running under kubuntu 6.10 (edgy) still doesn't have working tunnel support.

However if you apt-get wine (I have installed 0.9.22-0ubuntu3) and then run the latest windows binary of putty you should find that it works perfectly.

For those who ask "Why Use Putty? Just use ssh at the shell" the answer is simple: Corporate Firewalls.  If you are stuck behind a corporate firewall which requires username and password authentication to gain internet access, then Putty is a must have.

Robbo

---

### Post by sanitycheck on 2007-03-02
Is tunneling ever going to be fixed in Edgy's Putty?  I am apparently one of the very few people who need to use it, which is something of a surprise.  I need it because I use puttygen certificates originally created in the Windows version for remote access work.  For whatever reason I could not get ssh at the command line to work properly with the puttygen certificates; it kept asking for the passcode even though the passcode was correct.

I have to keep a Win98 VM with Putty for Windows running in it just for that reason (no Wine for me, I'm on 64-bit).  It's OK but my VNC and RDP tunneled screen size is limited by the VM window, and the performance probably isn't as good as running it under Kubuntu.

Are there (k)ubuntu alternatives to Putty, hopefully GUI alternatives, with puttygen certificate support? - thanks in advance

---

### Post by sanitycheck on 2007-03-04
By coincidence the February 2007 issue of Linux Magazine has an article on UniTTY, which offers the easy-setup forwarding of Putty and many other features such as a built-in VNC client:

[http://www.3sp.com/products/applications/unitty/unitty.jsp](http://www.3sp.com/products/applications/unitty/unitty.jsp)

It runs on Java but it uses some sort of half-script-half-binary installer, apparently because it is not open-source (I'd rather have a .jar and skip the installer).  I had no problems with installation on 64-bit Edgy.

They also have an installer for the Windows version.

---

