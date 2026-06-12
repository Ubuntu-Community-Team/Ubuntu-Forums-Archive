---
title: "More internet trouble"
date: 2006-02-26
forum: General Help
---

### Post by Madman68 on 2006-02-26
Yesterday while I was using Ubuntu the power shut off for some reason. When I tried to use Ubuntu it had several problems, one of them being that it won't connect to the internet anymore. I checked the eathernet cord and all connects and they were ok. Ubuntu reconizes the internet and shows me the connection in network preferences but won't connect when I try to use the internet. Thanks again!

---

### Post by Ramses de Norre on 2006-02-26
Is it configured correctly? Check /etc/network/interfaces 
What does it exactly says when you try to connect to the internet?

---

### Post by Madman68 on 2006-02-26
An alert message comes up saying: > -website name- cannot be found. Please check the name and try again. It says this every time I try to visit a website. Any help would be welcome. Thanks!

---

### Post by Ramses de Norre on 2006-02-28
This looks like a DNS problem.
Can you ping ip adresses?
try ```
ping 82.211.81.166
```
Does it gives replies or time outs? 
(press ctrl+c after a couple of lines to stop the pinging).

---

