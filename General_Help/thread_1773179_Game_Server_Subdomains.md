---
title: "Game Server Subdomains"
date: 2011-06-01
forum: General Help
---

### Post by sirhalos on 2011-06-01
I have a game server running two different versions of the game, however the game itself listens to one port.

Example: Game server 1 listens to Port 3724, Game server 2 listens to Port 3725.

I am trying to create a subdomain to listen to these ports, however I am unable to add a A class DNS entry since it doesn't look at port number.

I have added the subdomain names as CNAME on DNS and also added them to /etc/hosts.

What else would I need to do to have my ubuntu server to be able to receive the following. 

gameone.domain.com
gametwo.domain.com 

Where both are listening to different ports? Again both game servers are setup to listen to the ports I wish however the game is unable to do so.

Thanks.

---

