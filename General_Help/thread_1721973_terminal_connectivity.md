---
title: "terminal connectivity"
date: 2011-04-05
forum: General Help
---

### Post by agdangel on 2011-04-05
Hi guys
 
I have an Ubuntu machine that I'm using at work to try a couple of things with. Naturally we use a firewall here, as we're a corporation. When I try to download software packages from th terminal it seems to deny me access. It's not on our domain, but I've put the proxy in - web traffic goes fine from the browser.
 
does the terminal communicate on different ports? am I going to have to open ports, or is there another setting somewhere that I need to fill for the terminal to download packages?
 
any help is greatly appreciated.

---

### Post by spacesamurai on 2011-04-05
When updating, I think it should be using the standard http port# 80. Are you able to view web pages on the current machine? If yes, there should not be any issues with updating your box.

Can you please give more information as to how you are updating your terminal?

---

### Post by Frogs Hair on 2011-04-05
This may not apply , but some companies use programs to block certain types of internet access for security reasons.

---

### Post by agdangel on 2011-04-05
> **spacesamurai said:**
> When updating, I think it should be using the standard http port# 80. Are you able to view web pages on the current machine? If yes, there should not be any issues with updating your box.
 
Can you please give more information as to how you are updating your terminal?
 
 
Thanks for the response.
 
I don't think this machine has been updating, now that I think of it. I will run a manual check but it doesn't seem to have updated automatically the way my home machine does.  
 
firefox connects fine once I input our proxy server settings.

---

### Post by spacesamurai on 2011-04-05
OK, so lets try to set the network proxy for the server. You can do this as:

System --> Preferences --> Network Proxy.

Once you set the proxy here, give the update another try and tell us what you get.

---

### Post by agdangel on 2011-04-05
> **Frogs Hair said:**
> This may not apply , but some companies use programs to block certain types of internet access for security reasons.
 
 
I'll try the update after verifying the proxy. thanks.
 
 
this certainly could be the case, and I should probably know (I am an IT guy) but our network security is managed offshore and I'm not about to bother them with all this. 
 
however if I do know what particular kinds of channels the terminal uses I might be able to figure out what's going on here. any ideas on that? I'd imagine it uses whatever channels necessary (ftp, ssh, http, wherever necessary depending on where the terminal is reaching for its info) .... but then again I'm somewhat new to ubuntu and unix, so I figured it was worth asking a couple questions.
 
thanks for the replies!

---

