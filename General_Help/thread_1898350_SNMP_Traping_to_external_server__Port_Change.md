---
title: "SNMP Traping to external server / Port Change"
date: 2011-12-21
forum: General Help
---

### Post by Rattlehead_ie on 2011-12-21
Hi guys,
I'm a complete novice (n00b) and would appreciate some help and assistance in this case. I am trying to setup a machine here to sent out SNMP traps to an external server. These traps must also be sent out via a different port than the standard UDP 162. 

The server is being used for RADIUS and I need it to report on users logging in, sessions and all that. I've entered my config in /etc/snmp/snmpd.conf and happy that locally the traps are there when I do a snmpwalk but have no idea where to go from there.
Where to change the port
How to report on the radius information
If this config is done in snmpd or do I need to create snmptrapsd.conf etc

Again any pointers would be greatly appreciated.

---

### Post by The Cog on 2011-12-21
I'm having trouble understanding what you want to do here.

Some explanations (apologies if you already know this):

RADIUS is an authentication protocol. 
A RADIUS client (a PC, network router etc) will ask the RADIUS server to verify usernames/passwords etc. when someone tries to log on to the client machine. It may also ask the RADIUS server to authorise things they're trying to do, and may also send usage accounting information to the RADIUS server. 

SNMP is a management protocol. It is normally thought of in terms of a Manager machine and a number of Agent machines that the Manager is looking after. The SNMP protocol allows the Manager to use GET and SET requests to fetch and perhaps alter settings, counters etc. in each Agent. For example, a Manager might be periodically reading the CPU load of a number of servers so that it can produce graphs. In this context, the Manager is actively sending GET or SET requests to the Agents and the Agents are passively waiting for instructions from the Manager. These management requests are normally sent to port 161 of the Agent. When you use snmpwalk, you are taking the role of a Manager and GETting a collection of status variables from an agent.

SNMP Traps are a mechanism whereby an Agent will, of its own volition, send a TRAP to a Manager. This is intended to report unexpected events, such as a the occurrence of a fault or of a user logging in. These TRAPs are normally sent to port 162 of the Manager. The Manager should do something appropriate like logging the event, flashing a warning, or closing the reinforced blastproof doors.

The three mechanisms described above are essentially independent. Quite often, an SNMP manager will perform both SNMP functions - regularly querying the status of its flock of agents, and doing something like raising an alarm if it receives a trap from one of its flock. I'm sure that you can't receive traps with snmpwalk though, so I'm not sure exactly what you are looking at there.

I don't see how this ties in with RADIUS at all, except unless you want the RADIUS server to send SNMP traps to the SNMP manager whenever it allows (or refuses) user access. I would normally expect the RADIUS server to do its own logging of such things though.

Maybe you can explain in more detail what you want to achieve?

---

### Post by Rattlehead_ie on 2011-12-21
Sorry COG, I was a little bit narrow minded and typing quickly this am when I wrote this.

The RADIUS server (i.e agent) I want to trap back to a Manager (in my specific case its Netcool) when a auth session has been requested from a client whatever it maybe. So if a user logs in and requests access to whatever its requesting that the Radius server receives this request and traps it sending info to netcool alerting it that a user has logged in or logged out, maybe even if the user has typed the wrong password.

---

### Post by The Cog on 2011-12-21
That makes sense. I think you need to be looking at the configuration options for the RADIUS server for this, to get it to send traps to a manager server somewhere. 

You don't need to be looking at snmpd with is an agent listening for GET/SET commands from a Manager, and you don't want to be looking at snmptrapd which is a Manager process listening for traps from elsewhere.

I'm not familiar with any RADIUS servers, so I don't know if any of the common ones are able to generate traps at all. Even if they can, sending to a port other than 162 might be problematic - may even involve using NAT to change the destination port in transit.

---

### Post by jonobr on 2011-12-21
Hello


Which version of radius are working on?

---

