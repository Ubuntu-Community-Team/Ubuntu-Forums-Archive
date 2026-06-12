---
title: "Why is the internet slow on ubuntu??"
date: 2006-02-21
forum: General Help
---

### Post by REXXER on 2006-02-21
I have fiber optics and the internet in ubuntu is still slow as hell. wat is that about?? TY

---

### Post by kaamos on 2006-02-21
Can you be more specific what is slow? So are you getting slow transfer rates when downloading, or is firefox taking a long time to look up web addresses?

Is there a difference in time to open these two links?

[http://www.google.com/](http://www.google.com/)
[http://66.102.9.147/](http://66.102.9.147/)

---

### Post by REXXER on 2006-02-21
it takes a long long long time to load sites!!!!!

---

### Post by kaamos on 2006-02-21
Sound like a dns problem.. Got an answer for the latter question? That would help.

---

### Post by REXXER on 2006-02-21
im not using my ubuntu laptop right now, cause its way tooooo slow! the 66.102.9.147 takes longer to load

---

### Post by REXXER on 2006-02-21
my desktop (which runs windows xp home) says that their is a problem with an ip adress on another computer, meaning my ubuntu laptop! wat do i do??

---

### Post by kaamos on 2006-02-21
Look up your dns servers and write them down. If you are on the same connection that ubuntu will be, type "ipconfig /all" in windows command prompt, that should show your dns-servers. Check that the ones listed in ubuntus network-config (System->Administration->Network settings->dns) match those.

Another thing you could try: 
Open firefox, type about:config in the address bar. Type ipv6 in the filter. Change network.dns.disableIPv6 to true

EDIT: ah, you posted again. Try setting a static ip in ubuntus network settings.

---

### Post by REXXER on 2006-02-21
it is still really slow!

---

### Post by REXXER on 2006-02-21
what should i make the ip address, the subnet mask, and gateway address??

---

### Post by bfbay315 on 2006-02-21
I had a simlilar problem except that I wasnt using a fiber card, I am using a standard ethernet, 100mbps.  

I may be wrong on this, so somebody correct me if I'm wrong.  My understanding is that firefox is configured, by default, to use the IPv6 internet addressing protocol.  However if your card does not handle IPv6, you may need to disable that and reconfigure for IPv4.   

a quick fix I made was to disable IPv6 in firefox 
1) open firefox
2) type "about:config" in the url
3) scroll down to "network.dns.disableIPv6" 
4) double click on "network.dns.disableIPv6" changing the value to true
5) restart the browser

this worked for me.. Hope this helps.

this link has some useful/useless info..
[http://ubuntuforums.org/archive/index.php/t-87798.html]("http://ubuntuforums.org/archive/index.php/t-87798.html")

Brian

---

### Post by kaamos on 2006-02-21
How is it connected? Through the xp machine or to a router or a direct connection to the net?

---

### Post by bfbay315 on 2006-02-21
kaamos beat me to it..

---

### Post by REXXER on 2006-02-21
i think it is through the xp machine but im not positive

---

### Post by n00bWillingToLearn on 2006-04-06
[QUOTE=kaamos]Can you be more specific what is slow? So are you getting slow transfer rates when downloading, or is firefox taking a long time to look up web addresses?

Is there a difference in time to open these two links?

[http://www.google.com/](http://www.google.com/)
[http://66.102.9.147/](http://66.102.9.147/)[/QUOTE]
I am not at my ubuntu machine right now but I believe that for me the former link would load faster than the latter (the problem being DNS). I am noticeing that firefox is taking an inordinate amount of time(up to 10 seconds) "looking up" an adress and once I have connected to a site I can sometimes browse at normal speeds within that site and it seems that when I cannot that those pages have content from other domains. I immediately suspected a dns problem so I tried pinging and to my surprise it was immediate. Could this be the IPv6 problem bfbay315 is talking about?

---

