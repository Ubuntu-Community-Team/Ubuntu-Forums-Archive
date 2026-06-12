---
title: "Static IP- Lucid Lynx"
date: 2010-07-07
forum: General Help
---

### Post by reica on 2010-07-07
I have trouble getting a **gateway** to the internet when setting eth0 with a fixed IP address.
The gateway address (192.168.2.1 my modem/router)** resets to 0.0.0.0** whenever I apply the changes. 
DHCP works fine but I need a fixed address for my server.
Can anyone help?
Rein

---

### Post by energybeing on 2010-07-07
What IP are you trying to set your machine to have?  The IP that you set your machine to have must be in the same subnet as your gateway, 192.168.2.x.  If you try to set your machine to have an IP of anything else, IE 192.168.1.x or 10.0.0.x or whatever, you will have problems.

---

### Post by Leppie on 2010-07-07
could you post your /etc/network/interfaces?

---

### Post by alphacrucis2 on 2010-07-07
> **reica said:**
> I have trouble getting a **gateway** to the internet when setting eth0 with a fixed IP address.
The gateway address (192.168.2.1 my modem/router)** resets to 0.0.0.0** whenever I apply the changes. 
DHCP works fine but I need a fixed address for my server.
Can anyone help?
Rein


If you are setting the fixed address via network manager, make sure you hit the [COLOR="Red"]enter[/COLOR] key after typing the IP address, subnet mask and default gateway, otherwise it doesn't save the setting. You will also need to specify at least one DNS server. On my setup I just set the DNS server the same as the dgway as my router acts as a DNS forwarder. YMMV.

---

### Post by reica on 2010-07-07
> **alphacrucis2 said:**
> If you are setting the fixed address via network manager, make sure you hit the [COLOR="Red"]enter[/COLOR] key after typing the IP address, subnet mask and default gateway, otherwise it doesn't save the setting. You will also need to specify at least one DNS server. On my setup I just set the DNS server the same as the dgway as my router acts as a DNS forwarder. YMMV.

Yeah...thankyou. Hit the nail on the head. Works fine now :D

---

### Post by Iowan on 2010-07-07
Remember to mark it [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). ;)

---

### Post by alphacrucis2 on 2010-07-07
> **reica said:**
> Yeah...thankyou. Hit the nail on the head. Works fine now :D

That one caught me out the first time I set up a static address via NM. I thought I was going nuts. It is probably a paper cut type bug in NM as you don't normally need to hit enter to make a field on a GUI interface stick. Especially when there is an "apply" button which should save whatever you had typed in the fields.

---

