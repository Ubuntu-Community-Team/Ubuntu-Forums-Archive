---
title: "Need Help with Samba"
date: 2010-10-12
forum: General Help
---

### Post by dave21458 on 2010-10-12
I had my Ubuntu Linux 8.10 Server working fine. I moved the location. The only change was the IP. I changed interfaces to reflect my new IP. Everything works except now I can not connect to my server using my laptop running XP. Before the move I had no problem connecting to the server with my laptop. Windows can see the server but will not connect. Can changing the server IP affect Samba?

---

### Post by Carlbc18 on 2010-10-12
try removing the previous network connection on your xp laptop by doing this in a cmd window:

```
net use \\server name\share name /del
```

Also, if that doesn't work, after you execute the command via command line, attempt a restart.  Sometimes the delete is a little finicky. 

if the command works or you've restarted attempt to reconnect via start-->run--><path to samba share>

---

### Post by dave21458 on 2010-10-12
I had disconnect old connections (mapped as drives) previously.
I did try 'net' commands no luck. path not found error.

---

### Post by Carlbc18 on 2010-10-12
I assume you have tried a restart?  Also, is your samba share showing up as a mapped drive?  if so, you could do:

```
net use <drive letter> /delete
```

---

### Post by pricetech on 2010-10-12
What kind of error message are you getting when it fails ??

---

### Post by dave21458 on 2010-10-12
I tried restart many times. I had disconnect mapped drive first.
Error Message is Basically 
"Server not accessible. You may not have permission...."
"The network path not found"

---

### Post by dave21458 on 2010-10-13
:)The problem was with UFW the firewall would only allow connection from previous IP. This would stop Samba from issuing the IP for the server to Windows. 
I discovered this when use 'net use \\myserver\share' on my laptops XP command window. This would return a "Network Path not found" Windows error code 53. 
Then checking iptables on server.

---

