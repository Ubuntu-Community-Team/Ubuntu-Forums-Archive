---
title: "Communication between client and server when DHCP is enabled"
date: 2010-09-28
forum: General Help
---

### Post by Like2Learn on 2010-09-28
I have an embedded device which acts as a client, and a server at office. The IP address of the client is allocated by DHCP, so its IP address is actually variable. I would like to know what is the simpliest way to maintain the communication between client and server when DHCP is enabled.
I once used socket many years ago to communicate between the client and the server. If I remember it right, I actually bypassed the dynamic IP issues by using the computer name to replace the IP address. Even the client is not at the same local network as the server, the scheme still worked. Correct me if my memory cheated me. Please let me know if socket is still the best solution for this kind of application involving DHCP?
I also heard from someone that it is necessary to implement [FONT=Times New Roman]multicast discovery protocols named BONJOUR, but I don't think it is necessary, and I don't think it is a simple solution. What do you think?[/FONT]
[FONT=Times New Roman]Thanks.[/FONT]

---

### Post by The Cog on 2010-09-28
I would have thought that the client connects to the server, and therefor the client needs to know the server's address but the server just waits for the call and doesn't need to know the client's address. So all you have to do is tell the client (somewhere in its configuration) that the address of the server is <whatever>. If the server is also DHCP then things get more difficult, and you probably need a name server with a fixed IP address that you can tell the client about.

---

### Post by Like2Learn on 2010-09-28
> **The Cog said:**
> I would have thought that the client connects to the server, and therefor the client needs to know the server's address but the server just waits for the call and doesn't need to know the client's address. So all you have to do is tell the client (somewhere in its configuration) that the address of the server is <whatever>. If the server is also DHCP then things get more difficult, and you probably need a name server with a fixed IP address that you can tell the client about.
 
Yes, if both the server and the client are DHCP, then I think a name server will be a MUST. However, I think most of the enterprise already have a name server in place, so there will be no additional work.
Thank you!

---

