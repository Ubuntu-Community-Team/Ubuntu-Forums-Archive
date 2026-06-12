---
title: "Server Kernel vs Real-time (Studio kernel)"
date: 2009-06-30
forum: General Help
---

### Post by Jestersage on 2009-06-30
One of the reason I decided to go fro Ubuntu instead of openSuSE (for now) is that Ubuntu Server have a kernel that is compile FOR servers. However, what does that mean, and how does that compare to real-time kernel (ala Ubuntu Studio)?

---

### Post by t4thfavor on 2009-06-30
I thought realtime kernels didn't do well with background processes because they give realtime priority to the currently in use thread(s). Im not an expert, but I do know that routters, and time sensative stuff run realtime kernels. That is all I know.

---

### Post by Jestersage on 2009-07-01
I see... but if routers are basically a type of servers (in a way), then...

---

### Post by t4thfavor on 2009-07-01
Im stumped.

Read this, 
[http://en.wikipedia.org/wiki/Real-time_operating_system](http://en.wikipedia.org/wiki/Real-time_operating_system)

---

### Post by Jestersage on 2009-07-04
Okay, i figure it out. So server basically would have low overhead, high latency, while RT kernel will have high overhead, low latency.

---

