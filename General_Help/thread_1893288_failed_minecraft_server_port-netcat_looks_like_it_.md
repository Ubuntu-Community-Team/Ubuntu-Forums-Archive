---
title: "failed minecraft server port-netcat looks like it does nothing"
date: 2011-12-09
forum: General Help
---

### Post by uh20 on 2011-12-09
trying to keep a listen for a minecraft server, i read a guide and did this
java Xms1024M -Xmx1024M -jar craftbukkit.jar nogui | netcat -l -p 25565

problem is when netcat runs, it rants about what it is, and my minecraft server still gets its annoying little *FAILED TO BIND TO PORT* message

upon any nc or netcat command, it spits out this text
~netcat -l -p 25565
~This is nc from the netcat-openbsd package. An alternative nc is available
in the netcat-traditional package.
usage: nc [-46DdhklnrStUuvzC] [-i interval] [-P proxy_username] [-p source_port]
      [-s source_ip_address] [-T ToS] [-w timeout] [-X proxy_protocol]
      [-x proxy_address[:port]] [hostname] [port[s]]

any ideas on whats happening?

---

### Post by uh20 on 2011-12-09
nvm it fixed itself, turns out java itself screwed up when another java applet was up, although it had nothing to do with the port, it was the problem

---

