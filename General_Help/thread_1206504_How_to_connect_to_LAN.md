---
title: "How to connect to LAN?"
date: 2009-07-07
forum: General Help
---

### Post by kaustubh.bansal on 2009-07-07
I had a broadband connection that requires username and password for a few days. I used **sudo pppoeconf** to set up the connection.
Now I want to revert to my original regular LAN connection but i dont know how to do it. Can anyone help?

---

### Post by fragos on 2009-07-07
PPPOE is probably to accomodate a DSL modem. You connection to that moden is Ethernet LAN. Don't use PPPOE and your Ethernet port is ready for LAN connection. If this is a home LAN I recommend you get a wireless router -- they have 4 wired LAN ports. If the LAN is at work you will need to configure your browser for an Internet proxy.

---

### Post by kaustubh.bansal on 2009-07-08
Hello, I used **pppoeconf** just once as i had to connect to dsl at home.
Now i'm back to college where LAN connects directly. I have set proxy but LAN is not even being recognized

---

### Post by fragos on 2009-07-08
> **kaustubh.bansal said:**
> Hello, I used **pppoeconf** just once as i had to connect to dsl at home.
Now i'm back to college where LAN connects directly. I have set proxy but LAN is not even being recognized

Check with your schools IT department. They be using something like MAC blocking.

---

### Post by kaustubh.bansal on 2009-07-10
It appears my ethernet is disabled in ubuntu. I have a dual boot system and LAN connects fine in windows. So, i guess my MAC is not blocked.
The problem must be with ethernet. But i don't know what caused it and how to re-enable it.

---

### Post by Peter09 on 2009-07-10
Have you got the network icon (top right) if so what do you see when you left click, and also when you right click.

can you post the output of the terminal command

```
ifconfig
```

---

### Post by kaustubh.bansal on 2009-07-10
On left click, i have the following options
(Note: Italics denote greyed options)

[FONT="Lucida Console"][I]**Wired Network**
device not managed
**Wireless Network**
wireless is disabled[/I]
VPN Connections >
[/FONT]

On Right Click, I have

[FONT="Lucida Console"]Enable Networking (ticked)
Enable Wireless
Connection Information
Edit Connections
About[/FONT]

Here's the result of ifconfig:
```

kaustubh@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:832 (832.0 B)  TX bytes:832 (832.0 B)


```

(Note: I have temporarily disabled Wireless to check ethernet)

---

### Post by Peter09 on 2009-07-10
When you connect the cable (ethernet) into the back of your machine do you see any lights on the connector?

---

### Post by kaustubh.bansal on 2009-07-10
Yes, I do see the LEDs blinking

---

### Post by ZhuaSD on 2009-07-22
What distro are you on?  Pls give system specs.

You connected directly to a LAN right out of the box originally?  

NO configuration at all?

---

