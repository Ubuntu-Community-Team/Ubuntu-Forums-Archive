---
title: "Can you run ubuntu on desk top and windows on wireless laptop using same modem"
date: 2009-11-25
forum: General Help
---

### Post by specs2020 on 2009-11-25
I would like to know if I can run ubuntu 9.10 on my desk top and run windows XP on my wireless laptop using the same modem. The modem is a gateway and i have DSL from AT&T. Iam worried that if the modem is set for Ubuntu my laptop wii not work.Thanks in advance for any help or advice you can give me.

---

### Post by marshmallow1304 on 2009-11-25
That should work nicely.  I'm not familiar with AT&T's internet, but I assume that the modem is also a router (can you hook up more than one machine at a time?).  If that is the case, you will not have any issues.

---

### Post by benj1 on 2009-11-25
> **marshmallow1304 said:**
> That should work nicely.  I'm not familiar with AT&T's internet, but I assume that the modem is also a router (can you hook up more than one machine at a time?).  If that is the case, you will not have any issues.
+1

stand alone routers arent expensive anyway

---

### Post by specs2020 on 2009-11-25
The desk top is pluged in to it but I do not think there is any place to plug any more in.

---

### Post by specs2020 on 2009-11-25
So the only way it will work if I get a stand alone router. Thanks for all the help.

---

### Post by emachnic on 2009-11-25
Just spring for a wireless router so you don't need to plug your laptop in to get internet

---

### Post by specs2020 on 2009-11-25
My Laptop is wireless and not pluged in but the desk top is pluged in to the wireless modem.

---

### Post by emachnic on 2009-11-25
Your laptop has to be connected to a wireless network or connected by ethernet cable. You'll need a router if you want to use both at the same time so get a wireless router and you'll be able to connect wirelessly

---

### Post by specs2020 on 2009-11-25
My DSL is wireless along with my laptop but the desk top is not wireless it is pluged in directly to the modem. So it looks like i need to buy a wirless router if I am correct. Thank you

---

### Post by EndPerform on 2009-11-25
> **specs2020 said:**
> My DSL is wireless along with my laptop but the desk top is not wireless it is pluged in directly to the modem. So it looks like i need to buy a wirless router if I am correct. Thank you

Yes, you'll need a wireless router.  From the sounds of it, AT&T provided the modem to you, and that's all you have.  I have AT&T as well, and I've got my modem running through a Linksys router which serves 3 laptops and 3 desktops.

---

### Post by lisati on 2009-11-25
> **specs2020 said:**
> My DSL is wireless along with my laptop but the desk top is not wireless it is pluged in directly to the modem. So it looks like i need to buy a wirless router if I am correct. Thank you

From what I've read in this thread, what you want to do is feasible. Although I didn't purchase a separate router immediately, what I did when I got DSL is pretty much the same has been suggested (buy a stand alone router with wireless capabilities). One bonus of getting a router: it opens up the possibility of sharing other resources between your computers at home if you so choose, not just the internet connection.

And don't be scared to ask questions. Quite a few of us here at the forums have some experience setting up home networks.

---

### Post by 73ckn797 on 2009-11-25
> **specs2020 said:**
> My DSL is wireless along with my laptop but the desk top is not wireless it is pluged in directly to the modem. So it looks like i need to buy a wirless router if I am correct. Thank you


You are saying that the DSL modem is dual purpose wired/wireless? It has a connection for a wire to the desktop but also is a wireless modem? If that is what you mean then you will have no problem.

I use cable internet and it has a wired modem. In order to use other computers in the house I have connected the modem to a router that is wired and wireless. My desktop connects by wire and laptop and 3 other computers using wireless.

The one AT&T system I am familiar with is only a modem and has to also use a router as I describe.

---

### Post by wilee-nilee on 2009-11-25
> **73ckn797 said:**
> You are saying that the DSL modem is dual purpose wired/wireless? It has a connection for a wire to the desktop but also is a wireless modem? If that is what you mean then you will have no problem.

I use cable internet and it has a wired modem. In order to use other computers in the house I have connected the modem to a router that is wired and wireless. My desktop connects by wire and laptop and 3 other computers using wireless.

The one AT&T system I am familiar with is only a modem and has to also use a router as I describe.

+1 Call your provider or look at the network manager and see if your getting a wireless signal, you may have wireless already.

---

### Post by running_rabbit07 on 2009-11-25
To check and see if your modem is capable of connecting to multiple machines you can use 2 methods.

1. Fire up both systems and see if they both connect to the net.

2. Run the command ```
netstat -r
``` in a terminal and make note of the default gateway number that is shown there. I have attached an example of this. Next, run the command ```
ifconfig
``` in a terminal and make note of your IP address. Next open firefox and inter the default gateway address, that should connect you to the modem to be able to find out what capabilities it has. If it asks for a password and you don't know it and don't have the manual to the modem, then you can google "brand model# password" Example, "cisco wrt110 password" and you should be able to find the factory password, if not post here and maybe someone here will know it.

---

