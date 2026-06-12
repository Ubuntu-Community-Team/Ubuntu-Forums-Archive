---
title: "SSH issue"
date: 2009-08-06
forum: General Help
---

### Post by Patricrawley on 2009-08-06
I can tunnel in and run everything just fine on the local network. However, I tried to tunnel in with the external IP address of the server and it was refused. I have the port opened up to the computer. What's the issue?

---

### Post by sefs on 2009-08-06
When you say you tried with your external ip, do you mean

1) you tried your external ip from OUTSIDE your LAN

or 

2) you tried your external ip from INSIDE your lan

it 2) then you are running into a nat traversal problem where nat will simply not let you go out and then come back in, unless you tweak your configuration to allow such.  Sadly though I don't know the tweak :)

---

### Post by Patricrawley on 2009-08-06
Ahh, I tried 2. I guess I could get a friend to help me out then. I'm going off to college in the fall and I want to have this server running at home so I can back up my data.

---

### Post by cgb on 2009-08-06
Not sure if there is a Router involved but make sure the Router is set to forward the port to the appropriate internal IP as well.

*correction: In your original post I think you meant you opened the Router port to the computer but make sure it is also forwarded to the internal port.

---

### Post by Patricrawley on 2009-08-07
I did mean the router. In iptables everything is listed as open on the computer. I think I may have mistyped when I forwarded the IP because I'm still blocked out at work. I'll check later.

---

### Post by martinbaselier on 2009-08-07
Try using a different port. Some routers don't do well with forwarding port 22, since they have ssh access themselves.

---

### Post by Patricrawley on 2009-08-07
Well my power flickered last night and my router reassigns local ips when it get's turned off giving priority to the ethernet and before my server was .8, now it's probably much lower.

---

### Post by martinbaselier on 2009-08-07
Most routers either allow clients to use a static ip or have an option in the dhcp server, to use a static address for a certain mac address.

---

### Post by Iowan on 2009-08-07
> **martinbaselier said:**
> Most routers either allow clients to use a static ip _or have an option in the dhcp server, to use a static address for a certain mac address._AKA static lease... probably a GOOD thing for a server.

---

### Post by Patricrawley on 2009-08-09
I know it's .3 now and it will stay that way because I've restarted the router a few times now and it always goes to .3. Now my issue is timing out when using the external ip address. I have tried the -C variable and it doesn't do much good.

---

