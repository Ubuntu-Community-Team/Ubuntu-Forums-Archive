---
title: "Client-Server Connection with Ubuntu"
date: 2011-11-26
forum: General Help
---

### Post by mobius129a on 2011-11-26
Hi all,

I have some questions regarding a system I want to set-up. First, I'll give an overview of requirements.

**REQUIREMENTS**

**Components**

[LIST]
[*]Client machine (X-server) has 2.80GHz and 2GB RAM (I think I'll be able to get better than this but this is a worst-case scenario)
[*]Terminal/Application Server machine (X-client) is a Dell PowerEdge 2500
[*]Data server machine is a Dell PowerEdge T310
[*]Connections will be over standard ethernet cables
[/LIST]
[B]Functionality and Performance
[/B]
[LIST]
[*]All machines will be varying
[*]The client should be able to perform the following with the terminal/application server:
[*]Perform system administration of both servers
[*]Launch processor-intensive (but not graphics-intensive) applications via GUI
[*]Build applications with application server software via GUI
[*]Build intranet pages with content management system via GUI
[*]Access data and files via GUI
[*]The terminal/application server should use the data server as the store from which user files are accessed. The data server will essentially have a flat file structure, while the terminal/application server will render html documents, etc. and add a layer of frontend organisation to the file system.
[/LIST]
**Security**

[LIST]
[*]Everything will be local, so this shouldn't be a problem
[/LIST]
**QUESTIONS**

What I specifically want to know is what protocols and software I should use to:
(a) connect the terminal/application server to the data server
(b) connect the terminal/application server to the client

From what I understand some of my options for (b) are as follows:

[LIST]
[*]Remote video connection, e.g. VNC, NX
[LIST]
[*]too processor-intensive for client?
[*]privileges?
[/LIST]
[*]SSH with X
[LIST]
[*]limited GUI functionality?
[/LIST]
[*]Fileshare
[LIST]
[*]only data?
[/LIST]
[*]Thin client server software, e.g. Edubuntu
[LIST]
[*]don't know whether this can provide functionality outlined above?
[/LIST]
[/LIST]

As for (a) I believe a fileshare should be sufficient, but am unsure of any higher-level software that may add extra functionality.

Any clarifications, corrections, etc. please say!
Thanks.

---

