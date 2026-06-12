---
title: "wireless/LAN problem"
date: 2006-01-24
forum: General Help
---

### Post by BruschiOnTap on 2006-01-24
Ok, I am having a weird problem with my wireless/LAN cards. I assume I have two separate cards since they are eth0 and eth1 respectively

In the last two weeks my wireless says it is on Network Connection: lo

I think this is loopback. Does this mean it's sending and receiving its own signal??? When I go to a hotspot it doesn't detect any other signals and never gets going. When I plug in to eth1, it also won't recognize any networks. 

I did sudo ifup eth0 and got some information:
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:12:3f:f9:0a:cc
Sending on LPF/eth0/00:12:3f:f9:0a:cc
Sending on Socket/fallback

Then it says no DHCPOFFERS received, which I guess means it doesn't sense a network?

This is driving me crazy becuase I am in a foreign country and having to pay for internet. Please help!

---

### Post by lorenco on 2006-01-24
What is the output of 'iwconfig' ?

So you know what hardware you have ?

---

### Post by BruschiOnTap on 2006-01-24
[QUOTE=stream303]Aha!  Looks like your setup is picking up an internal nameserver instead of your isp's nameserver(s).  I'm used to seeing this with some soho routers....

If you can obtain the real dns addresses of your isp, let's prevent your /etc/resolv.conf from being overwritten with an invalid nameserver and point it to the right ones.

You'll want to edit **/etc/dhcp3/dhclient.conf**    (sudo gedit /etc/dhcp3/dhclient.conf)

and just before the request line, add this:

**prepend domain-name-servers 123.45.678.90, 123.45.678.91;**
(use your isp's real dns addresses of course)
Just separate multiple addresses with commas, and don't forget the semicolon at the end.

Now instead of rebooting, you can bring the interface down and up again from the terminal:

sudo ifdown eth0
sudo ifup eth0

Let's see if this works for you.[/QUOTE]

Ok, I used this info  to figure out that my computer is also looking for the wrong nameserver.  It's a laptop, though, so I want to use wi-fi and be able to connect to any one of them... how do I configure for that???  Is my problem just too stoopid to merit a reply on here?

---

### Post by lorenco on 2006-01-26
[quote=BruschiOnTap]Ok, I used this info  to figure out that my computer is also looking for the wrong nameserver.  It's a laptop, though, so I want to use wi-fi and be able to connect to any one of them... how do I configure for that???  Is my problem just too stoopid to merit a reply on here?[/quote] 
Can you post the output of iwconfig ?  You need to supply some more info here otherwise I can not help...

Do you know what Hardware (Wireless Card) you Latop has ??:confused:

Common hardware for laptops:  Athereos, Intel Pro etc...

---

### Post by BruschiOnTap on 2006-02-19
wow, three weeks later I see someone replied!

My card is an Intel Pro Wireless that comes standard on the Dell Inspiron 600m.  I found another thread on here where a guy with the same wireless card got apt-get update and his support for it stopped altogether.  However, I don't have my computer handy to run whatever they were suggesting he do.  Do you think the same thing caused this to happen?

I've tried getting WiFi Radar and another similar program but neither responded or gave me any feedback.

I am not in a great state at hte moment, having to use pay-by-the-minute internet service in a cafe without my own computer...

---

### Post by lorenco on 2006-02-19
I have a laptop (IBM Thinkpad) with the same card.

It will etiher be ipw2100 or a ipw2200 module:  You can check this doing:

> lsmod | grep ipw 
This will show you what (if) your wirless module is configured.  Normally this module configures on my laptop to eth1, not eth0 as this is the onboard ethernet card.

You should ideally try and run ipwconfig as root as well this output will show if you have any wireless cards configured.

You may also load these modules using 
> sudo modprobe ipw2?00 and either use 1 or 2 for ?

Hope this point you in the right direction.

---

### Post by BruschiOnTap on 2006-02-22
thanks, Ill see what this does and report back ASAP!

---

### Post by BruschiOnTap on 2006-02-23
Ok, when I did the lsmod grep command it gave me some info

ipw2200           92680 0
firmware_class  9472 1 ipw2200
ieee 80211       27012 1 ipw2200
ieee 80211       5636 2 ipw2200

then when I put in the sudo modprobe ipw2200 command, it asked me for a password adn then apparently did something because it gave me another prompt.

I should probably note that I can activate and deactivate my wireless card as eth1 but it never finds a signal, even in places where it should.

---

### Post by lorenco on 2006-02-23
> Ok, when I did the lsmod grep command it gave me some info

ipw2200           92680 0
firmware_class  9472 1 ipw2200
ieee 80211       27012 1 ipw2200
ieee 80211       5636 2 ipw2200
This is good.  It shows that you have the ipw2200 module (driver) loaded.

>  then when I put in the sudo modprobe ipw2200 command, it asked me for a password adn then apparently did something because it gave me another prompt.

You would not need to do this as it was already loaded as shown above. (You can experiment by doing "sudo modprobe -r ipw2200" to remove the module and "sudo modprobe ipw2200" to load it again....
In between these commands you can run the lsmod ... grep command again to check whether the modules load ok.

>  I should probably note that I can activate and deactivate my wireless card as eth1 but it never finds a signal, even in places where it should.

Please specify how you "[de]activate"...

Can you paste the output of "sudo iwconfig  eth1"?  This will show your current wireless config.

Can you also paste the output of "sudo iwlist scan"? (While in the same location .... ?) This will show you all the wireless networks in range ... (There is possibility that this is a long output in areas where you have lots of AP's.

It is possible that you wireless network is "hidden" ?  You would need to know what kind of encrption the network use.  Do you have this info ?  We would need it to configure the network.:-D

---

### Post by BruschiOnTap on 2006-02-25
by 'deactivate' I mean in the GUI, opening the properties and configuration panels to activate or deactivate wireless/wired connections.  So yeah, the wireless activates apparently as it should, but can't find connections.

as for hidden connections and encryption, I've been trying to use the wireless in cafe hotspots, where it should just connect automatically as soon as it senses the network.  I thought it might be the network but other people have no trouble getting connected.

thanks for your help so far, I'll give you a copy of the printout for those commands you gave me ASAP.

---

### Post by BruschiOnTap on 2006-02-26
so, after the iwconfig eth1 I got a little printout saying, essentially, that my radio was turned off.  Everything else was also turned off and all the numeric values were set at 0.

after thinking for a while I had a moment of clarity and hit the laptop hotkey that turned the radio on and off when I ran windows on it and suddenly my computer was a hotbed of network activity.  Only  problem was that I couldnt actually connect to any of the signals it picked up.  It would obtain an IP address but the address was always 127,0,0,1.  So I went into the DNS tab and deleted that address listing  to see what it would do.  Nothing happened, still.  Finally, I turned off the computer and restarted it.  When I did this it gave me a message after putting in my password that read:

Could not look up internet address for mrs-robinson *thats my host name thingy*  It may be possible to correct the problem by adding mrs-robinson to the file /etc/hosts.

So I went into terminal and did sudo gedit /etc/hosts and it printed:

unable to look up mrs-robinson via gethostbyname

So basically, a bunch of commands dont work in my terminal now and its clear that I did something major and now I cant fix it.  On the plus side, we worked out the main problem with my wireless... is my new problem fixable or am I going to need to do something drastic to my computer?

---

### Post by huckem on 2006-02-26
You may be on the right track now.  When there are network connections available to you, you can view them by going into the networking gui from the admin. menu, deactivate your eth1 and eth0.  Then you can go into configure for both of them respectively and choose a network name from the dropdown menu.  Set up WEP keys if you need to, if not just leave it blank.  I use DHCP to get my IP's and all that, so try that first.  Now, do the exact same setup on BOTH the eth0 and eth1, and then activate them both.  This worked for me.  Let me know if this helps, or if I totally missed the point.  good luck.

---

### Post by BruschiOnTap on 2006-02-27
ok, but my problem now is that it wont recognize my computers  "name" (mrs-robinson) 

when I put "sudo" for a command it replies with the following print-out

"unable to look up mrs-robinson via gethostbyname"

so what did I do to **** it up and  how do I fix it???

also, when I log in to a session it gives me this dialogue

"Could not look up internet address for mrs-robinson.  It may be possible to correct the problem by adding mrs-robinson to the file /etc/hosts."

How do I sudo gedit that file when I cant type "sudo gedit" into my terminal???

*ready to stab myself with a blunt keyboard-shaped object*

---

### Post by lorenco on 2006-02-27
Hi,

If I remove my fully qualified machine name from /etc/hosts I also get: 
> sudo: unable to lookup xyz.abc.net via gethostbyname()
Password: But I still get the prompt... to enter passwd.

You can try to edit this file and add you fully qualified domain name of your PC
Hosts file as follows:
> 127.0.0.1 localhost.localdomain localhost xyz xyz.abc.net 
In your case add: 
> 127.0.0.1 localhost.localdomain localhost **mrs-robinson**

---

