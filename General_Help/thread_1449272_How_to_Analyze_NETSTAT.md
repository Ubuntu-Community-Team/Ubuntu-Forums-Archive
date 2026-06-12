---
title: "How to Analyze NETSTAT"
date: 2010-04-07
forum: General Help
---

### Post by ricyaun on 2010-04-07
I need to know what this means and what to do to fix this.  Thanks.

ric@ric-desktop:~$ netstat --inet -an
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:4128          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:4129            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.100:45625     72.14.204.147:80        ESTABLISHED
tcp        0      0 192.168.1.100:45622     72.14.204.147:80        ESTABLISHED
tcp        0      0 192.168.1.100:45623     72.14.204.147:80        ESTABLISHED
tcp        0      0 192.168.1.100:40577     207.182.145.66:80       ESTABLISHED
tcp        0      0 192.168.1.100:40584     207.182.145.66:80       ESTABLISHED
tcp        1      0 192.168.1.100:37800     72.3.246.59:80          CLOSE_WAIT 
tcp        0      0 192.168.1.100:40585     207.182.145.66:80       ESTABLISHED
tcp        0      0 192.168.1.100:45619     72.14.204.147:80        ESTABLISHED
tcp        0      0 192.168.1.100:40583     207.182.145.66:80       ESTABLISHED
tcp        0      0 192.168.1.100:45624     72.14.204.147:80        ESTABLISHED
tcp        0      0 192.168.1.100:40587     207.182.145.66:80       ESTABLISHED
tcp        0      0 192.168.1.100:49569     184.73.222.205:80       ESTABLISHED
tcp        0      0 192.168.1.100:40586     207.182.145.66:80       ESTABLISHED
tcp        0      0 192.168.1.100:40582     207.182.145.66:80       ESTABLISHED
udp        0      0 0.0.0.0:55779           0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*

---

### Post by ricyaun on 2010-04-07
sure didn't copy and paste well did it.

---

### Post by Calash on 2010-04-07
Not sure if I follow you.  What is the problem you are trying to fix?

---

### Post by ricyaun on 2010-04-07
> **Calash said:**
> Not sure if I follow you.  What is the problem you are trying to fix?

I have some hacker issues.  The netstat scans I was getting changed quite a bit after installing ids apps, and I would like to find out what all of the router addresses mean in the local addresses.  Also I was not getting the 127.0.0.1 local host addresses in the local addresses column before the install.  It would be a big help if the spaces carried over in the copy and paste.

---

### Post by ricyaun on 2010-04-07
Let me try this again with a screenshot.  I didn't realize it would turn out so bad.  Don't know how this is going to turn out.

/home/ric/Pictures/Screenshot-2.png

I see it didn't turn out well at all.
Any suggestions how to show you guys this netstat scan.

---

### Post by Chris Musampa on 2010-04-07
Paste your terminal text between code tags (hit the '#' symbol at the top when entering your post) and it should keep the formatting.

---

### Post by ricyaun on 2010-04-07
> **Chris Musampa said:**
> Paste your terminal text between code tags (hit the '#' symbol at the top when entering your post) and it should keep the formatting.

Thanks I will remember.  Have answered my own question now.  Thanks for the pointer

ricyaun

---

### Post by ricyaun on 2010-04-07
> **ricyaun said:**
> Thanks I will remember.  Have answered my own question now.  Thanks for the pointer

ricyaun
after looking for the # symbol.  Never mind I just found out how to upload a screenshot.

---

### Post by ricyaun on 2010-04-07
> **ricyaun said:**
> after looking for the # symbol.  Never mind I just found out how to upload a screenshot.

Test sample screenshot

---

### Post by ricyaun on 2010-04-07
Well that didn't work out well either

---

### Post by ricyaun on 2010-04-07
appears my hacker buddy didn't appreciate my posting that screenshot.  I got his proxy address though.  74.125.115.102:www - It is a google.  google doesn't have an abuse department I can find so they tend to use it alot when I am netstat active.  He had decided to use up my resources until I posted his IP proxy address here.  Yeah Yeah I know I am supposed to be paranoid -wear an aluminum foil hat to keep the mind police out.  But I am not.

---

### Post by Calash on 2010-04-08
You can install FireStarter from the Software Center.  Then you can block the port numbers and/or the IP address being used by the hacker.


How do you know your being hacked?  Are you behind a router?  If so, check the settings to see if port forwarding is enabled for the listed ports.

---

