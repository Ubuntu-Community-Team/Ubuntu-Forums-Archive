---
title: "Router problems"
date: 2011-02-16
forum: General Help
---

### Post by todaymueller on 2011-02-16
I appreciate that this is going to sound a bit basic and I am a little ashamed I cannot work out how to do this. But how do I connect a PS3 and PC running lucid linx to a router? 
I can get them both to connect to the internet, but only individually. If I switch on the PS3 it will go online but then the pc will not [ go online ] and visa versa. 
I know I sound a right thicky for not knowing how to do this, but can anybody help ?

---

### Post by coffeecat on 2011-02-16
Sounds like something is wrong with your router. Are you sure you mean a router?

If you connect your PS3 to a standard domestic modem-router either wirelessly or with an ethernet cable, and if you do the same with your PC, the router will control the traffic and both devices will be able to connect to the internet. That's how it is with my setup. I have a PS3 and a handful of computers. All can connect to the internet simultaneously via the modem-router.

So - what make and model of router do you have? Is it a modem-router? Do you have adsl over the phone landline, or do you get broadband via cable?

---

### Post by todaymueller on 2011-02-16
Sorry I should have given more information. I am using a nikkai [ maplins ] 5 port ethernet switch wired to a cable modem [ virgin ] with 2 ethernet cables going to a PC and a PS3 . If I unplug the ethernet switch and modem [ then switch em' back on ] then switch on a device it will connect but shuts out the other.

---

### Post by coffeecat on 2011-02-16
Here's your problem:

> **todaymueller said:**
> 5 port ethernet switch wired to a cable modem

An ethernet switch isn't a router, although a router incorporates  a switch. Put simply, you need a router to assign internal network addresses to each device - your PS3 and your computer - usually by acting as a DHCP server. A switch relies on each device already having a network address assigned. A router is a more complex device than a switch.

I've looked on the Maplins site, and this may be what you need, but talk to the assistants to be sure. I've always found them helpful and knowledgeable. That is if you want to go back to Maplins.

[http://www.maplin.co.uk/wired-broadband-xdsl-cable-router-34845](http://www.maplin.co.uk/wired-broadband-xdsl-cable-router-34845)

**EDIT**: also, if you look at the downloadable PDFs on that site, you'll see that in addition to being a DHCP server, that router does NAT (network address translation) and has a built-in firewall, among other things. All standard fare for a router, but not part of the design of a switch.

---

### Post by todaymueller on 2011-02-17
Thank you for the response and spending the time to reply to my question. I shall hot foot it back to maplins and see if I can upgrade to a proper router and give it another go.  :)

---

### Post by coffeecat on 2011-02-17
One last thought. I've read that some cable connections need to "register" the MAC code of the network interface of each device that you connect to the modem. When you connect with your PS3, the Virgin network will see the MAC code of the PS3 through the switch, and ditto with the computer. But when you connect a router to the modem, the Virgin network will see the MAC code of the outward facing interface of the router - the MAC codes of the computer and PS3 will not be visible to it.

I don't know whether this will be a problem because I use landline ADSL. I just remember seeing threads about this issue a couple of years or so ago. The Maplins people might know more, or you could talk to technical support at Virgin - that's if the technical support people are real support people and not assistants reading from cheat sheets. :(

Good luck anyway. :)

---

### Post by todaymueller on 2011-02-18
Yay, I changed the router today and I can now connect both the PS3 and PC at the same time, success. :P

---

