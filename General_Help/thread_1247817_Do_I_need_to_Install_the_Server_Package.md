---
title: "Do I need to Install the Server Package?"
date: 2009-08-23
forum: General Help
---

### Post by greenco on 2009-08-23
I have a laptop and a PC and both of them are running Ubuntu v8.04. I have installed the OpenSSH Client and Server on both computers and I am able to share files and folders between them. The PC is connected to a wireless router and is connected to a high speed internet connection. I connect my laptop to the PC with a wireless connection. I can connect to the PC's printer and I am able to print files that are actually stored on my laptop. What I would like to do is to use my laptop, to locate and open a file, that is actually stored on the PC and then print that file. When I attempt this "OpenOffice" tries to connect me to a database. 

Can this be done or do I need to install the Ubuntu 8.04 Server package onto the PC?

---

### Post by blueridgedog on 2009-08-23
Try the "Places" menu then "Connect to Server" then specify ssh as the connection type.  Enter the IP address of the PC, which you can get from the PC with the command:

```
ifconfig
```

---

### Post by greenco on 2009-08-24
Thanks blueridgedog, but I have SSH installed and working just fine. I want to use the laptop to open a spreadsheet, that is on my PC, and then be able to print it without moving files from one computer to another.

---

### Post by blueridgedog on 2009-08-24
> **greenco said:**
> Thanks blueridgedog, but I have SSH installed and working just fine. I want to use the laptop to open a spreadsheet, that is on my PC, and then be able to print it without moving files from one computer to another.

Following the instructions I posted will give you a "mapped location" in Nautilus whereby you can browse and interact with files on a remote system.  It should do what you are looking for.

---

