---
title: "Router question...???"
date: 2010-12-12
forum: General Help
---

### Post by robertcoulson on 2010-12-12
Hi, I was just wondering if there is there is any difference between a $29.95 router and a $109.95 router...???
Like is a more expensive router more apt to transfer data to my laptop quicker...??? 
Robert

---

### Post by Nexusx6 on 2010-12-12
There is most defiantly a difference being mostly in options available. $100 router will generally have a more robust firmware that will give the user access to more options and allow them to route traffic in more complex ways than a $30 router. 

A large portion of the price is also in the wireless capabilities. The most expensive routers at big box stores with have the latest Wireless N Draft with MIMO which boast very large theoretical coverage areas such has being able to be outside on the other side of the house and still receiving a wireless signal (This is rarely the actual case however).

So the question really comes down to, what do you need? Do you need high-bandwith large coverage wireless Internet, or do not even own a laptop? Are you planning on running a home server, or do you just want to connect to the net?

---

### Post by CharlesA on 2010-12-12
It's mostly a difference between speed and features.

The router I have now was a 60 dollar one that had Wireless N and 4 10/100 ports on it.

It works better then some of the more expensive ones I've seen.

---

### Post by robertcoulson on 2010-12-12
No, I have a new laptop and a cheap N router, it is in the basement and my laptop is upstairs...Was getting about 1/2 meg download a second, went and moved my router around and it jumped up to about 6.5 meg a second and moved it once more and can't get it back to 6 meg...Scary stuff...
Robert

---

### Post by CharlesA on 2010-12-12
Wireless signal loses strength when it goes thru walls.

---

### Post by Old_Grey_Wolf on 2010-12-12
> **Nexusx6 said:**
> There is most defiantly a difference being mostly in options available. ...

A large portion of the price is also in the wireless capabilities. ...


My house is 233m² or 2500ft². I needed 2 wireless G routers for connecting the computers in the house. With wireless N, I only needed one. With wireless G, I only got 54Mbps; however, with wireless N I get 200+ Mbps. That is computer to computer. My Internet connection is only 7 Mbps.  I have one of the more expensive routers that allows me to connect a 2 TB HDD to the router that can be shared between all the computers for backups and streaming video/audio files. 

The more expensive routers do give you more capabilities; however, shop around for the best price based on your needs.

---

### Post by robertcoulson on 2010-12-12
well CharlesA....Should I bring it upstairs with longer wires that connect it to my modem...???
Robert

---

### Post by robertcoulson on 2010-12-12
Old-Gray-Wolf....My (cheap) N router only says I get about 54 mega bits per second...Guess I new a more expensive router...Any ideas on what to buy...???
Robert

---

### Post by Old_Grey_Wolf on 2010-12-12
> **robertcoulson said:**
> Old-Gray-Wolf....My (cheap) N router only says I get about 54 mega bits per second...Guess I new a more expensive router...Any ideas on what to buy...???
Robert

Your computers need to have wireless N adapters. If the computers only have wireless G adapters then you will only get 54Mbps. If you have a wireless N router but the computers you are using only have wireless G network cards you will not see a speed increase.

---

### Post by CharlesA on 2010-12-12
> **robertcoulson said:**
> well CharlesA....Should I bring it upstairs with longer wires that connect it to my modem...???
Robert

Could try that, yes. Or get a bigger antennas, if your router has removable antennas.

---

### Post by robertcoulson on 2010-12-13
Maybe a bigger antenna...I know my router is an "N", but how can I tell if my new laptop card is an "N" or not...???
Robert

---

### Post by CharlesA on 2010-12-13
> **robertcoulson said:**
> Maybe a bigger antenna...I know my router is an "N", but how can I tell if my new laptop card is an "N" or not...???
Robert

It would say on the packaging. 

Anyway, you can get high-gain antennas, which might help, but only if your router has removable antennas.

---

### Post by robertcoulson on 2010-12-13
When you say the packing, I presume the laptop packing..Correct...???
Robert

---

### Post by katykat on 2010-12-13
One aspect of cheap routers not often addressed is that they have a tendency to overheat and lock up with heavy and prolonged data transfers.

---

### Post by CharlesA on 2010-12-13
> **robertcoulson said:**
> When you say the packing, I presume the laptop packing..Correct...???
Robert

If it came built-in, yes.

If you have an add-on card, what type it is should be listed on the box.

---

### Post by msandoy on 2010-12-13
> **katykat said:**
> One aspect of cheap routers not often addressed is that they have a tendency to overheat and lock up with heavy and prolonged data transfers.

This is specially a problem if you are doing torrent transfers, since those use many connections for each transfer. When you burn your fingers on the outside of the case, take the hint. In general, I would go for a mid range router, 60$ and up. Unless you have specific needs.

---

### Post by msandoy on 2010-12-13
Just some more info, personally, I have bad experience with Asus routers, burned out 2 of them in less then a year. Those were even 100$+ ones. I have good experience with Netgear and Zyxel. Those have not died on me yet.

---

### Post by robertcoulson on 2010-12-14
Well, my cheap router is a Dynex and right now with me positioning the antennas, My speed has gone to about 6.5 mega bits..Not too bad...But bottom line is I don't know if my built in card ONLY alowws 54 bps...???
Robert

---

### Post by Old_Grey_Wolf on 2010-12-14
> **robertcoulson said:**
> Maybe a bigger antenna...I know my router is an "N", but how can I tell if my new laptop card is an "N" or not...???
Robert

Enter this command to list your hardware
```
sudo lshw
```
Look through the output for the Wireless interface. The Product line may show 802.11 with the letters b, g, or n behind it. If it includes an n then it is Wireless N. If the 802.11 isn't there then I don't know.

---

### Post by CharlesA on 2010-12-14
Giving the make and model is laptop would help narrow it down too. :)

---

### Post by robertcoulson on 2010-12-14
Make and model is
Acer espire (I think) 
4 gig ram
750 gig HD
I5 processor

---

### Post by robertcoulson on 2010-12-14
oh it also says
Acer Npilify 802.11 b/g/n
Robert

---

### Post by CharlesA on 2010-12-14
Yep it's a Wireless N then. :)

---

### Post by robertcoulson on 2010-12-14
you know what CharlesA, when I finally got a good spot to leave the router downstairs, my web searching is fast...Even though it's a $29.95 router...I am happen now (so far ha,ha)...Is "N" the latest router, or (now that I have not spent a lot of money)should I buy a better one...???
Robert

---

### Post by CharlesA on 2010-12-14
Wireless "N" is the latest standard for wireless, and it should be fine. :)

---

### Post by robertcoulson on 2010-12-16
Thank you sir for the info...
Robert

---

