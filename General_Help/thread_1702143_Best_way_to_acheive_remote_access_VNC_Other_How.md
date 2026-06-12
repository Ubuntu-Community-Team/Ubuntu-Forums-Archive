---
title: "Best way to acheive remote access? VNC? Other? How?"
date: 2011-03-07
forum: General Help
---

### Post by icebox83 on 2011-03-07
New member here just looking for a solution for remote access over LAN and the internet. I've known Linux for seven years but have only begun working with it extensively the past couple months. I had recently tried a couple free VNC solutions but ended up giving up when nothing worked. TeamViewer ended up not working properly either and instead crashed at the end of each session. Any chance there's a simple solution to this?

---

### Post by Habitual on 2011-03-07
This will depend on the definition of "remote access"
Since you mentioned TeamViewer, I will assume graphically.

Can you clarify what the purpose of the access is?
That will tell us what "access" means and we can better suggest something that will work.

Thank you.

---

### Post by uRock on 2011-03-07
I use ssh.

---

### Post by icebox83 on 2011-03-07
> **Habitual said:**
> This will depend on the definition of "remote access"
Since you mentioned TeamViewer, I will assume graphically.

Can you clarify what the purpose of the access is?
That will tell us what "access" means and we can better suggest something that will work.

Thank you.

Sure thing. I do indeed mean graphically. The application here is to be able to perform maintenance and check various things when a remote digital signage appliance stops functioning. We're coming from Windows where they would often go down; don't know about Linux yet since we're in the process of starting the testing phase and just put our first machine out in the field, sans remote access capability. On Windows we used LogMeIn, which worked GREAT. No such thing for Linux.

---

### Post by Habitual on 2011-03-07
NX is an exciting new technology for remote display. It provides near local speed application responsiveness over high latency, low bandwidth links. The core libraries for NX are provided by NoMachine under the GPL. FreeNX is a GPL implementation of the NX Server and NX Client Components. 

[FreeNX]("http://freenx.berlios.de/") if the target machines are *nix.
RDP is the targets are Windows boxes.

HTH.

---

### Post by matt_symes on 2011-03-07
Hi

Webmin is also an option.

Kind regards

---

