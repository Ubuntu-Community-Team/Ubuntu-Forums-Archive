---
title: "SSH with X11 forwarding"
date: 2012-07-05
forum: General Help
---

### Post by Penfold1971 on 2012-07-05
I'm re-attempting to set things up so that I can connect to my Ubu machine from my iMac. Eventually, on the Ubu machine, I want to disconnect the monitor, keyboard and mouse and also, internally, the optical drive, and just run things remotely from my iMac.

So far, I've installed and configured a ssh server on the Ubu machine - or at least, I think I have. It was a couple of days ago, and now I'm back onto it, I want to check that things are as they should be.

**First step - how can I check to see if I really did install the ssh server?**

This might seem a daft question, but I'm very much the novice here.

---

### Post by zero2xiii on 2012-07-05
Hay,

Most people here will suggest you use a VNC server. So, with that said:

I have no experience on Mac but to connect from a linux machine to a ssh server you type:

```
ssh ssh_user@192.168.1.1
```
the ssh_user being the user set up to be able to use ssh (or any user ON the machine)

To use x11 forwarding:

```
ssh ssh_user@192.168.1.1 -Y
```
or
```
ssh ssh_user@192.168.1.1 -X
```

But i think if I remember correctly, -Y is desired because of beter security or something. Can't remember, just know people suggest it OVER -X. -X being the fall back.

Cherz

---

### Post by Penfold1971 on 2012-07-05
Thanks. But how can I firstly check, while on the Ubu machine, to see if ssh server is installed?

---

### Post by zero2xiii on 2012-07-05
Hay,

Sorry I missed that part hahaha.

```
ssh localhost
```
```
ssh $(whoami)@127.0.0.1
```

This should connect if the server is set up correctly. But check it from the mac? Why not? Just ssh into it without the -Y or -X flags... and then see if it connects...

Cherz

---

### Post by Penfold1971 on 2012-07-05
Hmmm.

This is what happens when I use Terminal on my iMac:

penfolds-imac:~ penfold1$ ssh localhost
ssh: connect to host localhost port 22: Connection refused
penfolds-imac:~ penfold1$ ssh -X localhost
ssh: connect to host localhost port 22: Connection refused
penfolds-imac:~ penfold1$ ssh $(whoami)@127.0.0.1
ssh: connect to host 127.0.0.1 port 22: Connection refused
penfolds-imac:~ penfold1 ssh -Y localhost
ssh: connect to host localhost port 22: Connection refused
penfolds-imac:~ penfold1$ 

As you can see, I tried three ways to 'ssh localhost'

---

### Post by Penfold1971 on 2012-07-05
On my Ubu machine:

The authenticity of host 'localhost (127.0.0.1)' can't be established

---

### Post by SeijiSensei on 2012-07-05
That tries to connect to an SSH server on the Mac itself via the "localhost" interface.

From the Mac, you want to use

```

ssh -X you@server_ip

```

You can use "ssh you@localhost" on the Ubuntu box to test that the server is listening.

The first time you connect to a machine you'll be told that the ssh client can't determine the authenticity of the remote server.  If you say "yes" at the prompt, the client will add the server's public key to its local store (in /home/you/.ssh/authorized_keys), and you won't see the prompt again unless the server has a new IP address or new name.

---

### Post by zero2xiii on 2012-07-05
Ooooh snap,

Seems like it might seem somewhat dubious on what I actualy meant haha. I apologize.

+1 for SeijiSensei.

On the MAC use ssh -Y/X user@ubuntu_ip 
On the Ubuntu machine use the localhost version.

Again I apologize.

:neutral:

---

### Post by Penfold1971 on 2012-07-05
Well, this is from the screen of the X11 Terminal on my iMac :

[FONT="Courier New"]bash-3.2$ ssh -X [email]penfold@penfold-Z68MA-D2H-B3.local[/email]
[email]penfold@penfold-z68ma-d2h-b3.local[/email]'s password: 
Warning: untrusted X11 forwarding setup failed: xauth key data not generated
Warning: No xauth data; using fake authentication data for X11 forwarding.
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-26-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

Last login: Thu Jul  5 22:56:54 2012 from penfolds-imac.local
penfold@penfold-Z68MA-D2H-B3:~$ [/FONT]

Can you help me unpack that and make some sense of it, please?

---

### Post by Penfold1971 on 2012-07-06
Does the message I copied from Terminal, in the last post, mean that I have connected successfully with the Ubu machine?

If so, I only have a limited number of things I want to do on the Ubu machine remotely from my iMac. They include :

1)  Check to see if there are any updates to be downloaded _**and**_ download them

2)  Restart (possibly) on occasion

3)  Shut Down

4)  Start up again

I have this machine exclusively for running Folding@home. With the help of folk over on the F@H forums, I've got full control of the f@H client (running on the Ubu machine) from my iMac.

---

### Post by SeijiSensei on 2012-07-06
Just a general hint for future troubleshooting.  Nearly any standard error like the ones you posted have been asked about by people on the Internet.  If you search Google for the text of the error, as I just did, you'll often find the answer.  Here's a long, somewhat technical explanation for the "Warning: untrusted X11 forwarding setup failed: xauth key data not generated" error:

[http://cygwin.com/ml/cygwin-xfree/2008-11/msg00154.html](http://cygwin.com/ml/cygwin-xfree/2008-11/msg00154.html)

The practical solution is to use "ssh -Y" instead of "ssh -X".  This seems to be an issue with the Cygwin client that Apple uses.  The standard openssh client on most Linux boxes doesn't report this error.

As to your other questions, yes you did make a connection.  

As for running updates, there's no reason you need a graphical application to do that.  Just run 

```
sudo apt-get update
sudo apt-get upgrade
```

from the command prompt after you are connected.

To restart the machine use "sudo reboot".  To bring down the machine and turn it off, use "sudo poweroff".  For more details, see [http://www.computerhope.com/issues/ch000606.htm](http://www.computerhope.com/issues/ch000606.htm).

I take it this is your first encounter with Linux.  Most simple tasks like the ones you describe are easily handled by typing commands at the prompt and don't require a graphical application at all.

---

### Post by Penfold1971 on 2012-07-06
> **SeijiSensei said:**
> I take it this is your first encounter with Linux.  Most simple tasks like the ones you describe are easily handled by typing commands at the prompt and don't require a graphical application at all.

I finished building my new machine on Monday 25th of June, and had Ubuntu 12.04 running on it later that day. It's the first machine I've ever built, and pre-25th June, I'd never seen Ubuntu, nor any variety of Linux, on a screen before, let alone use it. So, yes, I am very, very new to Linux :)

I'll be happy enough using commands remotely instead of using a GUI. There are so few I'll need, if everything goes well. I'll just collect and learn the ones I need as and when I need them.

I've just re-connected with the Ubu machine using Terminal on my iMac and after entering my password, the next lines are :

[FONT="Courier New"]Warning: No xauth data; using fake authentication data for X11 forwarding.
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-26-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
[/FONT]
So it looks as if "ssh -Y " reports the same error as "ssh -X" ?

As for the rest, I got :

[FONT="Courier New"]1 package can be updated.
1 update is a security update.[/FONT]

Two questions :

1)  Should I do a restart after a security update?

2)  What is the difference between 
[LIST][FONT="Courier New"]sudo apt-get [COLOR="Red"]update[/COLOR][/FONT]
[/LIST]
and
[LIST][FONT="Courier New"]sudo apt-get [COLOR="Red"]upgrade[/COLOR][/FONT]
[/LIST]

I thank you for helping me with all this. It's a bit of a mystery at the moment, and I'm very wary of making blunders and causing chaos.

---

### Post by Penfold1971 on 2012-07-06
**P.S.**  I'm also equally new to the use of Terminal commands.

---

### Post by SeijiSensei on 2012-07-06
You only need to restart the server if the operating system "kernel" is updated.  However if you have a running "daemon" process, like the Apache web server, you'd need to restart that process itself after an update with "sudo service servicename restart", e.g., "sudo service apache2 restart".

"Update" and "upgrade" perform two different tasks.  Update checks with the repositories and rebuilds the local package database on your computer.  You run it before upgrading to make sure your computer will be requesting the most up-to-date versions of any software on your machine.  The "upgrade" directive actually downloads the replacement files and installs them on the machine.

I suggest you browse some of the Ubuntu documentation, particularly the [Server Guide](https://help.ubuntu.com/12.04/serverguide/index.html). Here's the [page about updates](https://help.ubuntu.com/12.04/serverguide/apt-get.html).

---

