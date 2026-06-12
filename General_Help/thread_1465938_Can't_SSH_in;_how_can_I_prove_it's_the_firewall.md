---
title: "Can't SSH in; how can I prove it's the firewall?"
date: 2010-04-29
forum: General Help
---

### Post by yah.shoor on 2010-04-29
My sysadmin has let me squeeze an Ubuntu server in amongst his many Windows servers. I'm setting it up to let a third party ssh into it, but I'm having some difficulties getting it to work. There's a Sonicwall in between this server and the net. Can anyone suggest a way for me to prove that the firewall is configured incorrectly?

We've configured the firewall, and it looks like it ought to work. We set up ping and ssh services in the firewall admin interface. I can ping the server, no problem, but I can't ssh into it at all. sshd_config is set up with very generic settings; I haven't changed the port it's listening on or anything in the ListenAddress field. If I try to ssh to localhost from the server's command line, it  gives me a comforting RSA key warning.

When I check the log after restarting ssh, everything looks okay to me. It's not complaining about being unable to bind the port to the address or anything. Seems obvious to me that something is wrong with the firewall, but perhaps I'm wrong. The only ways I can think of to actually prove that the firewall is misconfigured are:

1) Remove the firewall entirely, and attach the server directly to the net. Ugh.
2) Set up ufw on the server, remove the firewall entirely, and attach the server directly to the net. 

What am I missing here?

---

### Post by Iowan on 2010-04-29
Can you connect to the SSH server from the same side of the firewall (or does the server connect directly to FW)?

---

### Post by yah.shoor on 2010-04-29
Whoops, I forgot a step: it's all alone on the firewall right now, but last night I attached a laptop and was able to ssh to the server on its internal IP address. I got that same comforting RSA key warning.

---

### Post by yah.shoor on 2010-04-29
If the bits were getting to my Ubuntu machine at all, they'd show up in the logs, right? The only things I see in the logs are me pitifully stopping and restarting the ssh server.

---

