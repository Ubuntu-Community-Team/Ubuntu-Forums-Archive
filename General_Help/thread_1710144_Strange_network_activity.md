---
title: "Strange network activity"
date: 2011-03-19
forum: General Help
---

### Post by Spyderkid on 2011-03-19
My computer seems to be sending and receiving data (i know this sounds crazy) whenever I click or type anything.

it seems to send anything from 50kb to 1mb

everything seems to be ok with my firewall no strange protocals.

---

### Post by 5149.5 on 2011-03-19
Open terminal and enter netstat -natp. Do you see any strange connections? You could paste the results in a post if you would like us to have a look.

---

### Post by Spyderkid on 2011-03-19
this is what i got nothing strange i don't think appart from maybe bottem line

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1263/cupsd      
tcp        0      0 192.168.0.8:53607       74.125.230.113:443      ESTABLISHED 32368/chrome    
tcp        0      0 192.168.0.8:55688       74.125.77.102:80        ESTABLISHED 32368/chrome    
tcp        0      0 192.168.0.8:39204       209.85.147.138:80       ESTABLISHED 32368/chrome    
tcp6       0      0 ::1:631                 :::*                    LISTEN      1263/cupsd

---

### Post by 5149.5 on 2011-03-19
I don't see anything strange there. Just a couple browser to unsecured web pages and one secured. ??????

---

### Post by Spyderkid on 2011-03-19
just realised what the bottem line is i think its my printer which uses CUPS

---

### Post by 5149.5 on 2011-03-19
> **Spyderkid said:**
> just realised what the bottem line is i think its my printer which uses CUPS

Yeah, same as top line. I thought it was kind of odd that it listens on the loop back port but I know nothing about printers.

---

