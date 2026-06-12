---
title: "How to forward all HTTP request to port no 3128?"
date: 2009-08-14
forum: General Help
---

### Post by karthick87 on 2009-08-14
I am using squid in a single PC,and i have configured my browser to ip address 127.0.0.1 and port no 3128..It works fine.I want to forward all HTTP request to port no 3128..But when i google,i get the result such that,forwarding HTTP request to port no 3128 is not possible under localhost..Is it possible anyway??If so pls tell me the way..

                     Thanks in advance..!

---

### Post by tripolitan on 2009-08-14
Assuming that you're using Firefox 3.5 and you have Squid installed on the same client machine(for whatever reason): In your browser, remove localhost, 127.0.0.1 from the NO PROXY FOR: section

---

### Post by dcstar on 2009-08-14
> **getyourkarthick said:**
> I am using squid in a single PC,and i have configured my browser to ip address 127.0.0.1 and port no 3128..It works fine.I want to forward all HTTP request to port no 3128..But when i google,i get the result such that,forwarding HTTP request to port no 3128 is not possible under localhost..Is it possible anyway??If so pls tell me the way..

                     Thanks in advance..!

System-Preferences-Network Proxy

---

### Post by karthick87 on 2009-08-15
Already i have removed that local host from no proxy list..My problem is i am using broadband plan of HOME250,and only i can download upto 1GB for free of cost..So i have installed  squid and configured it to block certain types of file extensions and websites..But simply my friends used to goto to the internet settings and change it to no proxy and they keep on downloading.. Wat i want to do is I want to force my system to go only through proxy..

---

### Post by tripolitan on 2009-08-17
Your initial post was vague, you never mentioned your friends (you said single PC)or even your network topography, or even the fact that you have a network with others sharing internet connection from the beginning.

These pieces of information are crucial for others to give you advice, otherwise, its a complete waste of time. So, how about some complete information about your network?

---

