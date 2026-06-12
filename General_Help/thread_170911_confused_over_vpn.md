---
title: "confused over vpn"
date: 2006-05-05
forum: General Help
---

### Post by frank05 on 2006-05-05
I used to use the cisco vpn client on windows to connect to my university's network but now I use linux most of the time because it has better tools for development (imho). However, I cannot get vpn to work on linux. 
When I used the cisco client on windows all I had to enter was the server, my group and my username and password. What confuses me now is that when I use vpnc (which i've read is most like cisco) I need to specify a group secret in addition to the aforemention fields. I've never been given a group secret so is it really necessary? If it isn't could somone tell me how to configure vpnc to ignore it?

Thanks,

---

### Post by neouser99 on 2006-05-05
if you got the cisco client from the university, it was mostly packaged already with the group secret/auth key. it is really easy to get that config file from the windows client and use it with the linux client, which is what i ended up doing for my stuff.

basically i think that group thing is just a secondary authenticator for the client, then you auth to get in. if that doesn't work, you can contact your network admin and i am sure that he will help you get things straight.

-neo

---

