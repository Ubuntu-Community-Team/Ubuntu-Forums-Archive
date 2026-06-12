---
title: "Configure a router from the command line"
date: 2011-03-29
forum: General Help
---

### Post by Karmic Kiwi on 2011-03-29
I'm sitting here at school, and I need to forward a port from my router at home to my Ubuntu box also at home. I stupidly forgot to turn on external administration on the router, but I can still SSH into the server. Is there a way I can access the router through the server via the command line?

---

### Post by rbishop on 2011-03-29
What kind of router do you have?

---

### Post by Karmic Kiwi on 2011-03-29
> **rbishop said:**
> What kind of router do you have?

Oh, sorry. It's a WRT54GL running the latest Tomato.

---

### Post by rbishop on 2011-03-29
You should be able to telnet from your local server to your router using the local IP address of the router.

I have not used Tomato, so you may ssh to it rather than telnet.

I am using DD-WRT and am able to telnet from my local machine to the router for updates/changes.

---

### Post by Karmic Kiwi on 2011-03-29
> **rbishop said:**
> You should be able to telnet from your local server to your router using the local IP address of the router.

I have not used Tomato, so you may ssh to it rather than telnet.

I am using DD-WRT and am able to telnet from my local machine to the router for updates/changes.

SSH wasn't set up, but telnet worked perfectly. Thanks!

---

