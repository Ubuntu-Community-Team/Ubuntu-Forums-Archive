---
title: "Destination host not reachable"
date: 2011-09-29
forum: General Help
---

### Post by satish_j on 2011-09-29
Network suddenly stops working in Lucid.And,Pinging to 192.168.1.1 gives 'Destination Host unreachable'
If i restart the system,network works for some time,can access Internet,ping also working fine,but suddenly(say after 4-5 min),it sort of hangs.
I tried removing the N/w cable and inserting back properly,but that didn't helped.
Any ideas how to resolve this?

---

### Post by satish_j on 2011-10-24
This is driving me crazy..Iam browsing Internet perfectly,and then suddenly it stops & i get Destination Host Unreachable.
Can anyone pls shed some light on it??

---

### Post by satish_j on 2011-10-24
This is driving me crazy..Iam browsing Internet perfectly,and then suddenly it stops & i get Destination Host Unreachable.
Can anyone pls shed some light on it??

---

### Post by SwitchDK on 2011-10-24
Hi satish_j

To let us help you trouble shoot you really need to include more information such as:

[LIST]
[*]Network diagram
[*]Router/Gateway type/firewall/etc
[*]Wired/Wireless (I think you are using wired based on unplugging network)
[*]Has anything changed recently
[*]What happens if you leave ping running from when you start the machine
[*]Does this happen to other computers on the network
[/LIST]

---

### Post by satish_j on 2011-10-24
How do i get the Network Diagram?
Iam using Ubuntu on Desktop PC with no firewall..Connection is wired..
There is nothing changed.All i did is the update through Update manager,but does not select certain packagaes like flash,Evolution,etc..
This is standalone computer,no network..

> **SwitchDK said:**
> Hi satish_j

To let us help you trouble shoot you really need to include more information such as:

[LIST]
[*]Network diagram
[*]Router/Gateway type/firewall/etc
[*]Wired/Wireless (I think you are using wired based on unplugging network)
[*]Has anything changed recently
[*]What happens if you leave ping running from when you start the machine
[*]Does this happen to other computers on the network
[/LIST]

---

### Post by SwitchDK on 2011-10-24
Hi satish_j,

I wanted you to draw a network diagram but you have basically done that by describing your setup :)

I might have misunderstood you but you say > This is standalone computer,no network. Isn't the problem you are experiencing pinging 192.168.1.1? What is associated with IP address 192.168.1.1? Would you expect a ping reply? Is your computer connected to the internet?

---

### Post by satish_j on 2011-10-24
> **SwitchDK said:**
> Hi satish_j,

I wanted you to draw a network diagram but you have basically done that by describing your setup :)

I might have misunderstood you but you say  Isn't the problem you are experiencing pinging 192.168.1.1? What is associated with IP address 192.168.1.1? Would you expect a ping reply? Is your computer connected to the internet?

192.168.1.1 is the ADSL Router..When i boot up system,i log into Internet and am able to surf.At thsi time,if i ping 192.168.1.1,reply is coming proper..After some random amount of time,Internet stops working.gives 'Page cannot found' for all web pages.Now,if i try pinging,it gives me 'Destination Host unreachable'
nm icon still shows connected,however,if i reconnect network through nm icon,it gives error as 'Wired network is disconnected' and icon changes to icon+red cross.After,this,no matter how much time i try to reconnect network,it gives me diconnected error.Only way out of this is to reboot the system and start afresh..
Any ideas now?

---

### Post by SwitchDK on 2011-10-24
hi,

OK, that is useful information (you are actually do have a network consisting of your computer and a router albeit very small)

Once you computer lose network access check the following and post the information here:

- Does your computer still have an IP address (Right click on Network Manager and select "Connection Information") and what is it?
- Is there light in the network card in your computer (the network card probably has two LEDs, one for activity (orange) and one for connectivity (green))
- Is your router still on and working
- It would be great if you had a different computer you could connect to determine if the problem is your computer or the router

Start the trouble shooting at the physical layer i.e. cable, router hardware, computer hardware etc.

Let me know how you get on

---

### Post by satish_j on 2011-12-19
Iam still facing this prob,it is driving me insane,should the admins move this thread to Networking sub-forum?

---

### Post by MartijnNL on 2011-12-19
> **satish_j said:**
> Iam still facing this prob,it is driving me insane,should the admins move this thread to Networking sub-forum?

It probably would have helped if you had answered the last questions asked to you by SwitchDK on October the 24th instead of staying silent for 2 months and then continuing to say you still have the same problem. If you want help, be prepared to answer questions, try things out and so on until the problem is solved (in a relatively shot period of time), otherwise people trying to help you might give up.

---

### Post by satish_j on 2012-05-09
This is a bug in Ubuntu,have seen on Lauchpad too..
I am using 12.04 precise pangolin along with Lucid and the same problem exists in precise too..

---

