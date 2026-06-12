---
title: "cannot connect to router or VM server"
date: 2011-10-24
forum: General Help
---

### Post by nik1979 on 2011-10-24
Hi All,
I've recently installed and currently using 11.10. 
I am currently trying to set up a way to learn to use a Trixbox, via VM. After installing and following the instructions of [http://call-cheap.blogspot.com/](http://call-cheap.blogspot.com/), I'm now at the point trying to access the GUI via typing the trixbox ip. 

I get this message:

> Error 324 (net::ERR_EMPTY_RESPONSE): The server closed the connection without sending any data.

When I got my Host and Guest IP's and tried using Ping, it appears to work fine. No lost packets and performing under a ms. 

Now, I tried accessing my router via IP according to the users manual (P-660R) and again its seems not to work. I noticed it doesn't say the same error (so it could be not working in an unrelated matter).

When I tried places>connect to server> and tried accessing my VM Trixbox from there, using SSH it fails to connect. It claims user or password is incorrect.

Thanks for you time, 
nik

---

### Post by oldtimer7777 on 2011-10-24
Who set up your previous configuration for your router on last-known working system? Before you wiped your old system did you copy your configuration settings? 

> **nik1979 said:**
> Hi All,
I've recently installed and currently using 11.10. 
I am currently trying to set up a way to learn to use a Trixbox, via VM. After installing and following the instructions of [http://call-cheap.blogspot.com/](http://call-cheap.blogspot.com/), I'm now at the point trying to access the GUI via typing the trixbox ip. 

I get this message:



When I got my Host and Guest IP's and tried using Ping, it appears to work fine. No lost packets and performing under a ms. 

Now, I tried accessing my router via IP according to the users manual (P-660R) and again its seems not to work. I noticed it doesn't say the same error (so it could be not working in an unrelated matter).

When I tried places>connect to server> and tried accessing my VM Trixbox from there, using SSH it fails to connect. It claims user or password is incorrect.

Thanks for you time, 
nik

---

### Post by nik1979 on 2011-10-24
> **oldtimer7777 said:**
> Who set up your previous configuration for your router on last-known working system? 

the router came with the new land-line phone and is fresh out of the box when the telcom technician installed it. 

> Before you wiped your old system did you copy your configuration settings?
Nope. Other than noting it down on paper, I wouldn't know how to keep a detailed configuration setting (i'm sure there is a thread about it somewhere I just haven't found the time to look for it).

---

### Post by oldtimer7777 on 2011-10-24
I don't want to lead you the wrong direction. It sounds like you had a "paid" support tech install your previous system, correct? Have you contacted support to double check your settings to make sure you have them right?  It is important sometimes to get support directly from whomever last configured the system correctly.  It might even be faster and less frustrating that way too.  I've never configured a VM quite the way you have described. I wish I could be more of help. Perhaps someone else will come along and read your original message and know the answer and correct approach here.  But most paid tech support these days can walk you through itover the phone, I'm pretty positive.


> **nik1979 said:**
> the router came with the new land-line phone and is fresh out of the box when the telcom technician installed it. 


Nope. Other than noting it down on paper, I wouldn't know how to keep a detailed configuration setting (i'm sure there is a thread about it somewhere I just haven't found the time to look for it).

---

### Post by nik1979 on 2011-10-24
I installed my ubuntu 11.10. The technician came over to install the phone and dsl. He just set the wires, the router, the phone line and phone physicaly, no fiddling with the software settings. I then checked the bandwidth using my laptop (11.04 Gnome classic) and that is the limit of his access. 

You just gave me an idea there of testing if my laptop (I'm currently troubleshooting my desktop) can access the router IP. 

there is no techsupport for me to call except the telco and they won't touch my computer given their scope of work. 
 
> **oldtimer7777 said:**
> I don't want to lead you the wrong direction. It sounds like you had a "paid" support tech install your previous system, correct? Have you contacted support to double check your settings to make sure you have them right?  It is important sometimes to get support directly from whomever last configured the system correctly.  It might even better faster that way.

---

### Post by oldtimer7777 on 2011-10-24
> **nik1979 said:**
> I installed my ubuntu 11.10. The technician came over to install the phone and dsl. He just set the wires, the router, the phone line and phone physicaly, no fiddling with the software settings. I then checked the bandwidth using my laptop (11.04 Gnome classic) and that is the limit of his access. 

You just gave me an idea there of testing if my laptop (I'm currently troubleshooting my desktop) can access the router IP. 

there is no techsupport for me to call except the telco and they won't touch my computer given their scope of work.

The only thing I can add is make sure after you update your server settings in Ubuntu to do a complete power cycle of everything you got there. Step by step.  DSL. Then router. Then system.

---

### Post by nik1979 on 2011-10-24
> **oldtimer7777 said:**
> The only thing I can add is make sure after you update your server settings in Ubuntu to do a complete power cycle of everything you got there. Step by step.  DSL. Then router. Then system.

thanks oldtimer, 
I'll report back when I do the following.

---

### Post by nik1979 on 2011-11-01
Sorry for the late reply. i tried using my laptop to access the router and I had the same problem. I think the Telcom company locked the system. 

The reason I took so long to reply was that I was getting more familiar with PBX servers like trixbox. I had to learn a bunch of stuff which I'm still trying to figure out in my spare time. 

Thanks for the help oldtimer, your probably right about that router. Its a P-660R-D Series ZyXel, issued by the Philippine Long Distance Telephone Company (PLDT) as part of its Phone with DSL plan. I followed the manual and there was no user given, nor the password worked. I tried online for a different manual as the one given and still no use. I tried using the reset pin and again, no use. 

I may have to buy my own ADSL2+ Router or Wireless Modem.I still have a long way to go to figure out wireless and network basics :(

---

