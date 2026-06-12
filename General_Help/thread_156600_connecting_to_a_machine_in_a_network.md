---
title: "connecting to a machine in a network"
date: 2006-04-07
forum: General Help
---

### Post by orlox on 2006-04-07
Hi, I need to do a report on a computer on my college, and they told me to "connect" to a machine thats in the network, and that haves the neccesary programs. The only thing they gave me is the name of the machine. How am I supossed to get the connection done? Any help?

---

### Post by lnxpwr on 2006-04-07
first try a ping to the machine:     ping <machine name>
if this works than you can try to reach it over telnet or ssh (but you need a username and  a password): 
telnet <machine name> 
or 
ssh <a valid username>@<machine name>

---

