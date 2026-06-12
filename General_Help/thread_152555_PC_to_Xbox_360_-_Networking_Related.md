---
title: "PC to Xbox 360 - Networking Related"
date: 2006-03-30
forum: General Help
---

### Post by rubso on 2006-03-30
Hi, i want to share my Internet connection to my Xbox 360. how can you do it?
Note: i'm connecting to the internet through a wireless ( wifi ) adapter which is connected to a wireless router.
Thanks in advance.

---

### Post by JoshHendo on 2006-03-30
Umm, this has NOTHING to do with Ubuntu (wrong forum), except for the fact that you may also share the internet connection with Ubuntu. You will need to buy a wireless reciever for your xbox, then that will allow you to recieve internet on it :)

---

### Post by rubso on 2006-03-30
well, i used to share my connection to the Xbox 360 from WinXP without any problem, or recievers, and i believe Linux can do that, but i don't know how -_-!

---

### Post by RoboJ1M on 2006-03-30
Ah, do you mean you have a "wireless access point", not "wireless router".

And Access Point, or AP, is a wired2wireless bridge.
A Router is an internet connection sharing device.
(Google) 
If you have a wireless AP and you linux box has the internet connection, you can indeed turn your linux box into a router.

I can't really tell you how with ubuntu as I'm as new at this as you are.

What I do know it that I have several machines that are dedicated Linux Routers. I use Shorewall. Shorewall is a tool for configuring the advanced networking features of linux.

There are very good guides on how it all works on the Shorewall site, go here --> [http://www.shorewall.net/](http://www.shorewall.net/)

There are instructions on how to install the .deb version on that site too.

It's not nearly as click-and-go and the MS version, but it's better on a galactic scale.

However, if you're not up for hardcore networking, I recommend buying a Cable or xDSL dedicated router.

They are cheap and easy and now come with a lot of the advanced features linux supplies.

Regards,

J1M.

---

### Post by rubso on 2006-03-30
its quite clear right now , i guess take a look at the picture ;)
[IMG]http://i16.photobucket.com/albums/b10/rubso/clear.png[/IMG]

---

### Post by gorilly on 2006-03-30
surely your wireless router has 4 ethernet ports built in? cant you just connect your xbox using apatch lead?

i know what you mean about internet connection sharing i used to do it years ago when i had a stupid usb modem... having a router eliminates the need to do it.

---

### Post by dickohead on 2006-03-30
Step 1. Buy a switch.
Step 2. Buy a Router.
Step 3. Plug Internet into router.
Step 4. Plug router into Switch.
Step 5. Plug computers and X-Box 360 into switch with cat5/cat5e/cat6 ethernet cables (straight through)
Step 6. Set your pc's default gateways to the IP of your router.
Step 7. Play games online.

(This is how mine is set up and working)

---

### Post by RoboJ1M on 2006-03-30
OK, you *could* turn your new ubuntu box into a router.

But it's pointless.
Either plug your 360 into the router or get a wireless card/box/thingy for the 360.

In the case of you having no money or not being allowed to connect the 360 directly, you will have to enable routing on your Ubuntu box.

Only way I know how to do that is Shorewall or raw iproute2 configuration (not fun).

If you've go the money: buy a wireless client.
If you don't: Start reading Shorewall docs.

Reagrds,

J1M.

---

### Post by rubso on 2006-03-30
Thank you very much guys, Specially RoboJ1M

---

### Post by tsb on 2006-04-01
Doesn't the 360 have built in wifi?  A Wireless Router would be ideal.

---

### Post by Stew2 on 2006-04-01
[QUOTE=tsb]Doesn't the 360 have built in wifi?  A Wireless Router would be ideal.[/QUOTE]

Actually, the 360 doesn't have built in wifi for networking. I thought it did too, then when they came out I checked into it and the wireless they refer to is just for the controllers. Kind of sneaky advertising. I am sure though that on a prerelease write up they said that it would have built in wifi for connecting it to your home network. I personally would have preferred that to the wireless controllers :). This way they can sell you a wireless connector for about $130 Cdn. I think it hooks up to a usb port. I dont have one yet, I just like to watch the console wars. :-D 
Regards,
Stew2

---

### Post by rubso on 2006-04-04
lol stew, Microsoft Released a wifi adapter, but its too expensive and not worth it, i use Ethernet Cables instead a cheap option though ! ;)

---

### Post by NewbieNik on 2006-04-04
[QUOTE=Stew2] I thought it did too, then when they came out I checked into it and the wireless they refer to is just for the controllers. Kind of sneaky advertising.[/QUOTE]

From Microsoft??? I don't believe it....

---

### Post by craigmac on 2008-04-23
> **rubso said:**
> lol stew, Microsoft Released a wifi adapter, but its too expensive and not worth it, i use Ethernet Cables instead a cheap option though ! ;)

Hi, that's not entirely true. It is a little on the expensive side (mine cost CHF99) but it is rock solid and doesn't seem to be any slower than when I had it connected via Ethernet cable. 

I would say that if router ports are at a premium (mine are all used) then this is a handy way to get your Xbox Live on. 

BTW, the "built-in wireless" support is for controllers. It isn't advertised as built-in wi-fi - that's just wishful thinking on our part :roll:

Now to take a bath in disinfectant for appearing to defend Microsoft :lolflag:

---

