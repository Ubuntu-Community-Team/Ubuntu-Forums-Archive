---
title: "apt-get troubles behind a MS proxy server"
date: 2006-03-13
forum: General Help
---

### Post by General Moskovich on 2006-03-13
I'm having a horrible time trying to run apt-get behind a MS proxy server. If I change all the sources from http to ftp things are ok. So it seems my company's proxy only blocks http. 

I have found the program "ntlmaps", which gives me a NTLM Authorization Proxy Server. This is actually quite cool. I've set $http_proxy to localhost (/etc/bash.bashrc), and I can now use wget and stuff like that now. But for some reason apt-get doesn't work. 

Any ideas?

---

### Post by claes on 2006-03-13
A long time ago I was forced to work behind a ms proxy 2.0 and everything in linux was behaving very strange (Windows is always behaving strange). I found a norwegian company that hade made a windows proxy client for linux and light began to shine in my life. I got an acceptable working internet connection with that. But still alot of strange problem. Then I talked my boss into switching to a linux firewall and I never looked back. If you want to try the norwegian software look at:

apt-cache show dante-client

Claes

---

### Post by General Moskovich on 2006-03-13
Thanks for the reply. I was able to get ntlmaps to work afterall. My problem was two-fold. First, I needed to have the following line in my /etc/bash.bashrc file:

export http_proxy="http://localhost:5865"

Then my second problem was a configuration issue with the package. I incorrectly set the listening port. When set to 5865 everything works beautifully.

---

