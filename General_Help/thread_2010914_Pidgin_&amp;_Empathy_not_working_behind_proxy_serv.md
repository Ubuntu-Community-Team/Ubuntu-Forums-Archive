---
title: "Pidgin &amp; Empathy not working behind proxy server"
date: 2012-06-26
forum: General Help
---

### Post by xlearner on 2012-06-26
This is on getting Pidgin/Empathy work on Ubuntu 12.04. Probably, this issue was discussed earlier. But so far, I did not find any satisfactory solution. 

I recently installed Ubuntu 12.04. I have Pidgin 2.10.3 and Empathy 3.4.2 on my machine with authentication. At work, we have a http proxy server. I was trying to connect to my gtalk account. 

But unfortunately neither Pidgin nor Empathy works. On Pidgin, at the proxy tab, I supplied the proxy server and port information. For some reason it could never connect to the gtalk server. 

When I try gtalk on Windows 7 at our work place, it seems to work perfectly fine. So any help or suggestion would be greatly benefitted. 

If not Pidgin/Empathy, does anyone know of any other chat client that works behind a proxy server in ubuntu? Thanks!

---

### Post by xlearner on 2012-06-26
I see that there are around 83 views for this post. But no reply yet :-(! Any thoughts or suggestions? 

Wondering if I posted in the wrong section? Probably I should post this is on Pidgin and Empathy's forums as well!

---

### Post by Breno Cesar on 2012-07-23
> **xlearner said:**
> I see that there are around 83 views for this post. But no reply yet :-(! Any thoughts or suggestions? 

Wondering if I posted in the wrong section? Probably I should post this is on Pidgin and Empathy's forums as well!

Man....

I have this same problem , i've found some tricks reated about this in a famous brazilian "how-to" site named "viva o linux".

There is the link and the soluction.

[http://www.vivaolinux.com.br/topico/UbuntuBR/Empathy-nao-conecta/]("http://www.vivaolinux.com.br/topico/UbuntuBR/Empathy-nao-conecta/")

This trick didn't work to me , becaus for some reason te path and the file "/usr/share/pyshared/papyon/service/description/SingleSignOn/RequestMultipleSecurityTokens.py" dont exist.

---

### Post by xlearner on 2012-07-25
Dear Breno Cesar,

Thanks a lot for the reply. But sadly I don't know Portugese. Further, the file, "/usr/share/pyshared/papyon/service/description/SingleSignOn/RequestMultipleSecurityTokens.py" does not exist on machine as well.

So I am lost :-(!

Xlearner

---

### Post by xlearner on 2012-07-29
Breno Cesar,

I figured out how to connect to gtalk through pidgin behind a proxy server on ubuntu 12.04. **Steven** of pidgin forums told me this solution:

Open the Gmail account options, 
- In the proxy tab, enter the proxy information and the necessary details
- In the advanced tab, and set "Connection Security" to "Use old-style SSL" and then change the "Connect Port" to "443". Then connect server to: talk.google.com

This perfectly worked for me on gtalk :-)! 

Next, I am trying to figure out how to make pidgin work for yahoo messenger. Any clues on this? I realized that we must have a different settings for each service provider. 

Xlearner

---

### Post by arief1812 on 2012-10-11
> **xlearner said:**
> Breno Cesar,

I figured out how to connect to gtalk through pidgin behind a proxy server on ubuntu 12.04. **Steven** of pidgin forums told me this solution:

Open the Gmail account options, 
- In the proxy tab, enter the proxy information and the necessary details
- In the advanced tab, and set "Connection Security" to "Use old-style SSL" and then change the "Connect Port" to "443". Then connect server to: talk.google.com

This perfectly worked for me on gtalk :-)! 

Next, I am trying to figure out how to make pidgin work for yahoo messenger. Any clues on this? I realized that we must have a different settings for each service provider. 

Xlearner

yes it's worked on emphaty too, thank you very much ;)

---

