---
title: "ports locked ? after failed install"
date: 2012-01-26
forum: General Help
---

### Post by palloy on 2012-01-26
Is there anyway that ports can get permanently blocked after a failed install ?
If **netstat -lnp** says nothing is listening on port 80, how can a newly installed web browser be prevented from using port 80 ?

Lubuntu 11.10 + LXDE
Citadel install failed "cannot start server" and netstat showed the web component listening on :80 and :443, but the POP, IMAP and SMTP components NOT listening on :110, :143, :25, :995, :993, :465 , and CPU usage running at 50% + a few percent for the things I could see in Task Manager.
I got very confused and ended up uninstalling the lot. That got the CPU usage back to normal.

But subsequent installs of alternative packages don't do any better. They all seem to think something is already listening on their ports. I could go into the details, but I think the problem lies at a deeper level common to all. A lock on the ports being left on ?

I don't have any idea where I might find such a thing in the filesystem, or which tools to use to diagnose it.

---

### Post by imachavel on 2012-01-26
there is no way ports can get permanently blocked. But errors can cause a transmission failure. Let me re read this and see if I can't find a better answer to your question

have you tried reinstalling, or using a different browser?

---

### Post by palloy on 2012-01-26
I've now got a web server (Abyss) running. Connection from browser to 127.0.0.1:9999 works OK. Browser access to HTTP server on :8080 OK, which hadn't been used before.

When I reconfigure it to listen on :80 it seems happy to accept that, and Restart says it works OK, but netstat shows it isn't listening on anything, and I can't connect to it with a browser.  Reconfigure it back to :8080 and restart and it works OK.

---

### Post by palloy on 2012-01-27
I have written a little PHP script that issues a stream_socket_server() against a range of ports. It succeeds in opening port 80 , and fails to open port 8080, which the web server is using - confirming netstat.  Results attached

And yet the web server's port still can't be switched from :8080 to :80 - "listening error".

I should expect there to be some sort of register of opened ports, so that they can't be opened again. Where is that in the filesystem ? What module is responsible for checking things like that ?

---

### Post by palloy on 2012-01-27
OK, port 80 is not 'already in use', it is actually being blocked because I was not running as root and this is a lower range port (0-1023).
For some reason running under **sudo** isn't the same as running as root after **sudo su** .
If somebody would like to explain that to me I would be grateful.

There is scope for improving the error responses when not running as root. I suppose that is an application's responsibility.

Anyway running as root solves the problem.

---

### Post by palloy on 2012-01-27
- except that running a server as root is frowned upon.

I was thinking that if I ran as root, then closed down cleanly, that would get rid of the apparent blockage to running normally. But does it ?

I need some guidance - you know : [SIZE=3]General Guidelines[/SIZE]** 1. There are no stupid questions.**

---

