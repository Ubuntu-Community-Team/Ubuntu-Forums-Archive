---
title: "How do I parse nmap output to grab &quot;port/proto name&quot; of service"
date: 2012-02-01
forum: General Help
---

### Post by Dulus0 on 2012-02-01
Hi there, i am using attached php script, to gather all available services on ip address, using nmap, through php web ui. i am stuck, i need help to parse the output which nmap is generating and store in some variables, i need the port number(example: 80), ip proto name (tcp/udp), and service name (http) 
the output of nmap looks like this:
Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2012-02-01 20:22 CET
Interesting ports on localhost (127.0.0.1):
Not shown: 65525 closed ports
PORT      STATE SERVICE
21/tcp    open  ftp
53/tcp    open  domain
80/tcp    open  http
443/tcp   open  https
631/tcp   open  ipp
953/tcp   open  rndc
3306/tcp  open  mysql
9000/tcp  open  cslistener
10000/tcp open  snet-sensor-mgmt
28029/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.81 seconds




and i need do parse the port number, proto name and service name from it. i then need to store them in DB, but thats another problem right now i need to parse it.

so basically i just need these values parsed to some variables, so i can work with them

 i am not a programmer nor a php programmer, but i have some basic understanding of programming (i did a bunch of programs in C#), an a complete linux newbie.

---

