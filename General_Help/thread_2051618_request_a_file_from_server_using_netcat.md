---
title: "request a file from server using netcat?"
date: 2012-09-01
forum: General Help
---

### Post by Kdar on 2012-09-01
How do I request a file from a server using netcat? Specifically without touching server computer and just executing a command from client side.

Before.. using ssh or scp, I used command something like this:

ssh user@server-addr "cat /home/user/file.tar" | cat > /dev/null
or
scp [email]user@server-addr:/home/user/file.tar[/email] > /dev/null

How can I do the same or similar with netcat? I am finding it a bit hard to understand how I would tell which file I want to receive from client side.

--
Before I have used netcat to send a file to a server without problem... 
on server: nc -k -v -l 1234 > /dev/null
on client: nc server-addr 1234 < file.tar
But the reverse of this would not really work, since I want to send a request from client side, asking for some file.

---

