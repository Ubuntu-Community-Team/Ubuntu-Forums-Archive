---
title: "ssh port forwarding fails"
date: 2006-04-22
forum: General Help
---

### Post by seraglio on 2006-04-22
The following fails to provide port forwarding:

ssh -N -g -L 7000:server:7000 user@host

It produces a "bind: Address already in use" error, even though netstat shows there is nothing happening on the port beforehand.

Thanks for any insight, help, etc.

---

### Post by dblood on 2006-04-25
I was just struggling with this for a couple hours and finally figured it out.

If you add the -v option you see the following:

debug1: Connections to local port 5001 forwarded to remote address localhost:5000
debug1: Local forwarding listening on :: port 5001.
debug1: channel 0: new [port listener]
debug1: Local forwarding listening on 0.0.0.0 port 5001.
bind: Address already in use

After staring at this a half dozen times I realized what it was doing, opening up the port on both IP6 and IP4.  Because IP6 aliases IP4 this is causing an issue.  In short, just add the -4 option to the ssh command and it should work.

ssh -4 -g -L 5000:localhost:5000 user@host

Hope this helps

---

