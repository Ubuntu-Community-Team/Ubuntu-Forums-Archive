---
title: "Keeping data secure when using a laptop"
date: 2009-12-01
forum: General Help
---

### Post by Scunnered on 2009-12-01
I am not to happy about having personal data on my laptop feeling that it is insecure particularly when working outwith my home.  My preference would be to be in a position where I store my data on a separate system within my house and access that data from my laptop.  Anything that I would work with being saved back to the system.  In the main when I use the laptop outside of the home it is purely to keep up to speed with news and e-mails.

I have an old system which I could use. Ideally as I have a wireless network I would like to have the old system kept well apart from my other equipment.

How best do I address this question.

---

### Post by nothingspecial on 2009-12-01
[[COLOR="Magenta"]ssh[/COLOR]]("https://help.ubuntu.com/community/SSH")

---

### Post by Scunnered on 2009-12-01
**nothingspecial**

Many thanks for your reply.

Lets see if I understand your suggestion.  According to my beginning Ubuntu  Linux book it would appear this is for connecting remotely or for a shared folder created for other computers in my home.  I do not wish to connect remotely as this would defeat the object of keeping data away from my laptop when outwith my home.  I wish to keep my data secure rather than let it float about the web willy nilly.

If I set up shared folders can they be accessed without opening up firestarter.  Both systems would be using Ubuntu and on the same wireless network?  I hope this is possible as I can't make head or tail of firestarter so far.

---

### Post by nothingspecial on 2009-12-01
So you want to sit in your living room and access your data that`s on a pc in the garage so that you don`t have any data when you go out and about? Then it`s even easier. Still using ssh.

On both machines type ```
sudo apt-get install openssh-client openssh-server
```

You may have one or both of these already. I have no idea what is the default on the latest `buntu.

Then on the computer with the data, right click on the network icon and choose connection information. Remember what the ipaddress is. Then go to your laptop and in the places menu choose connect to server.

In the first box choose ssh

in the second type ```
username@ipadress_of_other_machine
``` for example ```
scunnered@192.168.2.3
```

tell it to remember the password forever and give it a bookmark, just tick the add bookmark box and give your other computer a name.

Now when ever you are connected to your wireless network you will be able to access all the data on the other machine from the places menu in your laptop.

However, because you have just entered your local ip address this will not work when you are out and about because you are not connected to your router.

oh and go into your router settings and make sure to give your data computer a static ip otherwise it may be assigned a different one if you restart your router.

---

### Post by Scunnered on 2009-12-01
**nothingspecial**

Can you please confirm if I am right in my thinking.

From what you have advised it looks very much like I will have to do a complete fresh install of Karmic on my laptop. 

If I read things right the system that has to store all my data will be called the SERVER and I should identify it as such.

The laptop from which I want to access the data will be identified as scunnered @ an ip address.

As far as I can see both my partner and myself currently have the same IP address therefore the server will also have this address.  All 3 systems being connected to the one wireless router.  I assume that this is what you would call a static IP address and should meet your instruction OK.  I have been keeping a close watch on my broadband speed of late particularly as it kept falling off.  During the period the modem was rebooted often but the address remained the same.  I just got a new modem from the ISP and it similarly appears to be constant.  If you feel it necessary to set this specifically would I be right in going into Network Connections and editing my connection.  Is it the MAC address that I would put the numbers into? 

Currently I have organised printer sharing between my partner and my-self as my printer is connected via a USB connection on my laptop.  Would this still be OK to set up between both laptops or should everything go via the server?   

It looks very much like I will have a bit of work with the initial set up over the 2 systems but I feel it will be worthwhile.  

Other than my concern over IP addresses I feel confident from your instructions that I will be able to keep my data under close control.

My sincere thanks for all your assistance in this matter.

---

### Post by audiomick on 2009-12-01
hi scunnered.
You need to do some reading about IP Addresses and such like. I will look up a few things and give you a few links. Keep an eye on the forum for the next 20 minutes or so. I will do this now, but need a few minutes.

---

### Post by MoebusNet on 2009-12-01
If you're concerned that someone might access data on your notebook, one option might be to use Ubuntu 9.10 Karmic Koala as your OS. During the install process, it gives you the option to encrypt your hard drive (as I understand it) so that a password is required not only to log-in, but to access data on the HDD. Of course, you will want to pick a relatively strong password (as always.)

You can always boot from a Live-CD to confirm hardware compatibility before changing to Karmic. And of course back up all your data before doing anything that might put it at risk. Hope that helps!

---

### Post by audiomick on 2009-12-01
First of all, here is some reading:
[http://en.wikipedia.org/wiki/IP_Address](http://en.wikipedia.org/wiki/IP_Address)
[http://en.wikipedia.org/wiki/MAC_Address](http://en.wikipedia.org/wiki/MAC_Address)

You can change an IP address, you cannot change a MAC address

Don't bother if you don't understand absolutely everything. For your purposes, for a start, the first Paragraph of bot articles is the most important, so you know what you are talking about.

At the moment, IPv6 is not yet very relevant. Nearly everthing on the market is still using IPv4, as far as I know.

I should perhaps mention that I haven't used ssh. However, I have a small network at home: Desktop, laptop, printer, Network Area Storage (NAS), and in the course of my work as a sound engineer I have a lot of contact with IP addresses and such for applications involving network controlled digital audio devices.

> **Scunnered said:**
> 
From what you have advised it looks very much like I will have to do a complete fresh install of Karmic on my laptop.

I don't see any reason for this. All that nothingspecial suggested to install was the ssh client and server packages on both machines.

> If I read things right the system that has to store all my data will be called the SERVER and I should identify it as such.



> The laptop from which I want to access the data will be identified as scunnered @ an ip address.

Some more reference material...;)

[http://en.wikipedia.org/wiki/Server_%28computing%29](http://en.wikipedia.org/wiki/Server_%28computing%29)
[http://en.wikipedia.org/wiki/Server_computer](http://en.wikipedia.org/wiki/Server_computer)
[http://en.wikipedia.org/wiki/File_server](http://en.wikipedia.org/wiki/File_server)

Of your two machines, your storage system will be acting as a type of server. What you call it is up to you, but calling it "server" makes a certain amount of sense. ;)


> As far as I can see both my partner and myself currently have the same IP address therefore the server will also have this address.  All 3 systems being connected to the one wireless router.

Not right.

Your router / internet connection gets issued an IP address by your service provider.
This address is usually a temporary assignment, a so called "lease", which is typically renewed every 24 hours. Very many providers, as far as I know, reissue the same IP for the renewal.
The important thing is that the lease stops periodically. This has to do with preventing misuse of your internet connection from outside. I wont try to explain that any closer, as I don't know enough about it.

This IP address is visible to the outside world, and serves the communication between you home network, via the router, and the internet. It is your address in the internet.

The computers in your home network, ( you, your wife, the one "in the garage", your router, and anything else in the local network like a printer that is connected via network not usb), all have their own IP address.

_**It is not possible for two devices in the same network to have the same IP address !!!**_

The router deals with traffic between devices in the network. It is the post office. It reads the IP addresses and sends the communication to the right receiver.

> I assume that this is what you would call a static IP address and should meet your instruction OK. 

No. (see IP leases above)
A static IP is when you assign a device an IP address that never changes.
Within your home network, you can assign each computer and other device, via the system administration of the device itself, a static IP address. The alternative is DHCP
[http://en.wikipedia.org/wiki/DHCP](http://en.wikipedia.org/wiki/DHCP)

I hope that is the last wiki page...:p

There are good reasons for wanting something to have a static IP address. For instance, if you set up your ssh for your files, you don't want the "server" to have a different address the next time you turn it all on, or you wont be able to find it.

The thing is, at least according to a computer professsional friend of mine, if you want a fixed IP address on a Linux machine, you have to worry about routing tables and all sorts of other complicated stuff.

You will have noticed that nothingspecial said to "got into your router and give the computer a fixed IP address."
This is also how I solved the issue.
The Router has a fixed (local Network!!) IP, and is the DHCP server.

The Printer has a fixed IP. I don't think it can't get one via DHCP, and it wouldn't make much sense if it could, because it has to be static to be found.

My desktop, my (windows) laptop, and the NAS (which has a Linux operating system) all get their IPs via DHCP from the Router, _BUT_ in the router I have reserved an IP address to their respective MAC addresses, so they always get the same address each time it all gets turned on.

 > I have been keeping a close watch on my broadband speed of late particularly as it kept falling off.  During the period the modem was rebooted often but the address remained the same.  I just got a new modem from the ISP and it similarly appears to be constant.    

Covered in the paragraph about IP leases from your provider.


> If you feel it necessary to set this specifically would I be right in going into Network Connections and editing my connection.

You will have realised by now that this is not what is meant.;)


> Is it the MAC address that I would put the numbers into? 

Also no. As I said, you can't change the MAC address


> Currently I have organised printer sharing between my partner and my-self as my printer is connected via a USB connection on my laptop.  Would this still be OK to set up between both laptops or should everything go via the server?   
You can leave it on the laptop, but if it is on the server, you wont have to plug it back in every time you set up the laptop at home, and your wife can still use it when you are away somewhere with the laptop.


> It looks very much like I will have a bit of work with the initial set up over the 2 systems but I feel it will be worthwhile.  
Yes, it is a bit of work to set up, but when it is all up and running, it is great. :D

> Other than my concern over IP addresses I feel confident from your instructions that I will be able to keep my data under close control.


I hope the IP stuff is clearer now, and I am sure you will sort out the ssh stuff. :D

best of luck
Michael

---

### Post by Scunnered on 2009-12-02
My thanks again for your kind assistance.

**Audiomick**

As no doubt you will have worked out that I am new to this aspect of the Linux environment. I with all the kind assistance given on this site am making progress but in this area of networking am at a total loss.

You advise that you have a small network at home with Network Area Storage which if I am right in thinking is what I am aiming for.

My thoughts were that as I am enjoying retirement and accessing the internet at various hotels where often access is not on a secured basis that I did not wish to leave glaring holes in my security of data.  It was this that prompted the question and is now getting me into deep waters.  Basically what I want to be able to do is have everything that I consider matters safely stored away securely and when using my laptop externally have no worries about anyone accessing my data because there would be none to access other than the usual dozes of spam that I keep getting.

I understand the IP address aspect from the point of view that if I want to visit this forum, Ubuntuforums.org is the written address, where in fact the reality is four sets of numbers split by dots.  Where I have a problem is with this constant changing of IP addresses, the so called lease.  I am using VirginMedia and everything I see leads me to believe that my IP address is constant.

As I advised when I connect to speedtest.net it displays an address and irrespective of whether I am working with my partners XP system or my Ubuntu one.  I went to Gibsons ShieldsUp site and again it displays the same numbers.  Everything that I have checked keeps bring me back to a constant IP address.

You state that you haven't used SSH which prompts the question would your method suit my needs and would it get me out of the IP address problem.

My remark about a fresh install on the laptop was with the intent of having copied all my data from it that there should be no easily identified residue of information on my laptop.  As I have to set up what would be the server with Karmic and load all my data there then a matching fresh install on the laptop would have everything compatible. 

**MoebusNet**

I am happy that Karmic will work perfectly with my equipment. My preference is to keep my data out of anyones hands where possible therefore the idea of keeping it at home.  I like the idea of encription but have the picture of me having a senior moment and not even remembering where I wrote down the extremely safe password therefore negating everything.

Again my thanks to you all

---

### Post by unik999 on 2009-12-02
hello 
i am writing down few steps top protect data when working at wireless network 


[SIZE=2][COLOR=SeaGreen]Most wireless networks are completely unprotected when you first set them up. However, in just a few minutes, you can protect your wireless network by using the same method banks use to protect your password when you log on to their Web sites: encryption. Encryption scrambles data on your wireless network so that only computers that have the encryption key can read your communications.[/COLOR][/SIZE]
[SIZE=2][COLOR=SeaGreen]You have several choices for wireless encryption:[/COLOR][/SIZE]
[SIZE=2][COLOR=SeaGreen]•[/COLOR][/SIZE][SIZE=2][COLOR=SeaGreen]64-bit WEP (Wired Equivalent Protection). The original wireless encryption standard, it is now outdated. The main problem with it is that it can be easily "cracked." Cracking a wireless network means defeating the encryption so that you can establish a connection without being invited.[/COLOR][/SIZE]
[SIZE=2][COLOR=SeaGreen]•[/COLOR][/SIZE][SIZE=2][COLOR=SeaGreen]128-bit WEP. An updated, more secure version of the original WEP. However, skilled attackers can still crack 128-bit WEP in a few hours or less, giving them access to your network.[/COLOR][/SIZE]
[SIZE=2][COLOR=SeaGreen]•[/COLOR][/SIZE][SIZE=2][COLOR=SeaGreen]WPA-PSK (also known as WPA-Personal). A more secure alternative to WEP, but because it is newer, it is not as widely supported. Microsoft Windows XP with Service Pack 2 supports WPA, so this type of encryption is the best choice if you plan to connect only Windows XP computers to your wireless network. However, if you have wireless devices that don't support WPA, such as media extenders or wireless cameras, you'll have to use WEP on your network instead.[/COLOR][/SIZE]
[SIZE=2][COLOR=SeaGreen]You might also see the security method called "WPA-Enterprise." As the name suggests, this method of network encryption is designed for business use. Setup for WPA-Enterprise is more complex than for other types of encryption, and it requires special network infrastructure.[/COLOR][/SIZE]
[SIZE=2][COLOR=SeaGreen]•[/COLOR][/SIZE][SIZE=2][COLOR=SeaGreen]WPA2. The newest type of wireless encryption, WPA2 provides the highest level of encryption available. WPA2 encryption should be your first choice if your wireless router and all of your wireless computers and devices support it.[/COLOR][/SIZE]
[SIZE=2][COLOR=SeaGreen]Even though one type of encryption may be better than another, any type will dramatically improve your network's security by making you a more difficult target.[/COLOR][/SIZE]

---

### Post by Scunnered on 2009-12-02
**unik999**

Many thanks for your information.  My concern at this time is when I take my laptop out of my home environment.  I have the required security here OK and keep a close watch on things. I propose to work only in the Linux environment with my information to keep matters as secure as possible.

Again thanks for your contribution

---

### Post by audiomick on 2009-12-02
g'day Scunnered
First of all, thanks for the tip about shields up. I didn't know it exists, but can happily report that "there is no evidence that my computer exists" :p

The good news for you is that I have not taken any special actions to achieve this. The DSL modem and the router are both in their default settings, and the computer is Ubuntu 9.10, also default as far as Network goes.
To be more precise, what is protecting me is the firewall in the router. As I said, in the default setting "do not allow anything"
[http://en.wikipedia.org/wiki/Firewall](http://en.wikipedia.org/wiki/Firewall)
(once again, the first paragraph of the Wiki references is more or less all you need for now)


So, a bit more background.
Whether you are using SSH, or anything else that communicates via the ethernet protocol, 
[http://en.wikipedia.org/wiki/Ethernet](http://en.wikipedia.org/wiki/Ethernet)
the following applies:

[COLOR="SeaGreen"]First of all, the advice from Unik999 is good and appropriate.[/COLOR] I'll get back to that.

A quick word about your setup: I am assuming that you are on a Broadband connection that has a Broadband ( or DSL or whatever it is called there) modem and a router, which might be both in the one device, and all your computers get to the internet via the router. If this is not the case, it doesn't matter, as the principle is the same, but you might have to extrapolate to fit your setup.

The address that you are seeing at the Gibson site is the one that your Internet Provider assigns to your connection. If may be fixed, but, as I said, it is more likely to be a 24 hr lease that renews to the same IP every time. This is a basic security thing, _as I understand it_, that prevents, for instance, a Spam sender from masquerading longer than the lease as being you. Anyway, it is standard practice, and doesn't bear on your issue, at least not for starters. It might if you get as far as wanting to set up a VPN 
[http://en.wikipedia.org/wiki/VPN](http://en.wikipedia.org/wiki/VPN)
but I am not up on that either. I think it is also beyond your needs for starters.

To help you get your head around it, here's an analogy: The IP that your provider gives you is the one that is visible from the outside looking in along the wires in the internet.
Consider it to be the street address of a Hotel. That is how you find the hotel.
What the Gibson site does is turn up in the street outside and see if they can break into the hotel.

The IP addresses in your home network are visible from inside. When you start using wireless LAN
[http://en.wikipedia.org/wiki/LAN](http://en.wikipedia.org/wiki/LAN)
[http://en.wikipedia.org/wiki/Wireless_LAN](http://en.wikipedia.org/wiki/Wireless_LAN)
it gets a bit more complicated, because there are then 2 sets of IP address that your router is dealing with, the LAN ones, and the WLAN ones.

If the IP from your provider is the street address of the hotel, the ones in your local network are the room numbers. They let you find your way from one room the other. To get out into the street, the internet, you have to go out the front door.

To set up SSH communication at home between your laptop and your "server" computer, you obviously need the room numbers, not the street address, because all you are doing is going from one room to the other.

On your Ubuntu computer, go to System> System Administration> Network
( or something very similar; I have to translate, because my computer is installed in German for the benefit of my girlfriend ;) )
The window that opens will be greyed out. There is a button in the middle of the bottom bar that will be called "click here to make changes" or something. Click on that and enter your password.
**[COLOR="Red"]Be careful not to change anything here, or you might break your internet connection!![/COLOR]**
If you setup is as I have assumed, the should be a tick in the box next to the entry "cable connection", or a similar name. The other type of connection is "point to point", which doesn't apply if you are using a router.
Select that, and click on "properties" to the right.
In the pop up that opens, the first entry should be "configuration". Look at the drop down [COLOR="Red"]**taking care not to change it's selection**[/COLOR], and you will see that it offers the choice between "automatic configuration (DHCP)" and static IP.

Now I have to guess a bit, as I don't have a working Ubuntu computer with a WLAN card on it: There is probably also a category in there for wireless connections. The same applies in principle.

This is the IP address configuration that you are interested in for the purposes of SSH.

As I have already mentioned, I believe it to be simpler to leave that on DHCP and reserve an address in your router (refer to the handbook of the router, they are all different) for each computer, but if any one else has a word to the wiser, let them speak!


On the subject of encryption of wireless connections: yes, it is critical.
Another analogy: having your firewall set up properly is like putting all your documents behind a fence with a security man on the gate. If you run an unsecured wireless LAN, it is the equivalent to the putting up a billboard behind the fence, and pasting all your documents on it.

Here in Germany it is even a legal obligation to secure your WLAN access, to prevent people from "hitchhiking" onto your internet access and downloading illegal content. Don't forget; your provider knows who is behind the addresses it gives out, and if someone is hijacking your internet connection for dastardly deeds, the powers that be will come knocking on your door.

Another analogy: when you go into the internet via wireless LAN, it is not unlike ringing the porter in the hotel to get him to order you a taxi. Your computer speaks to the router via WLAN, and the router "goes out the front door" to get what you want.

**[COLOR="Red"]Encryption rule number one: the best security is a cable.[/COLOR]**

If you don't absolutely need the connection to be wireless, use a cable. If you always sit at your desk to work, always in the same place, leave the WLAN off and plug in a cable.
Apart from the security thing, there is enough electro smog in the world without creating more that isn't really necessary. 

I only switch my WLAN on when I want to use the internet of an evening in summer from the balcony, or when I feel it might be a tactical error to disappear into the office of an evening and leave my girlfriend alone in the lounge room...;) Otherwise, the laptop is plugged into a cable in the office, and the WLAN module on the router is switched off. (Refer to the manual of your router. Mine has an external hardware switch, many have only a software switch)

An ethernet cable can be up to 100 metres long, which should be long enough to get around most normal homes.

Having decided to use a WLAN, don't leave it on when you're not using it. A WLAN, by nature of it's function, is a bit like a kid jumping up and down and screaming "I'm here, I'm here". When you get your encryption happening, it shuts him up a bit, but he's still there.
I work on the theory that, should someone manage to break into my WLAN, and then the next time he looks it is not there anymore, he might lose interest and go away. Also, the less time the thing is switched on, the less time there is for someone to notice it and try and hack it. Just by the by, _everyone_ I know, when they find a WLAN, has look to see if it might let them into the internet. And I am not talking about criminals or teenage hackers, just normal everyday people.

As far as the encryption goes; as I said the advice from unik999 is absolutely correct. Your router may also offer MAC address filtering. For that you need to know the MAC address of the computers that you want to allow in, and if it is on, it is a pain if you have a guest who wants to get into the net (if you can offer him a cable, it is not an issue).
MAC address filters are easy to circumvent. I see them as being a bit like those steering wheel locks that you used to be able to buy that went between the clutch pedal and the steering wheel. A determined thief can get past them, but they stop joyriders.

When you are thinking about the encryption, the most important thing is to know what _all_ of the devices that are in the WLAN can support. You can only allow one type, so it has to be the newest one that all the devices can deal with.

I think I will leave it at that for now, this is long enough already..;)

I have got the thread subscribed, and will look back in.
Michael

---

### Post by Scunnered on 2009-12-02
**Audiomick**

It is reassuring that your network is working behind the router firewall and this gives me hope that I can similarly have my needs met.

In my case I am served by VirginMedia who supply my broadband connection via cable.  I have been provided with a modem and router which can either be used via ethernet or wireless.  Currently my partner and myself have laptops connecting via wireless.  As I wish to store my data well away from my modem/router I had proposed to again use wireless.  As an aside we have only just decorated so I have visions of me being strung up from a 100 M ethernet and launched from the highest window at any suggestion of running one.

Perhaps it is me being thick and still not getting my head round things.  If you have everything tightly buttoned up behind your router firewall can I assume that I should be able to do the same. If this is the case would SSH not be needed and with it the need to worry about IP addresses.

I have been reading about file sharing and if by using this can keep all my important files on the desktop system and access them from my laptop then I would be happy enough with that.  I should then be able to take my laptop outwith my home knowing that my data is secure at home.

I am seeking the easiest way of achieving my aim and it appears to me that things are getting over complicated and well above my grasp of computing knowledge.

I am a strong believer in the KISS principal as the last S typifies me.

Will file sharing meet my needs or should I be taken out and shot?

Thanking you for your kind assistance

Ian

---

### Post by winh8r on 2009-12-02
Hi,Scunnered
How did I know you were in Scotland????!!!!!!!!

would it not be a whole lot easier to just buy a USB External Hard Drive (you can get a 1000GB one in Aldi for about 70 quid) and keep all your sensitive files on that for super security.

That way you can use your laptop when you are out and about and if you need access to your secure files , you can pull out your external drive,plug it in and away you go!

It is about half the size of a paperback novel and your data is really secure as it is not actually on your laptop.

If there are reasons that you do not wish to use an external Hard drive then I would suggest following the advice of audiomick .

Hope you get a solution soon.
Aw the best!

---

### Post by nothingspecial on 2009-12-02
I think you are worrying about this too much.

Just do as I said. Remove all your data from the laptop you take out, put it on the one you leave at home and access it through ssh.

Don`t worry about ipaddresses (or however you spell it).

As long as you are behind your router at home, you are as secure as you can be.

---

### Post by audiomick on 2009-12-02
Hi Scunnered.
Read your post. No need for a shooting... ;)
I have to get to bed now, but I will give you a few more thoughts tomorrow afternoon.

For now, neither winh8r nor nothingspecial is wrong. It all depends on exactly what you want to do. File sharing is also an option.

Also, don't worry about the amount of information I am feeding you. You don't have to have a detailed and in depth knowledge of it, just a a basic grasp of the concepts. You can get what you need going with very little in depth knowledge of all that. I am just trying to reduce your "banging your head against the wall" quotient. ;)

Michael

---

### Post by Scunnered on 2009-12-03
It is said that a little knowledge is a dangerous thing and having that in abundance I sought your kind assistance.  It now appears to me that having received this assistance that I am being spoilt for choice and as a consequence getting into an allmighty guddle.

**Winh8r**

Having identified me as a Scot you then attempt to break the mould by asking me to SPEND MONEY!!!!! are you trying to give me a heart attack?   I was aware of that option but in the spirit of the times I was thinking of re-cycling as I have a spare desktop gathering dust.

** Nothingspecial**

I like very much your quote &#8220;*As long as you are behind your router at home, you are as secure as you can be*&#8221; as this reinforces what I saw in Audiomick's post when he said &#8220;* what is protecting me is the firewall in the router*&#8221;.

If I then substitute my desktop for Winh8r's external HD and follow your advice of using SSH my only problem area is this IP address.  You show the code &#8220;scunnered@192.168.2.3&#8221; as being required and I would ask is it as simple as substituting my IP address.  This up till now is the rock that I am perishing on.

**Audiomick **

Both you and Nothingspecial are in agreement that provided I am behind the router I am safe and that assurance is exactly what I was looking for.  How do I embrace all this security?  Is it as simple as just having both my laptop and desktop behind the router firewall or need I do more.

==

Each and everyone of you have added to my knowledge, all the total confusion is totally down to my inexperience in computing.  You have got me far along the road to a conclusion and I ask from you how do I get there?

Again my sincere thanks for all your kind assistance.

---

### Post by nothingspecial on 2009-12-03
Assuming your username is scunnered then yes it is just a matter of substituting the correct ip address. 

Did you put ubuntu on the other computer yet?

---

### Post by Scunnered on 2009-12-03
**nothingspecial**

I have had a dummy run on the desktop system by using the live CD.

Strangely enough your code suggestion of scunnered could be a possibility for one of the systems.

I think that I will wait until Sunday when I can devote some time and close attention to the matter in hand.

This post gives me final assurance that I now know what should be done.

Once again my sincere thanks

---

### Post by audiomick on 2009-12-03
Hi Scunnered.
Looks like you're starting to see the light at the end of the tunnel. Great.

Regarding the suggestion from winh8r to use an external USB drive: It is a valid suggestion, but as you yourself pointed out, you already have the computer, and may as well use it.

One advantage of that is, as I already pointed out, you can move the printer to the desktop machine, the "server", and wont have to worry about plugging it into the laptop every time.
Also, I assume your wife will also end up having date stored in the "safe storage". If it is an external usb drive, it is plugged into one or the other of your laptops, i.e. access for one at a time, unless you do a rather circuitous file sharing thing.
It is also another computer in the house that can presumably get into the internet if need be. Given how important it is these days to get into the net, for instance to find out how to set up SSH ;), a backup computer is not a bad thing.


At the risk of running up against the Scottish nature, you might want to think about putting a second disc in the desktop, or plugging an external drive into it, for the purpose of backing up the really important stuff. Of course you can always just put it on a DVD or CD, but that leads to lots of CDs lying around fairly quickly. At any rate, bear in mind that having really essential stuff on only one hard drive is rather optimistic, to say the least.

As far as being safe behind the firewall goes, I get the impression that you are getting a grip on that. Once more for luck: You have two issues; 

the firewall in the router, which is controlling the traffic between your network at home and the internet, and

the encryption for your wireless LAN, which stops unwanted "guests" sniffing around in your home network and hijacking your internet connection.

On the question of whether to use SSH or file sharing, I think it comes down to how safe you want to be, and what else you might want to do.

File sharing just lets you move files from one place to the other. As far as it goes, if you have your firewall buttoned down and your WLAN properly encrypted, it should be safe enough.

I had a quick look at SSH, and how you connect it. It would seem to be not a great deal more complicated than setting up file sharing, if at all, so six of one or half a dozen of the other...

The advantage of SSH would be that the connection that is made is secure, analogous to moving your files around in an armoured car. On top of that, SSH opens the way to remotely operating the computer that you are connected to. Whether or not that is interesting to you is something that only time will tell.
Also, if you get to the point where you want to attempt to access your files from a hotel somewhere (might well happen), if you start with SSH now, you are already on the way to being able to do that (i.e. setting up a VPN via SSH )

Regarding the vexed question of the changing IP addresses: I hope you are a bit clearer on that.
The point is, whether you use file sharing or SSH, you need to take steps to make sure that your laptops and the desktop always have the same IP in the home network.
The file sharing also needs to know where the other computer is, although I think Samba just uses the computer name. At any rate, if you know what address the various computers have, it saves confusion. 

And it is really not hard to organize!

As I already mentioned, refer to the manual of the router ( do you know about the RTFM solution? Applies to the greater percentage of problems with computers and other machines. RTFM :- Read the *"fantastic"* manual... ;) )
Reserving addresses in the router seems to me to be the easiest way to go about it, and means that you don't have to change your laptop between DHCP for public access points in the hotel or wherever and static address for home.

You may well be wondering what to choose as an address. Your router will more than likely have a default IP ( the one that is visible inwards to your home network, not the one that is issued by your provider that the router shows the "outside world" in the internet ) in the range 192.168.xxx.xxx , or perhaps 10.000.xxx.xxxx. My brother tells me that you get the second one as often as not in Australia. In Germany ( EU land, same as UK ! ) they are all in the first one.

There is nothing mystical about these addresses. Theoretically, you could choose a random number between 0 and 255 for first three positions, the same on each machine, and a different number chosen at random between 0 and 255 for each machine, and it would work. Correction, I think 0 and 255 might be reserved for specific functions, so between 1 and 254.

The thing is, there is a bunch of blokes somewhere in the world who spend time thinking about keeping the internet working, and the have created "rules" for the assignment of IP addresses. I think there is something about that on the wiki page that I linked you to.
The 192.168.xxx.xxx range is simply a range intended for the sort of applications that you are  thinking about, i.e. small enclosed local networks.

I would suggest 192.168.0.1 for the router, or simply leave it on it's default, which may well be that anyway.
For the other machines, 192.168.0.2 , 192.168.0.3 , 192.168.0.4

The important thing is that the first three positions are the same, and the last one different.
Maybe your router has a 1 or a 2 or something else in the third position. This is fine, so long as everything else has the same thing. Otherwise you would need to change the subnet mask. This will default to 255.255.255.0 , and is fine like that.

That's enough for now, isn't it...;)
I will look in again tonight after work.
Michael

---

### Post by Scunnered on 2009-12-03
**audiomick**

From memory it was RTFM that got us all into this confusion. I had a look at my Ubuntu Linux book and that threw me, therefore the initial request.  There are times that I have found that the forum offers far better clarity.

I am going to take things slowly. As I said to nothingspecial I am proposing to devote Sunday to the task and take things carefully.

I will see how things work out and report back to all concerned.

Wish me luck

Ian

---

### Post by nothingspecial on 2009-12-03
Backing up your data is vital.

I once lost 20,000 songs when the hard drive they were on died. Luckily I don`t download music I buy it so I had all the cds but it took me over a month to get back to where I was. 

I now store them on an external drive plugged into my server which resides in the garage. I have another external drive and have set it up so that they both synchronise every night, giving me 2 copies of all my music, therefore if one dies I have another.

I am even more paranoid about my wifes college work.  I`m the IT specialist in this house so if she lost it I would be dead, well she might let me live but I`d probably never walk again. I have set up her laptop just as I described to you. Each night she opens up the server on her laptop and copies her work across. But I have set the backup to backup again on a further drive. The same system exists for our photos, movies and other data.

Infact the reason I dived in on this thread in the first place is that you sounded like you wanted a similar set up to me.

I have some stuff on my laptop, sure. But I can access all the data I have, music, photos etc from my laptop even though it physically resides on my server in the garage.

I rarley touch the server but use it every day. If I need to download a large file or torrent I let the server do it to free up my laptops wireless caperbilities. I seed various linux distros from it. If I want to convert video or sound, I let the server do it. It also streams music all round my house. It`s a workhorse that enables me to use my other computers processing power to do whatever I`m doing at the time. I do it all (except the music streaming) through ssh.

I think, once you get started and start to have a play around, you`ll see ssh is one of the most useful tools available in the Ubuntu repositories.

---

### Post by audiomick on 2009-12-03
Hallo again.
here are a couple more things:
If you want to go into the router, use a cable. You would have read the manual by now, I am sure, probably several times. ;) Normally they have a web based setup interface, that is to say, you type the IP address of the router into the address bar of your web browser ( Firefox, or whatever you're using) and a thing opens up in which you can do your setup.

This is accessible via WLAN, but it is advisable to plug in a cable. If you change something to do with the wireless connection, you will probably lose the connection when you confirm the change, and if something goes wrong, you might not get back in. On a cable, as long as you know the IP that the router has, you will get in.

You might be wondering how to find out the MAC address of your Laptop. Generally they have stickers on the underside, one for the ethernet connection and one for the WLAN connection. If these are gone, you can right click on the icon for network connections that should be in the task bar. As I said, at the moment I don't have an Ubuntu computer with a wireless card in it, but from memory there is one for the wired connection, and one for the wireless. Anyway, right click, choose properties, and look at the second tab. There you can see the current IP address for the connection, and the MAC address.

Do you know about ping? This is a command that goes and has a look if there is someone at home at the address you enter.
[http://en.wikipedia.org/wiki/Ping](http://en.wikipedia.org/wiki/Ping)

Open a terminal and type in the IP address of the device that you think you should have a connection to.

```
ping 192.168.0.1 (*or whatever the appropriate address is)*
```

If it works, it will look  like this:

```
mick@ubuntu-desktop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=9.43 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.230 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.244 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=0.242 ms

```

If it doesn't, it will look like this:

```
mick@ubuntu-desktop:~$ ping 192.168.0.5
PING 192.168.0.5 (192.168.0.5) 56(84) bytes of data.
From 192.168.0.3 icmp_seq=1 Destination Host Unreachable
From 192.168.0.3 icmp_seq=2 Destination Host Unreachable
From 192.168.0.3 icmp_seq=3 Destination Host Unreachable
From 192.168.0.3 icmp_seq=5 Destination Host Unreachable
From 192.168.0.3 icmp_seq=6 Destination Host Unreachable
From 192.168.0.3 icmp_seq=7 Destination Host Unreachable
^C
--- 192.168.0.5 ping statistics ---
10 packets transmitted, 0 received, +6 errors, 100% packet loss, time 9018ms

```

The odd thing is, if it is successful, it seems to go on forever. If you do a ping in windows, it does four and then stops. In the Linux terminal it doesn't, or I haven't ever had the patience to wait till it is finished. You seem to have to close the terminal to stop it.

Edit: You learn something ever day.... Ctrl + z stops it. :-)

The point is, the ping command ( the name comes, appropriately, from the noise a submarine makes with it's sonar ) sends a request for an answer at the most basic level of the ethernet protocol. If the connection is there and the IP address is right, you get an answer. If you don't, there is no connection, or the IP is wrong. No ifs or buts about it.
It is the single most useful tool for problem solving in network configuration. If your connection doesn't work, but you have a successful ping, then the problem is in your configuration or the program that is trying to make the connection. If the ping is not successful, then you need to check IPs and the basic functionality of the connection.

At this point, I wish you a heartily successful day on Sunday. I am looking forward to hearing how you got on.

best of luck,
Michael

---

### Post by Scunnered on 2009-12-04
**nothingspecial**

You have hit the nail on the head. This is exactly what I want. Like you my life is in constant danger if anything goes wrong with ***she who must be obeyed's data***.

At the moment she insists on keeping her photos on her system and having backup. So far it has not completely taken over the world but is getting close. It was the extra storage space on the HD that prompted the desktop for the purpose.

**audiomick**

I will take this one step at a time for the moment.  Once I get everything up and working after Sunday I will have a close look into what you say.

I had noted your remark about the final digit in an address as normally ending in ONE but as my previous address ended in 23 and my current in 6 this prompted me to take a step back for the moment.  Obviously some care must be taken so I will do more reading and see how I get on from there.

Again my thanks to you both for all your kind assistance

---

### Post by audiomick on 2009-12-04
Hallo Ian

> **Scunnered said:**
> 
I will take this one step at a time for the moment.  Once I get everything up and working after Sunday I will have a close look into what you say.


The last post was actually intended to help you on Sunday...

I probably write too much;)
I will summarize:

**_IF_** you are wanting to do something in your router, it is a good idea to get ahold of an ethernet cable and pug it in, rather than do it over wireless.

**_IF_** you need to know a MAC address, it is usually on a sticker on the underside of the Laptop. Otherwise it is easy to find in the computer.


**_IF_** you should have a connection problem, "ping" is a great tool to see if the basic connection is goood.


You haven't said exactly what you are planning, but I was assuming an SSH connection.


> ...your remark about the final digit in an address as normally ending in ONE...

Don't let my flood of words confuse ;). The **default** address in a lot of things often ends in one, but this is **arbitrary**.

You can leave it as it is, or change it to whatever you want between 1 and 254. 
The more important thing is that the first 3 positions are the same.

>   Obviously some care must be taken..
Some care sure. Don't forget, you are dealing with devices that are intended for the consumer mass market.
If they are too hard to operate, they  will fail on the market, therefore, they aren't hard to operate...;)


And another thing: what we are talking about here is stuff that is highly unlikely to break your operating system. At the worst, you might mess up the WLAN connection.
So, don't worry too much.

Safety precaution? Don't try to do the whole system at once.

Get the communication happening between one laptop and the desktop, taking careful notes of what you do.

The other system ( best if it is your wife's doesn't get used for the "experiment"... ;) ) remains untouched for the time being, so you can still get into the net and get help on the off chance that it goes pear shaped.

Once the first one is going, repeat the steps on the second.

You'll be right mate,
Michael

---

### Post by Scunnered on 2009-12-06
**Nothingspecial**

Here we go again.

I decided that I wanted both the desktop and laptop systems to be identical in set-up and downloaded Karmic yesterday.

I started with installing it to the desktop and on entering the first set of code the following error message was displayed :- 

&#8220;scunnered@scunnered-desktop:~$ sudo apt-get install openssh-client openssh-server 
[sudo] password for scunnered: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
openssh-client is already the newest version. 
Package openssh-server is not available, but is referred to by another package. 
This may mean that the package is missing, has been obsoleted, or 
is only available from another source 
E: Package openssh-server has no installation candidate&#8221;

I then did a fresh installation to the laptop and when the code was entered everything seemed to work OK.

Reverting to the desktop and right clicking on the network (Places > Network) I did not see anything about connection information and was not able to find an IP address.  However as my partner's XP machine is set-up to share her information was visible.   If I go to network on the laptop exactly the same situation applies.

I then decided to have a try at following the instruction for the laptop and where it displayed Service Type selected SSH.  I then in the server area entered scunnered@ IP address which then displayed the error of :-

Cannot display location: sftp://

At this point I decided that I must call on further assistance.

Should I stop the windows share initially?  I can see windows on both the desktop and laptop but nothing between the Karmic systems.

I am really struggling to get my head round the IP address situation. You advise that I should give the data computer (desktop) a static IP.  Can you please give me a walk through how I achieve it?

My Ubuntu Linux book was for 8.04 and the details do not correspond with the current displays. From what I can see from System > Preferences > Network Connections and following the example in the book if I edit the wireless connection and click on Ipv4 settings and change the method to manual that I am able to add an address. The book shows three items :

IP address,  Subnet Mask & Gateway address

and this is the rock on which I perish.

I found something in Network Tools which gave me some information but not all.  It gives an IP and Net mask (is this equal to Subnet Mask) but no gateway address.  I am starting to see where audiomick advises that the address is a movable feast now  having flitted in and out of this area I have seen at least 2 different sets of numbers.
  
Where OH where do I get this information? 

Do I have to allocate an individual IP address for each system or is it just for the desktop.

I am sorry to have to throw myself upon your mercy yet again and sincerely hope this will be the last.

---

### Post by nothingspecial on 2009-12-06
Hi Ian,

Firstly, did you update your new installation before attempting to install ssh
```

sudo apt-get update && sudo apt-get install openssh-server openssh-client
```

After doing this, go to the machine with the data on it and right click the network icon, choosing connection information, this will tell you that machines ip address. It will be something like 192.168.1.3. Do not worry, this is just an address on your home network. Nobody from outside your home network can use this address to access your computer.

Go to your laptop and click places > connect to server, like so ...

[ATTACH]138783[/ATTACH]

Then add the information like so

[ATTACH]138782[/ATTACH]

I gave you some missinformation before, in that I thought you needed your username, this is not necessary, just the ip address.

Once you click connect, your other computers file system will appear on your desktop. You only have to go through this process once. From now on you can access your other computer through the places menu.

If for some reason this is not working, try it through the command line to confirm that ssh is installed correctly. Please substitute the correct username and ip address

```
ssh ian@192.168.2.5
```

---

### Post by nothingspecial on 2009-12-06
Ian,

I hope I haven`t confused you. In the first screenshot, the pointer is in the wrong place. It is the highlighted box "connect to server" I want you to click.

This is because I tend to do stuff with the keyboard and not the mouse. The pointer is just where it happened to be.

---

### Post by audiomick on 2009-12-06
Hallo Ian,
Keep your chin up, you'll get there!

I'll keep it short this time...;)

Net mask is the same as subnet mask. It is a way of telling the computer how much of the IP address is relevant. For your purposes leave it at 255.255.255.0

If your interested, you can read up on it when you get your stuff sorted.

You can generally leave the gateway address empty, I think, or on the default. That is the address (internal, not external) of your "gateway" to the internet, i.e. the router. I don't recall ever having entered a specific gateway address, and have never had problems with it. I think it only becomes an issue in bigger networks.

Once again, don't despair, and good luck!
Michael

Each device in the network must have it's own individual address. Using the subnet mask 255.255.255.0 , the first 3 positions of the IP must be the same, or the devices can't see each other. The 4th position must be different for each device, or you get IP address conflicts.

I believe that the WLAN (wireless) and LAN (cabled network) that the router administrates constitute 2 separate networks, and that it isn't a problem if a device has the same IP for it's wireless and it's cabled network connection.

Once again, I would suggest a look in the manual for the router to see if you can't reserve IP addresses for the computers in there. I find it easier that way.

---

### Post by Scunnered on 2009-12-06
**Nothingspecial**

Well spotted I immediately applied your code when I installed Karmic.  Went round again and everything took OK.

Am still having problems with Places > Network as I still keep being shown all the windows information.  Went and stripped out windows shares and tried everything again.  Both the desktop and laptop when clicking on the Places > Network still show the windows info.  I have attempted to delete all the details of the windows network data from the system but they can't be removed.  Should I go right back to the start and re-install everything again?

As I could not get any IP address to display by right clicking on the Network on the desktop I looked at System > Administration > Network tools and it displayed an IP address.  I then went to the laptop and entered that information as instructed.  This time around it took the data and when I clicked add bookmark and provided a name it immediately went into if my thinking is right as the root directory (see attached).

I then followed your suggestion of checking the ssh and when I did this the following was displayed:
&#8220;ian@ian-laptop:~$ ssh ian@127.0.0.1
The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established. 
RSA key fingerprint is c5:34:89:37:3e:86:2c:dc:fb:4b:f7:80:dc:6c:e2:d5. 
Are you sure you want to continue connecting (yes/no)? y 
Please type 'yes' or 'no': yes 
Warning: Permanently added '127.0.0.1' (RSA) to the list of known hosts. 
ian@127.0.0.1's password: 
Linux ian-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 &#8221;
Where it asked for a password I supplied one but once again everything sent straight back as per the example.  The places menu now shows SFTP on 127.0.0.1 but clicking on that just brings up the root directory.
How do I set-up the static IP?  Do I go into System > Preferences > Network connections and add the 127.0.0.1 and audiomicks 255.255.255.0 ?

**Audiomick**

I would love to be able to read the router manual but VirginMedia who is my ISP do not have one. They provide a Wireless Set-up guide and a CD for use with windows and that's your lot.  If I phone them and ask them how I can set-up a static IP and say that I am using Ubuntu I will be asked what? OK so I say Linux when they immediately have a hissy fit and state that they don't support Linux so you can see how I am having problems here.

---

### Post by t0p on 2009-12-06
> **nothingspecial said:**
>  Luckily I don`t download music I buy it

Sorry for the off-topic aside, but I couldn't let that one go by unchallenged.

nothingspecial, what you said implies that people who download music don't pay for it.  That's a horrible libel and you should withdraw it forthwith!

---

### Post by t0p on 2009-12-06
> **Scunnered said:**
>   I would love to be able to read the router manual but VirginMedia who is my ISP do not have one. They provide a Wireless Set-up guide and a CD for use with windows and that's your lot.

Is there any particular reason you feel you have to rely on your ISP to give you a router manual.  There are lots of manuals available on the internet.  All you need is the router's make and model - Google will do the rest.

---

### Post by audiomick on 2009-12-06
Hey, progress is occurring!

Virgin Media are a pain then, aren't they? I get the same deal with my bank for the online banking function. They officially support the protocol for the connection, but don't want to know about Ubuntu or Linux. Just for the record, the router doesn't even know whether it is talking to a windows, mac, or linux computer.


The following are just thoughts that occur to me. Please don't feel like I am trying to persuade you to do anything. Setting a static IP in the laptop is fine; just bear in mind that if you want to use a public access point at any stage, you will almost certainly have to change it to DHCP for that, and back to the same static for at home that you use to set this stuff up.

As far as the router manual goes, as tOp said:
> Is there any particular reason you feel you have to rely on your ISP to give you a router manual. There are lots of manuals available on the internet. All you need is the router's make and model - Google will do the rest.

I didn't think of that, but he's right.

Also, have a look (with your Ubuntu Laptop) on the CD that came with the router. There might be a PDF manual on there.

If you haven't already shut the book on the hotline, you could try ringing them and asking how to reserve an address _in the router_. You don't have to mention that you are using Ubuntu, because the function is completely independant of the OS. If they tell you to use the windows cd, maybe you can borrow a windows machine from a mate.

What is maybe worth a try, if you have the energy, is, if there is mention any where in the wireless guide of a default IP for the router, type it into the address window of your web browser. You _might_ find it has a web browser based control interface. 


You have achieved an entry in your places menu for the machine at 127.0.0.1 which brings you into the root menu of that machine. Can you navigate through the folders there? If so, try going to the folder where you will be storing your data, and repeating the step that nothingspecial gave you to set the bookmark.

---

### Post by Scunnered on 2009-12-06
**t0p**

Thanks for the suggestion of seeking out a manual on google.  I will give that a try.

I think you were a bit quick getting on to nothingspecial as if you had fully read the post you will see that he stated "L***uckily I don`t download music I buy it so I had all the cds" *** a remark that I took to be lucky him as he had not to back round and round again purchasing music that he had already paid for.

**audiomick**

I will see if I can find online my manual if not I will be onto Virgin like a shot.  I do not have to try too hard to act daft, it comes naturally

Again thanks to each for your assistance

---

### Post by audiomick on 2009-12-06
I just edited the last one, so once again, in case you don't see it.

Have a look on the CD from the router with your Ubuntu Laptop. There might be a PDF file on there that is the manual.

---

### Post by Scunnered on 2009-12-06
**audiomick**

t0p's suggestion worked ok.  Found online now only have to follow things through.

Will have to delve into this some more but looks like I can get the static IP.

Thanks again

---

### Post by nothingspecial on 2009-12-06
> **t0p said:**
> Sorry for the off-topic aside, but I couldn't let that one go by unchallenged.

nothingspecial, what you said implies that people who download music don't pay for it.  That's a horrible libel and you should withdraw it forthwith!

No, you created that implication in your own (guilty or not) mind.

All I meant was that, luckily, I had the hard copies (cds) in my possession and was able to start reripping them immediately. I am well aware that you can download music legally, I just like having cds and lps.

@scunnered

Ian, you have successfully achieved what you intended to do. The root directory you see, is the root directory of your other computer and you access your files by simply navigating home/ian/documents, or whereever your stuff is located. :)

If you click on a picture it will be displayed on your laptop even though it physically resides on your other computer. The same is true for music, videos, pdfs. etc etc etc.

---

### Post by audiomick on 2009-12-06
> **Scunnered said:**
> **audiomick**

t0p's suggestion worked ok.  Found online now only have to follow things through.

Will have to delve into this some more but looks like I can get the static IP.

Thanks again

Fantastic.

Let us know how things develop, eh?

---

### Post by nothingspecial on 2009-12-06
@tOp

actually, rereading, I can see what you mean, I should have said, luckily I buy cds and lps rather than mp3s. Challenge accepted.

@scunnered

The static ip thing is not a major issue. You can connect to your other computer in this way again if your ip changes. It`s just easier if it remains the same. The important thing is that you`ve successfully connected yout 2 computers.

---

### Post by audiomick on 2009-12-06
@ nothingspecial
I just wanted to let you know that I have learnt something useful from you. I will be looking into setting up an ssh connection between my desktop and my vista laptop. Thanks.
Michael

---

### Post by nothingspecial on 2009-12-06
Everything, (well almost), I know about linux, I learned here, or rather was directed to from here. The fact that so many users pass the info along is what makes Ubuntu so successful.

---

### Post by Scunnered on 2009-12-06
**nothingspecial**

Something has gone wrong somewhere.  When I go to the laptop and click on the SFTP link as stated it opens up root folders.  Following what you say when I access the home folder I should see the home folder for scunnered and find my backup folder.

This is not the case what I see is the home > ian which when opened is everything that is on the laptop.

Can you please offer further guidance

Ian

---

### Post by audiomick on 2009-12-06
Hi Ian.
I reckon you've got your IP addresses mixed up, i.e. put the one for the laptop in instead of the one for the desktop.

I have just successfully opened the file system for this computer from this computer via ssh.

---

### Post by nothingspecial on 2009-12-06
Are you going to the right folder?

Aslong as the ip address is correct there should be no problem.

Check your private messages on ubuntu forums.

---

### Post by nothingspecial on 2009-12-06
Ian,

It`s not wrong, you are seeing your other computers root file system. It looks the same. Let me grab my wifes Ubuntu laptop and show you.

---

### Post by Scunnered on 2009-12-06
**audiomick**

You are determined to drive me to drink!!!!.  Not that I need any assistance in that department.  I have opened up the network tools and in each case find that both the desktop and the laptop display the identical IP Address.

The desktop is the system where I have placed the backup data and it is this that I want to read when I open up my laptop.  

Using these identifiers how did you set-up your data and reading systems.

I appear to be out of step with everyone else and it is geting me down. Could the fact that my laptop was purchased as a Ubuntu specific system cause these problems?  I had attempted to dual boot the system only to find that it would not accept windows and was advised that I would require to have the boot set-up altered if I wanted windows.

Your kind assistance will be most appreciated

Ian

---

### Post by nothingspecial on 2009-12-06
They look the same but they are not. On the left is the remote one, on the right is the computer I am using.

[ATTACH]138840[/ATTACH]

---

### Post by Scunnered on 2009-12-06
**Nothingspecial**

Firstly many thanks for the PM.  Following your instruction I have now achieved my aims.  This will I hope give me many hours of peace perfect peace.

Having completely shut down both systems and re-booted everything works a treat. The only thing that I have a minor problem with that so far I have to re-enter the server connection every time.  The remember password always does not seem to take.
Will give it a little longer to see what develops and read up on the SSH info.

**Audiomick **

Thanks for all your assistance in this matter.  While I have not embraced  your solution this time it has prompted me to look further into matters and no doubt it will still stand me in good stead later.

To everyone who offered their kind assistance my sincere thanks.  This has been some learning curve and I appreciate your patience and understanding in bringing matters to a conclusion.

Ian

---

### Post by nothingspecial on 2009-12-06
> **Scunnered said:**
> **Nothingspecial**
 The only thing that I have a minor problem with that so far I have to re-enter the server connection every time.  The remember password always does not seem to take.
D


Don`t worry about about it. That is the issue with static ips, that audiomick was helping with.

It can be done at a later date.

For now, you have done what you wanted. We will deal with static ips at a later date 

:D

---

### Post by audiomick on 2009-12-06
Hallo again Ian.
I was halfway through another novel when I noticed that you had posted again.

I am glad that you have got to where you wanted to be. I know only to well how frustrating it can be to try and work this sort of thing out. Good on you for sticking it through.

I hope you have got a bit of a "feel" for the business with IP addresses. For my part, I have learnt how SSH works, and will no doubt get on to setting it up between my desktop and my laptop, so thanks to you for broaching the topic.

I will keep the thread subscribed, so if you have anything new to report, please do so.

Michael

edit: or PS
> I have opened up the network tools and in each case find that both the desktop and the laptop display the identical IP Address.

Don't forget, you can't have the same IP twice in one network. If you do, change one.

---

### Post by nothingspecial on 2009-12-06
Michael,

If you have a question about ssh, ask.

In my experience it is the most useful tool I have. 

Using another computer, to do your jobs, has got to be a good thing...... if you ever need any pointers.........

---

### Post by audiomick on 2009-12-06
> **nothingspecial said:**
> Michael,

If you have a question about ssh, ask.

In my experience it is the most useful tool I have. 

Using another computer, to do your jobs, has got to be a good thing...... if you ever need any pointers.........

Thank you for the offer. :p

---

### Post by nothingspecial on 2009-12-06
Not that I`m some kind of expert or anything........

Just a user;)

---

### Post by audiomick on 2009-12-06
> **nothingspecial said:**
> Not that I`m some kind of expert or anything........

Just a user;)

Me too. We all help each other...;)

---

### Post by nothingspecial on 2009-12-06
Yes

end now before this turns into High School Musical and we both start singing about how good Ubuntu forums is  

:popcorn:

---

### Post by winh8r on 2009-12-10
Hello again,

I chipped in with a comment early on in the "Saga of Scunnered's Security" and have just popped in to say what a perfect example of the Ubuntu spirit this thread is.
Well Done to audiomick,nothingspecial and scunnered each of you learning and sharing in your own way and most of all helping thousands of other users by sharing the how to's and the "it doesn't" parts of this solution.
All of this was helped by an absence of technobabble and an honest and straightforward explanation of every stage.

PS. Scunnered - As a Scot, I wasn't suggesting that you purchase anything ,I was merely indicating that it was near enough the time of year when you can ask for "specific" gifts !!!!!
Hope that you have many hours of fun in your retirement with your good lady not only happy with the security set-up but also suitably proud of you for tackling it and seeing it through.

All the best to all three of you.

---

### Post by Scunnered on 2009-12-11
**winh8r**

Thanks for your kind comments.

Your remarks particularly in the ***sharing the how to's and the "it doesn't" parts*** of this solution as there is no doubt without the interaction of all concerned things could have ground to a halt.

I keep an eye on other forums and often find that RTFM rears its ugly head or that the post grinds to a halt. There appears to be an assumption that either the manual is clear, not often the case, or that the original poster has more knowledge and what is perfectly clear to the expert is totally beyond the comprehension of the poster.

There is no doubt without the kind assistance of nothingspecial and audiomick that this thread could have gone down that road and it is to their credit that they did not abandon me to the fates.

I am glad that you were not encouraging me to spoil our national image and buy something as this could have the rest of the community having a completely false notion.

Again my sincere thanks to everyone who assisted.

---

