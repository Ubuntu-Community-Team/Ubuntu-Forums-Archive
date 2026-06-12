---
title: "Really confused!"
date: 2010-06-11
forum: General Help
---

### Post by Enthrall on 2010-06-11
What I always thought was right, was wrong? :confused: 

Well heres the story I've set up a xubuntu lamp server.. so far.

I can access apache from within my lan. Called up a friend and asked him to attempt to connect to the webserver using my external ip and it didnt work. Thought either my isp is blocking port 80 or i need to forward it. So I forwarded the port of the computer with apache (not the router ip*192.168.0.1*) the server is 192.168.0.7. I got to check to see if its still blocked and it times out. Go back and forward the router which I never do, usually the computer ip on the lan,router- *192.168.0.1* to 80. Check port and by jeebus its open. Friend goes to my external ip and he says theres a login.

Now Im thinking wtf have I been port forwarding wrong all this time? :-sFirewall is turned off so its using NAT. Im so confused guys. 

Also a really important question what is the apache login/password is it the one I set for phpmyadmin? Cause when I set up lamp i dont remember setting one for apache, also it says "the site says webadmin" how do I change that.

When I check game ports that Iv forwarded before using the computers ip it says there closed however they've worked before.

View attachment below.

Another thing when I go to my external ip it takes me to my router config is this normal?

Thx for all the help! ):P

well to update I got rid of the router portforward and changed to the pc, now its forwarded. And works. I dont know why it didnt work before. Is there any reason you would forward the actual gateway ip?

---

### Post by dcstar on 2010-06-12
> **Enthrall said:**
> 
........
well to update I got rid of the router portforward and changed to the pc, now its forwarded. And works. I dont know why it didnt work before. Is there any reason you would forward the actual gateway ip?

[LIST=1]
[*]Because that is the way these things work.
[*]Mark the thread as solved.
[/LIST]

---

### Post by Hallowed on 2011-05-08
Hey so I am really confused too!
I just tried that IP address you listed above (192.168.0.1) and it says:
A username and password are being requested by [http://192.168.0.1](http://192.168.0.1). The site says: "WebAdmin"

That is the exact same thing mine says. I'm trying to set up a server using wamp. But I have no idea what it's username and password its asking for? Is this something to do with my ISP? (quest). I know its not my router because I tried connecting without my router being plugged in at all. Unless my modem does something ? I dunno help?

---

### Post by idoitprone on 2011-05-08
> **Hallowed said:**
> Hey so I am really confused too!
I just tried that IP address you listed above (192.168.0.1) and it says:
A username and password are being requested by [http://192.168.0.1](http://192.168.0.1). The site says: "WebAdmin"

That is the exact same thing mine says. I'm trying to set up a server using wamp. But I have no idea what it's username and password its asking for? Is this something to do with my ISP? (quest). I know its not my router because I tried connecting without my router being plugged in at all. Unless my modem does something ? I dunno help?

there should be a default user name and pass if you havent set it kidda like my d-link router

username: admin
pass: <there is no pass>

---

### Post by alphacrucis2 on 2011-05-08
Reply to the OP rather than the hijack.

Some address blocks are reserved for local private use only. ie they do not get routed via the public internet. 192.168.x.x is one of these blocks. Millions of routers would be using 192.168.0.1 as an internal address so how could the internet possibly know which one was meant. That is why a public address must be used (because public addresses are unique). Port forwarding is just a method of translating the external (public address) to an internal private address. The same thing happens in reverse when an application (a browser for example) connects out to the internet. Your router changes the source address to be its public address. The router keeps a table of these translations so that it knows how to send the responses back to the correct internal address and source port.

[http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network)

---

