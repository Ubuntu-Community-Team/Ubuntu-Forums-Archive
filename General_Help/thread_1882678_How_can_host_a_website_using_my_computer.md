---
title: "How can host a website using my computer ?"
date: 2011-11-17
forum: General Help
---

### Post by West201 on 2011-11-17
I've heard I can host my two blogs using my own computers. They don't get much traffic. Any simple way of doing this ? 
Is a 20MB internet connection good enough ? Thanks

---

### Post by desktorp on 2011-11-17
How easy it is kinda depends on what you want.  Domain names are the big  hangup for some people.  A domain name needs to have an IP address  attached to it, so it knows where your computer is, right?  Typical residential connections come with a **dynamic** IP  address, rather than a **static** IP address.  Dynamic IP addresses change  unexpectedly, so you need to use **DNS** to keep it synchronized, or pay for  a static IP address.  Some ISPs used to just let you add a static IP without much more cost, but now it's almost always tied in to some overpriced business account.  The average, small-potatoes home-host like you and I, basically just need to get comfortable using DNS.  Many modems/routers support automatic DNS synchronization.  Domain name providers like GoDaddy also provide some sort of DNS services, but I've never personally used them.

Aside from the domain name / IP address junk, you should also work up a basic understanding of Apache or some other web server software.  You might need things like PHP and a database like MySQL or something, depending on your choices with content management / blog / forum software, but that stuff is pretty straightforward, compared to the above mentioned stuff.

There is probably some one-click hosting solution that someone will swoop in and rub in my face, but that's the gist of the entry level confusion most people have to face when they decide to host from home.  You clearly are familiar with some level of that already, so maybe you can be more specific about what part seems daunting or the most confusing.

Sorry if my reply just added more confusion. ):P

---

### Post by West201 on 2011-11-17
> **desktorp said:**
> How easy it is kinda depends on what you want.  Domain names are the big  hangup for some people.  A domain name needs to have an IP address  attached to it, so it knows where your computer is, right?  Typical residential connections come with a **dynamic** IP  address, rather than a **static** IP address.  Dynamic IP addresses change  unexpectedly, so you need to use **DNS** to keep it synchronized, or pay for  a static IP address.  Some ISPs used to just let you add a static IP without much more cost, but now it's almost always tied in to some overpriced business account.  The average, small-potatoes home-host like you and I, basically just need to get comfortable using DNS.  Many modems/routers support automatic DNS synchronization.  Domain name providers like GoDaddy also provide some sort of DNS services, but I've never personally used them.

Aside from the domain name / IP address junk, you should also work up a basic understanding of Apache or some other web server software.  You might need things like PHP and a database like MySQL or something, depending on your choices with content management / blog / forum software, but that stuff is pretty straightforward, compared to the above mentioned stuff.

There is probably some one-click hosting solution that someone will swoop in and rub in my face, but that's the gist of the entry level confusion most people have to face when they decide to host from home.  You clearly are familiar with some level of that already, so maybe you can be more specific about what part seems daunting or the most confusing.

Sorry if my reply just added more confusion. ):P

I called my ISP and I was told that my IP is static. So I would need to set up LAMP and they redirect the domains to my I.P address ?

---

### Post by restorator on 2011-11-17
It is pretty easy to set up a basic home webserver. However, properly securing it is something much more difficult and time consuming. If you have no experience, I would advise you set up one that is only available inside your home network at first and learn how to use it and properly secure it before you open it up to the world.

---

### Post by West201 on 2011-11-17
> **restorator said:**
> It is pretty easy to set up a basic home webserver. However, properly securing it is something much more difficult and time consuming. If you have no experience, I would advise you set up one that is only available inside your home network at first and learn how to use it and properly secure it before you open it up to the world.

For what your saying it's going to be easy. Is there a tutorial you can refer me to ? :)

---

### Post by lisati on 2011-11-17
> **jessejj89 said:**
> I called my ISP and I was told that my IP is static. So I would need to set up LAMP and they redirect the domains to my I.P address ?

Going through your ISP to redirect your domain name to your IP address is one option, but might cost extra money. There are also free options, such as using services like [no-ip.com]("http://no-ip.com")

---

### Post by gordintoronto on 2011-11-17
Assuming you want a web site name such as [www.gordsblog.com](www.gordsblog.com), you will need to sign up with a domain name registrar such as godaddy.com or isqsolutions. It's not very expensive, but you need to renew it every year, or you will lose it.

You could wait until you've got everything running nicely, and run the risk that someone registers gordsblog.com ahead of you, or you could register it immediately and put up an "under construction" web page.

Many ISPs include a free web page for all clients, but they have a name such as [www.myisp.com/~gordintoronto](www.myisp.com/~gordintoronto)  A good friend has a huge web site with that kind of address. (He can't back it up on a single DVD...)

---

