---
title: "how to monitor a socket"
date: 2010-08-10
forum: General Help
---

### Post by ashahzad4 on 2010-08-10
Hi ALL, 
           I want to know that through which commands i can monitor a socket that has been created on my machine to know which connections it has and which data it receives and sends.

I tried lsof |grep TCP, it does tells me that my TCP socket is connected to some other machines socket, but it doesnt tells me what is being communicated over the socket.

Ahmad

---

### Post by vvsiva007 on 2010-08-10
try using netcat --- netcat  localhost portnumber

---

