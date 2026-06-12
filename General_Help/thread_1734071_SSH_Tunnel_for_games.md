---
title: "SSH Tunnel for games"
date: 2011-04-19
forum: General Help
---

### Post by ffriozi on 2011-04-19
Hello, today i got one dedicated server to tunnel gamers connections to the server.
but i got some doubts

how to do an script like this:


[HTML]Using username "tunnel".
Last login: Mon Apr 18 17:23:07 2011 from 187.115.29.110
Welcome TibiaTunnel New System
www.tibiatunnel.com
.....................................................................[/HTML]

after i click "connect" the putty connect to the server and automatic start an script to keep alive the SSH (every "." is 1 minute) but if i press "CTRL+C" to stop the script the connection is lost.

how to do that??

Thanks!!

---

### Post by spikoley on 2011-04-20
Pressing Control + C will stop the script which will kill the connection.  The script is what is creating the connection.

What are you trying to do?

---

### Post by Lars Noodén on 2011-04-20
You might not need a script to keep the connection alive.  On the client side you can try the **ServerAliveInterval** and **ServerAliveCountMax** configuration directives.  Or on the server, you could set **ClientAliveInterval** and **ClientAliveCountMax**.

---

