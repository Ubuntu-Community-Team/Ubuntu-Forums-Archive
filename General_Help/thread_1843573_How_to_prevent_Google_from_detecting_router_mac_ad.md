---
title: "How to prevent Google from detecting router mac address"
date: 2011-09-13
forum: General Help
---

### Post by Ralph L on 2011-09-13
I have been reading about how google collects the location of routers by driving around neighborhoods and recording wifi router mac addresses and the house addresses of nearby houses.  Apparently mac addresses are not protected even if the wifi is encrypted.  Also, if one has an Android phone with gps, the mac address of any wifi router detected by the phone along with the current gps location is sent to Google, who puts it in a data base.

Does anybody know of a router I can purchase that protects its mac addresses--maybe by encrypting them or making them random and constantly changing.  (Yes, this violates the basic concept of a mac address, but it seems possible.)

Thanks
Ralph

---

### Post by haqking on 2011-09-13
> **Ralph L said:**
> I have been reading about how google collects the location of routers by driving around neighborhoods and recording wifi router mac addresses and the house addresses of nearby houses.  Apparently mac addresses are not protected even if the wifi is encrypted.  Also, if one has an Android phone with gps, the mac address of any wifi router detected by the phone along with the current gps location is sent to Google, who puts it in a data base.

Does anybody know of a router I can purchase that protects its mac addresses--maybe by encrypting them or making them random and constantly changing.  (Yes, this violates the basic concept of a mac address, but it seems possible.)

Thanks
Ralph


You can turn your router off and thats about it ;-)

Edit: here is an article i had in my bookmarks from last year [http://www.freerepublic.com/focus/f-news/2500738/posts](http://www.freerepublic.com/focus/f-news/2500738/posts)

If your Mac was encrypted or constantly changing traffic woudl never  find its way back to your router, also your ISP would dropits  connection, thats why when people change there routers sometimes they  need to use MAC cloning to show an old one to maintain the connection  until ISP sorts it out. [http://www.whatismyip.com/faq/what-is-mac-cloning.asp](http://www.whatismyip.com/faq/what-is-mac-cloning.asp)

---

### Post by haqking on 2011-09-13
Edit, Double post

---

### Post by Old_Grey_Wolf on 2011-09-13
I see that haqking already answered this.

---

### Post by milkkart on 2011-09-13
think he means having the MAC of the wireless network card changing constantly rather than the MAC of the WAN interface, since there would be no way for the streetview car to see the WAN one without actually breaking into the router. marginally more plausible, possibly if you're router supports DD-WRT firmware that could do it. then just change MAC address once a week or so.

---

### Post by SoFl W on 2011-09-13
Jeeez, you make Google sound so....what is the word I am looking for? You make Google look so "EVIL".  Just because they track your every move on the internet, go through all your gmail, google docs, google voice, all your cell phone info, you location at all times, and want to know more information about you doesn't make them evil.  Let them have all your info.  Remember, privacy smivency, you should have nothing to hide.  Why worry?

---

### Post by Habitual on 2011-09-13
let me count the conspiracies (yawn)....
nsa key in window registry.
PGP is backdoored.
RSA is backdoored.
Bill Gates can read your hard drive (when you/I/we used Windows)
Carnivore program.
Sony's DRM rootkit (ok, this was legit)

> **sofl w said:**
> ...privacy smivency, you should have nothing to hide.  Why worry?

+1.

---

### Post by Old_Grey_Wolf on 2011-09-13
> **milkkart said:**
> think he means having the MAC of the wireless network card changing constantly rather than the MAC of the WAN interface, since there would be no way for the streetview car to see the WAN one without actually breaking into the router. marginally more plausible, possibly if you're router supports DD-WRT firmware that could do it. then just change MAC address once a week or so.

After re-reading the post, I think that is what is actually being asked. 

I can change the WLAN MAC address all I want; however, if I type in "/usr/sbin/arp -a" in a terminal on a computer connected wirelessly to the router, the router's wireless broadcast MAC address doesn't change. I doubt that most consumer routers would make it very easy to change the router's broadcast MAC address.

---

### Post by Old_Grey_Wolf on 2011-09-13
I have been using the Internet from the days of ARPANET. I know that if you put something on the Internet it is no longer guaranteed to be private. I also know that if you broadcast it on radio frequencies, it is no longer guaranteed to be private. That includes your cell phone. 

Am I paranoid? No, I don't think so. 

I know that if I put anything into the public domain or airspace it is fair game. Therefore, I don't put anything into the public domain or airspace I wouldn't want the general public to know. I actually talk to people face-to-face.

---

### Post by Old_Grey_Wolf on 2011-09-13
Should this thread still be in the General Help Forum or moved elsewhere?

Or, can it get back to answering the OP's post?

If someone does have a suggestion, I would be interested in what it is. I try to be aware of things I can use to increase my security on the Internet or over public airspace.

---

### Post by Dangertux on 2011-09-13
This doesn't happen anymore but yes... It used to happen.

See Samy Kamkar's Black Hat Presentation "How I Met Your Girlfriend"

Shortly after that they stopped collecting that information (so they say). However, it is definitely secured better now.

---

### Post by |{urse on 2011-09-13
Use tor. Then it wont matter if they know your real mac or not as you will be behind someone else's router with a different mac address online.   Delete your facebook account (for starters) if you really care about people knowing who you are online.

---

### Post by Dangertux on 2011-09-13
For what they are talking about Tor won't help. Tor can't obfuscate the signal from your wireless access point. 

To OP : If you're really concerned about this you need to make sure your router isn't vulnerable to NAT pinning. Since that is the other piece of the puzzle that allows geolocation, and the only piece of it you can actually control.

In this case I would recommend a browser addon that striclty enforces same origin policies like NoScript.

---

### Post by |{urse on 2011-09-13
My point is that no matter whether "they" know what your mac address is or not, there will likely be no surveillance of your wireless access point unless your ip/mac has been logged during suspicious activity, which tor masks anyways so there are no worries.. you can tattoo your mac address on your forehead now.

Maybe we are talking about different "they"s.

---

### Post by SoFl W on 2011-09-14
> **Habitual said:**
> 
+1.
I hope you know I was being sarcastic and think anybody who thinks that way is a fool.

---

### Post by SeijiSensei on 2011-09-14
> **Old_Gray_Wolf said:**
> I doubt that most consumer routers would make it very easy to change the router's broadcast MAC address.

Actually many of them do.  My Netgear allows me to specify a custom MAC address; it's right on the first page of settings. I think the Linksys I have also does.  

At one time, I believe, some ISPs registered the MAC addresses of their customers during installation and only allowed further connections from that address.  If you replaced the router, you either had to re-register with the ISP or spoof the old MAC address.  I don't think this is a very common practice any more; consumers change routers too often to make this practicable.

---

### Post by haqking on 2011-09-14
> **SeijiSensei said:**
> Actually many of them do.  My Netgear allows me to specify a custom MAC address; it's right on the first page of settings. I think the Linksys I have also does.  

At one time, I believe, some ISPs registered the MAC addresses of their customers during installation and only allowed further connections from that address.  If you replaced the router, you either had to re-register with the ISP or spoof the old MAC address.  I don't think this is a very common practice any more; consumers change routers too often to make this practicable.


your router may with a DD-WRT firmware

you can check if it does here [http://www.dd-wrt.com/site/support/router-database](http://www.dd-wrt.com/site/support/router-database)

Warning: Changing or cloning your MAC may cause issues with connectivity with your ISP though

[DD_WRT FAQ]("http://www.dd-wrt.com/wiki/index.php/Index:FAQ")

[]("http://www.dd-wrt.com/wiki/index.php/Index:FAQ")

---

### Post by zero2xiii on 2011-09-14
I also don't see why there is a problem?

But if you are "security aware" (the term some people use to try and cover up their illegal activity, OR the paranoia), the answer is easy

[SIZE="4"]**_RUN CABLE! DON'T USE WIRELESS_**[/SIZE]

Ah, now I feel better. :)


No wireless activity is private, the military even knew that in the days of world war one and two. Thus the encryption. But triangilation has come a far way. The HAMs around here can pinpoint pirates in under 5 minutes worth of radio transmission. Fact of the matter, big brother is reality, beter learn to not have anything to hide... Or, dig a hole, and live in it :lolflag:

Cherz, and good luck.

PS:: Standard wifi is on 2.4 (B/G/N) try going to 5.8 (A). there is FAR LESS trafic and snoopers up there. Or if you can, go down to 900MHz, even less snoopers down there than up on 5.8...

---

### Post by SeijiSensei on 2011-09-14
> **haqking said:**
> your router may with a DD-WRT firmware

I don't know if you're talking to me when you say "your router," but my router is running the standard firmware from Netgear, not DD-WRT or Tomato.

---

### Post by haqking on 2011-09-14
> **SeijiSensei said:**
> I don't know if you're talking to me when you say "your router," but my router is running the standard firmware from Netgear, not DD-WRT or Tomato.


No sorry, i meant it for others if their router didnt support it.  With DD-WRT if your router supports the firmware change they may be able to get the feature is what i meant ;-)

cheers

---

### Post by Dreamer Fithp Apprentice on 2011-09-14
> **zero2xiii said:**
> I also don't see why there is a problem?

But if you are "security aware" (the term some people use to try and cover up their illegal activity, OR the paranoia

Read some history, dude.
Also read The Gulag Archipelago and 1984.
Prevailing attitudes like this --> police states.
What Sinclaire Lewis meant by "It Can't Happen Here" is, of course, that it CAN.

---

### Post by |{urse on 2011-09-14
I find that paranoia is the best policy only when you actually have something to hide. Do I care whether an adbrite cookie knows what sites I frequent? No. Do I care if someone is remoted into my box and installed a rootkit that keylogs, camlogs or even is using my ip to purchase illegal things? Yes. So use linux, use tor, learn how to set up iptables. If you're "paranoid" like me, set up a hardware firewall out of some crappy old computer running IPcop. Use less common wireless channels, keep a good salted password and don't broadcast your essid. Doesn't really sound that paranoid after all, does it?

So far as  DD-WRT or tomato firmware, I've never used it.. sounds like this might fit the bill to change my mac address occasionally as  my router doesnt provide this functionality. I'll have to check that out ^^

---

### Post by SparTacux on 2011-09-14
> **Ralph L said:**
> I have been reading about how google collects the location of routers by driving around neighborhoods and recording wifi router mac addresses and the house addresses of nearby houses.  Apparently mac addresses are not protected even if the wifi is encrypted.  Also, if one has an Android phone with gps, the mac address of any wifi router detected by the phone along with the current gps location is sent to Google, who puts it in a data base.

Does anybody know of a router I can purchase that protects its mac addresses--maybe by encrypting them or making them random and constantly changing.  (Yes, this violates the basic concept of a mac address, but it seems possible.)

Thanks
Ralph

I think there are two MAC addresses associated with modem routers. 

One is the WAN or internet facing  MAC and the other is your LAN side MAC. I did a ping from my router   over a wireless connection to a laptop and the MAC address recorded on the laptop was the router LAN side MAC.

You can change the WAN side MAC address in my router by backing up the router settings to a .CFG configuration file. Open the router configuration file using gedit and do a search for MAC. There's a line that says USE THIS MAC address = . Put the new MAC here and save the file. Reload into router by using a restore router command. 

I'm not sure how to change the LAN MAC but I guess it could be done in the same way or maybe Telnet into the router and have a look around the Linux file system of the router.

There's a possibility that different router manufacturers  have a range of MACS allocated to them and can be identified by particular model just by MAC address.  Don't quote me on that ;-). Some routers have known vulnerabilities which can be exploited by firing malformed packets on certain ports. If this is true then changing the WAN MAC address might be a good idea ?

---

### Post by haqking on 2011-09-14
> **SparTacux said:**
> I think there are two MAC addresses associated with modem routers. 

One is the WAN or internet facing  MAC and the other is your LAN side MAC. I did a ping from my router   over a wireless connection to a laptop and the MAC address recorded on the laptop was the router LAN side MAC.

You can change the WAN side MAC address in my router by backing up the router settings to a .CFG configuration file. Open the router configuration file using gedit and do a search for MAC. There's a line that says USE THIS MAC address = . Put the new MAC here and save the file. Reload into router by using a restore router command. 

I'm not sure how to change the LAN MAC but I guess it could be done in the same way or maybe Telnet into the router and have a look around the Linux file system of the router.

There's a possibility that different router manufacturers  have a range of MACS allocated to them and can be identified by particular model just by MAC address.  Don't quote me on that ;-). Some routers have known vulnerabilities which can be exploited by firing malformed packets on certain ports. If this is true then changing the WAN MAC address might be a good idea ?


MAC addresses are hardcoded into the NIC itself, changing through software or spoofing is a little different.

Though it can be done and often useful (when changing ISP etc)  it can often cause headaches with the ISP and traffic coming to a MAC they expect.

Lan side MACs are same, machine MAC can be changed at command line with right tools.

---

