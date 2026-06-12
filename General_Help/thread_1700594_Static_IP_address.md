---
title: "Static IP address"
date: 2011-03-05
forum: General Help
---

### Post by Wuxin on 2011-03-05
I'm having trouble printing wireless from my Ubuntu laptop.  For some reason, the list of my attempted print jobs (which haven't gone through to the printer) are logged on the finder on my Apple desktop!  Someone told me that it could be a problem of not having a "static IP address."  What is this and would this solve my problem? Thanks in advance!

---

### Post by turtle153 on 2011-03-05
To get a static IP, right click the Network Manager icon and Edit Connections... Edit the connection you use and under IPv4 settings use Method: Manual.

Note that this probably won't fix it alone, there's a chance that the Apple computer also has the same IP, so you'll need to go to the router settings and assign new ones.

---

### Post by coffeecat on 2011-03-05
A static IP address for the printer will probably help. I assigned a static IP address to my networked HP printer to make it easier to use. But where in the network does yours appear? Is it a standalone networked printer with its own network interface (ethernet or wireless) attached to your router, or is it attached to either the Mac or your Ubuntu machine with a USB cable?

turtle153's instructions will indeed assign a static IP address to your Ubuntu machine but I guess it's the printer we need to look at.

If it's a network printer, you can assign a static IP address either in the printer configuration or in your router.

Post back more details of your setup and someone will be able to help.

---

### Post by Wuxin on 2011-03-05
Okay.  I have an IBM ThinkPad T43 which I use with Ubuntu.  I have a Brother HL 2170w printer which I have set up on a wireless basis--no USB connections.  My desktop is a Mac-mini which is connected to my router, a 2Wire.  So the deal is, I want both my laptop and the desktop to function wireless with the printer.  After examining my router info, it appears that all devices do have a static IP so there must be something more going on.  Hope this additional info provides sufficient detail.  Thanks!

---

### Post by coffeecat on 2011-03-05
> **Wuxin said:**
> After examining my router info, it appears that all devices do have a static IP so there must be something more going on.

I have to ask: are you sure? Usually you have to reserve and assign a specific IP address to a specific MAC in the router for it to be truly static. If you are simply in the habit of switching on your devices in the same order, then they will tend to get the same IP addresses each time, but this is not guaranteed and is not true static IP addressing.

Try assigning a different static IP address for the printer, deleting the printer entry from Ubuntu's Administration > Printing utility and then adding the printer back in Printing but with the new IP address. See if that sticks.

With my setup, my router assigns dynamic addresses from 192.168.1.2 upwards in the order in which devices handshake with the router. So I have set my network printer to have a static address 192.168.1.100 in the printer configuration, being a number much larger than would be assigned through DHCP. So, instead of the printer relying on DHCP and saying to the router, "can I have an IP address please?", it's saying, "Hi there. My address is 192.168.1.100. That OK?" And the router is replying, "Oh. All right then."

I find that works just fine.

---

### Post by Wuxin on 2011-03-05
Okay, thank you for the very complete and accessible answer.  Now I have to ask, how do you go about changing these IP addresses?  Where do you set these parameters so that they are understood by all the devices involved?

---

### Post by coffeecat on 2011-03-05
> **Wuxin said:**
> Now I have to ask, how do you go about changing these IP addresses?

For the printer, there are two ways of doing it.

The first way is in the router, if the router supports this. Log in to the router web configuration interface and see if you can find a list of all the attached hosts. For Linksys routers it's under Status > Local Network. Make a note of the MAC address for the printer. At this point though I can't see how to assign a static address within the Linksys interface. I thought you could. You certainly can with Netgear routers, so what router are you using?

The other way is with the printer configuration. I have no experience of Brother printers so you should look in the printer manual. But this is how I did it with my HP printer. Whether or not you can do it with a Brother machine, I don't know, but you could give it a try.

Because the HP documentation was so poor, I attached it (via ethernet) to my router, went into the router web configuration to get its internal IP address as above. Let's say it was 192.168.1.5. Then I put '192.168.1.5' in the firefox address bar in Ubuntu and I was in my printer web configuration utility. Thereon it was straightforward to set my chosen static address of 192.168.1.100 in the printer configuration and since then, whichever router I use, it has that address.

By the way, when you assign an address, make sure it's in the right range. Some routers use 192.168.1.x, others 192.168.0.x and others use a range somewhere in 10.0.x.y.

---

### Post by Wuxin on 2011-03-05
I am using a 2Wire router, a standard one used by AT&T for DSL connections.  I do see the list of designated IP addresses in the router, all of which have the 192.168.1 format.  I can see the one designated for my laptop, I believe I know the one for the printer, but I'm not sure which is the Mac IP.  So basically is it the laptop and printer IP's I want to change?  Or is it just the printer IP which needs to be changed?  I hate to get in there and mess with making manual changes that could possibly make things even worse!  But the laptop is definitely identified in the router by name.  And the printer, if indeed it is the printer, is identified by a number beginning with BRW which leads me to think it's the Brother.

---

### Post by coffeecat on 2011-03-05
The MAC address...

[http://en.wikipedia.org/wiki/MAC_address](http://en.wikipedia.org/wiki/MAC_address)

... is in the form 01:23:45:67:89:ab. You need to assign a static address for the printer. There's no harm in assigning a static IP address for your Ubuntu machine, but there's no real point that I can see.

In some routers (clearly not all from my Linksys experience) you can assign a static IP address for an attached device by means of the MAC address - in this case the MAC address of the Printer's network interface. Where you've found the assigned IP address for the printer in the router interface, you'll see the MAC address as well - if the router is any good.

If you can't find how to do it in your router - check the router manual - then it might be quicker setting the IP address in the printer's configuration. But exactly how you do that you'll have to find in your printer documentation.

---

### Post by Wuxin on 2011-03-05
I'll give that a shot.  As far as getting information from the printer manual--forget it!  I called the customer-no-service 800 number for Brother and, while they said Linux is compatible with Brother printers, they don't *offer support* for Linux!  In other words, you're on your own trying to get it to work.  This forum is far more instructive and helpful for anything pertaining to Ubuntu!

---

### Post by coffeecat on 2011-03-05
Your mistake was to mention Linux. Just say you want to set up a static IP address in the printer. Don't mention your OS; it's irrelevant. If they say you need to use a web browser in the way I did (check my earlier post again - it might work for a Brother printer), just tell them that you're using Windows and Internet Explorer. :wink: They won't know. Or even MacOS and Safari, which you could do anyway. Configuring something through a web interface you can use whatever OS and whatever browser you want. Just don't give customer (un)support any excuse to fob you off. :)

---

### Post by Wuxin on 2011-03-05
Good advice.  I don't recall what the context was  that I happened to mention Linux, but it was in response to something the customer-no-service agent asked me.  But I will remember this if I have to call again.  If I do set a static IP for the printer, will this in any way effect the interface between my Mac and the printer?  For some reason the Mac desktop always manages to find its way to the printer wireless even without the static IP address.  How is that?

---

### Post by Wuxin on 2011-03-05
Quick note here: I managed to get into my printer's configuration and indeed the IP boot menthod is "auto."  There is an option to change the boot method to "static."  Would it be sufficient just to change the boot method to "static" leaving the existing IP address in place, or is it better to actually change the IP address?  My concern here is that the wireless connection works for both the Mac desktop and the Ubuntu laptop.  Thanks!

---

### Post by JKyleOKC on 2011-03-05
By any chance is the printer switched on before the Mac laptop is powered up? Sometimes, the sequence in which devices are powered up has a great effect on whether other devices are able to connect to them. This isn't widely known, and its effects can be maddeningly intermittent when trying to troubleshoot.

Before you change any settings, try this: power all three down normally, then power the printer up first, followed by the other two computers after a minute or so for the printer to finish booting. If both computers are then able to contact the printer, you'll know that it's a sequence-sensitive situation!

From there, you can either leave things as-is and always power the printer up first, or change the settings as discussed in earlier threads.

Hope this helps!

---

### Post by coffeecat on 2011-03-06
> **Wuxin said:**
> But I will remember this if I have to call again.  If I do set a static IP for the printer, will this in any way effect the interface between my Mac and the printer?  For some reason the Mac desktop always manages to find its way to the printer wireless even without the static IP address.  How is that?

In my experience a Mac does seem to be more tolerant of a dynamic Printer IP address than Ubuntu. Anyway, my Mac Mini is happy with my HP printer set to a static address. It's happy, Ubuntu is happy - and I'm happy. :)

> **Wuxin said:**
> Quick note here: I managed to get into my printer's configuration and indeed the IP boot menthod is "auto."  There is an option to change the boot method to "static."  Would it be sufficient just to change the boot method to "static" leaving the existing IP address in place, or is it better to actually change the IP address?

You need to change  the IP address. If you leave it as it is, the address will be in the range the router allocates dynamically. Next time you switch everything on, the router may allocate that address to either the Mac or your Ubuntu machine and you'll have an address clash. Check your router interface again and see if there is a range of DHCP allocated addresses. In my Linksys, for example, I've set the starting IP address for DHCP clients as 192.168.1.2, and left the default of about a maximum 50 DHCP clients, which means that the highest DHCP allocated address will be 192.168.1.51. And that means that the static IP address of 192.168.1.100 I've chosen for my printer is safe.

Different routers have different ways of showing the addresses used for DHCP allocated addresses. With Netgears you simply define the start and end address for DHCP, but it should be clear. If you need any help, just post what you find in the router interface and we can take it from there. Screenshots would be useful. I've set up several different makes of router for myself and friends but I don't believe I'm familiar with whatever interface 2Wire uses.

---

### Post by Wuxin on 2011-03-06
With regard to the power up sequence, I usually leave everything in sleep mode.  I only 
occasionally power things off completely in order to clean things up.  My desktop is  in sleep mode most of the time, as is my printer.  My laptop is the only device I power off when not in  use.  I have been unsuccessful in locating the DHCP sequence in my router's summary page.  It *appears* that the sequence is 192.168.1.01, etc., but I'm not certain.  I'm basing that on the existing allocated numbers for devices.  Where might I look for this information?

---

### Post by coffeecat on 2011-03-06
> **Wuxin said:**
> 192.168.1.01

192.168.1.1 is probably the address the router assigns itself on its LAN interface. So that would be your LAN gateway address. Some then assign addresses from 192.168.1.2, some from higher up the sequence, but this is usually alterable. Post some screenshots of the interface as I suggested and we can take it from there. The design and layout of each manufacturer's interface varies so much, even though they do the same job, that's it's difficult to say where exactly is what you want. Look for "LAN administration" or "LAN setup" or something like that.

---

### Post by Wuxin on 2011-03-06
Ah!  Found it!  The DHCP range is 192.168.1.64-192.168.1.253.  Interesting that it uses these somewhat odd numbers.

---

### Post by coffeecat on 2011-03-06
> **Wuxin said:**
> Ah!  Found it!  The DHCP range is 192.168.1.64-192.168.1.253.  Interesting that it uses these somewhat odd numbers.

Not that unusual, although I don't understand the rationale of the different ranges different manufacturers use. The default range for a Linksys router (although I changed this for my own reasons) starts at 192.168.1.64 as well.

Anyway, now you know that the addresses between 192.168.1.2 and 192.168.1.63 won't be assigned by DHCP, so you are safe to use anything in that range  for static addresses

---

### Post by Wuxin on 2011-03-06
Do I have to change the DHCP range in order to use those numbers?  The router says, "If you change the IP address range, you must renew the DHCP lease on all devices on the network." That sounds like it could be something of a pain.

---

### Post by coffeecat on 2011-03-06
> **Wuxin said:**
> Do I have to change the DHCP range in order to use those numbers?  The router says, "If you change the IP address range, you must renew the DHCP lease on all devices on the network." That sounds like it could be something of a pain.

No. Leave that range as it is. It gives you plenty of numbers both dynamically assigned addresses and 62 potential static addresses. What you have to do is to set a static address between 192.168.1.2 and 192.168.1.63 in the printer itself. My apologies for suggesting you could set a static address in the router itself. I've been doing a bit of research and it seems that you can only do this in some makes of router. These are my results:

Linksys - No
Netgear - Yes, very easily.
Zoom - Yes
Edimax - No
D-Link - Yes, in theory but it doesn't work :rolleyes:

I don't know about your make. If you post the exact model I'll see if I can find the user manual on the internet and have a look but you might find it easier to concentrate your energies on the printer.

---

### Post by Wuxin on 2011-03-06
Here it is...the model of the router is                            2701HG-B Gateway.  Thanks so much for your help with this!

---

### Post by coffeecat on 2011-03-06
> **Wuxin said:**
> Here it is...the model of the router is                            2701HG-B Gateway.  Thanks so much for your help with this!

This seems to be where you can download the pdf manual:

[http://www.fixya.com/support/t1811928-pdf_file_or_manual_2_wire_gateway](http://www.fixya.com/support/t1811928-pdf_file_or_manual_2_wire_gateway)

Looking at page 69 (p74 in Evince) it seems that the router allocates itself the address 192.168.1.254 (not 192.168.1.1 as I thought which is more common), and has a DHCP range of between 64 and 253 as you say. Look at page 78 (83 in Evince). I think that is where you can assign a static address. They don't actually call it a static address there - it's called DHCP address allocation which comes to the same thing. If it works the way I think it works, once you've identified the printer, you can allocate an address and the router will always give it that address and not assign that address to anything else.

---

### Post by Wuxin on 2011-03-06
Okay, thanks so much for this.  So that means the static IP number should be between 1 and 63, is that correct?  Is there an advantage to doing this through the router because it seems to me that the process for assigning the address through the printer page is a bit more straightforward.  

I should also point out that in the  "Finder" file, which is where all hardware devices are stored on Apple, it shows under the printer "connection failed."  I'm not sure what this means because the connection works with my Mac, just not with Ubuntu.  But here is an indication that something isn't right, or at least isn't recognized by the router.

---

### Post by coffeecat on 2011-03-06
> **Wuxin said:**
> Okay, thanks so much for this.  So that means the static IP number should be between 1 and 63, is that correct?  Is there an advantage to doing this through the router because it seems to me that the process for assigning the address through the printer page is a bit more straightforward.  

You have a choice. The advantage of using the router is that it keeps tabs on all IP addresses and won't assign the same address to two devices. You simply have to be careful if you assign an address in the printer. For you, the way your router is set up, a static address needs to be in the range 1 and 63. However, if that page in the router I pointed you to allows you to reserve an address in the DHCP range then the router will reserve that for the printer only so long as it is working properly. 

> **Wuxin said:**
>  I should also point out that in the  "Finder" file, which is where all hardware devices are stored on Apple, it shows under the printer "connection failed."  I'm not sure what this means because the connection works with my Mac, just not with Ubuntu.  But here is an indication that something isn't right, or at least isn't recognized by the router.

Tbh, I'm not sure what's going on in the Mac. Perhaps the best thing would be to assign the printer IP address however you decide to do it and then switch off everything, and then reboot everything starting with  the router. Then I would reinstall the printer in Ubuntu to take account of the new static address and then have another look at the Mac.

---

### Post by Wuxin on 2011-03-06
Hmm.  I went into the router and the DHCP has a drop down menu with the designated range of 192.168.1.64, etc.  It doesn't seem that there is an option to assign a number outside that range.  Maybe you can delete the number in DHCP window and assign one in its place, but I think the router wants you to stay within its range.  Is there a way around using the drop down menu?

---

### Post by coffeecat on 2011-03-07
> **Wuxin said:**
> Hmm.  I went into the router and the DHCP has a drop down menu with the designated range of 192.168.1.64, etc.  It doesn't seem that there is an option to assign a number outside that range.  Maybe you can delete the number in DHCP window and assign one in its place, but I think the router wants you to stay within its range.  Is there a way around using the drop down menu?

I don't know. As I said before, I don't have on-hands experience of your particular make of router. But the answer is in what I said before. Either:

Use that drop-down to assign a fixed IP address to the printer within the DHCP range. If the router is doing its job properly then it won't assign that address to anything else.

Or...

Use the printer configuration to assign a fixed address, but this time it would need to be outside the DHCP range. I.e., choose an address in the 1-63 range. Personally, if I was using the printer configuration to set the address, I'd go for 192.168.1.50 - easily memorable.

---

### Post by Wuxin on 2011-03-07
[FONT=Times New Roman][SIZE=3]Thanks so much!  I believe the issue is finally resolved.  It seems to be working now.  I affixed a number within the range allocated by the router.  For the time being it seems to be working.  If there is a future problem, I'll know where to go!  Thanks so much for your patience, knowledge, and goodwill!  

Is there a way to mark this issue as SOLVED?  Thanks again!
[/SIZE][/FONT]

---

### Post by coffeecat on 2011-03-08
I'm glad it's solved. If you want to mark the thread as solved, click on the 'Thread Tools' drop-down at the top right of the thread.

I've certainly learnt something from this. Hitherto I've always set fixed IP addresses from within the device concerned. (I've also done this with a network storage device.) I've only been aware that you should be able to  assign fixed IP addresses from the router without ever needing to do it myself. Now I've discovered that depending on the make of router, you can assign a fixed IP address outside the reserved DHCP range, or only within the reserved DHCP range, or not at all. Which is useful to know.

Good luck with your network! You'll be wanting to get a fileserver next, accessible from both your Ubuntu machine and your Mac Mini. :wink:

---

### Post by Wuxin on 2011-03-13
[FONT=Times New Roman][SIZE=4]Thanks again for all your help.  I'm glad that you too learned something of value from this exchange.  Please tell me what a "fileserver" is and why it would be of value to me?

Thanks!
[/SIZE][/FONT]

---

### Post by coffeecat on 2011-03-13
I used the term fileserver loosely:

[http://en.wikipedia.org/wiki/Fileserver](http://en.wikipedia.org/wiki/Fileserver)

Strictly speaking in the home environment, I should have said NAS, or network attached storage device:

[http://en.wikipedia.org/wiki/Network-attached_storage](http://en.wikipedia.org/wiki/Network-attached_storage)

I use one of these:

[http://www.wdc.com/en/products/products.aspx?id=300](http://www.wdc.com/en/products/products.aspx?id=300)

It's basically a 1TB drive in a housing which has a low-power processor and (probably) Linux based firmware for doing the networking tasks. There is a web-based configuration interface which is one reason why this also has a fixed IP address. In a situation where you have more than one machine it's useful as a central access  point for data. It can also serve streams so that my Sony PS3, which I only use as a media centre, can stream music and videos from it.

I tend to keep my personal data on the local machines and sync with the NAS every so often so that the NAS is really being used as an archive/backup. Transfer speeds using smb are sufficient  for streaming videos, but slow - about 2 MB/s - for archiving.

---

