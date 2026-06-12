---
title: "Howto home VoIP/POTS/SIP/ATA solution?"
date: 2010-05-25
forum: General Help
---

### Post by Metallinut on 2010-05-25
I'm looking for advice and/or suggestions.

Here's what I have now.
[LIST]
[*]I have an Ubuntu PC I'd like to use as a SIP server.
[*]I have a POTS setup at home, but recently ended my home phone service, my wife and I now only using cell phones.
[*]I have a Google Voice number.
[*]I have a Gizmo5 number.
[/LIST]
Here is what I would like to do:
Have my Google Voice number forward to both my cell, and my Gizmo5 number. If I'm at home, the Gizmo5 number gets handled by the SIP server running on Ubuntu. Using an ATA, my home phone lines ring, and I can answer the call.

To get even fancier, I would also like to have a similar setup for my wife. I assume a SIP server could handle two incoming numbers? I have cordless phones that support different ringtones. It'd be totally boss if I could have a different ring depending on who's number was called.

I may someday like to be able to place outgoing calls using the POTS phones, but for now, just receiving free calls through Gizmo5 would be great, and presents the least amount of money to get going. I think all I would need to buy is an ATA to convert from the Ubuntu box to the POTS. Then it should just be a matter of configuring the SIP server?

So. Has anyone done anything like this? Can you suggest ways to accomplish this? If you've done something like this, what are you using for an ATA? Any suggestions?

Come to think of it, do I even need a SIP server? Could I get an ATA, and plug in my Gizmo5 proxy info? Would I gain access to more features/control using a SIP server?

Thanks,

---

### Post by dino99 on 2010-05-25
some info via synaptic: search about sip voip dadhi-tools

---

### Post by Metallinut on 2010-05-25
OK. After doing some more research, I think I now know 0.001% more than before. But here we go. It looks like to connect my POTS to an IP system, I would need either an ATA, like a PAP2, or possibly something like [this]("http://www.atlasphones.com/ditdanpcical.html"). If I did get the PCI card, would I need an FXO or FXS module, or both? From what I've seen, I *think* I only need an FXS, as I'm not connecting back into a PSTN outside the house (all data will be through broadband).

I'm also looking at Asterisk (reading the OReilly book now). If I've got an Ubuntu machine running Asterisk, do I only need an FXS card? Or do I need an ATA as well?

I'm so freaking lost on this, but really looking forward to getting something like this to work.

---

### Post by buu700 on 2010-09-12
Any progress? I'm really interested in this too.

---

### Post by Ceyx on 2010-11-20
Hello,

If you guys are still interested, I can tell you what I have done using the Linksys SPA2102 - works great.  Gave up my land line.  I have two lines into my house and can dial anywhere in the world.  Very inexpensive, reliable and flexible way to go.  Anyhow, if you have any questions, fly them on by....

Regards

PS - you do not need Asterisk, or any other software either !

---

### Post by linuxtechie on 2010-12-03
> **Ceyx said:**
> Hello,

If you guys are still interested, I can tell you what I have done using the Linksys SPA2102 - works great.  Gave up my land line.  I have two lines into my house and can dial anywhere in the world.  Very inexpensive, reliable and flexible way to go.  Anyhow, if you have any questions, fly them on by....

Regards

PS - you do not need Asterisk, or any other software either !

Well you managed to build up the interest. How about going ahead and sharing with us?

+LT

---

### Post by Ceyx on 2010-12-15
Hope this is of some insight.  I'll try to keep it very simple so one can get an idea of what is involved.

Got a usb phone as gift, so of course I had to hook it up to one of my Linux boxes.  Ended up using Twinkle - an excellent little program.  Got myself a phone number from a Voip Provider in Winnipeg, Canada. ( Les.net ) Total expense so far ?  Under 10 bucks.  

With this setup I could receive and send regular phone ( landline ) calls anywhere in the world for next to nothing...actually pennies.

I found however, that with my computer being up and down all the time with my tweaking and upgrades and what not, that the phone service was not reliable - due to me and no one else.

Next, did some research on what is known as an ATA - analog telephone adapter.  In sum, it connects your existing vanilla, or not so vanilla, phones to the internet. ( you don't need a computer for this ATA setup but broadband IS required ).

Found myself with an SPA 2102 from Linksys/Cisco (sixty bucks).  Plugged  it into my router, attached my garage sale bought telephone ( so retro ! ) The 2102 is accessed thru a web interface that you can configure to connect to your service provider - in my case les.net. You can turn off or on web access thru the keypad of the phone, for security.  No hackers allowed.  It is inaccessable thru SSH etc as far as I know.

Les.net has some excellent single page instructions on how to set up your Linksys ATA  (and others) - 5 or six fields to fill in and you are on the air ..

So other than using the web browser on my computer I have not been into my ATA since I set it up about 6 months ago. I no longer have a traditional land line.  I spend under 8 bucks a month for this setup. My phones have never been down.

Things to ponder : * do NOT get an ATA that has fallen off the back of a truck. Telephone fraud is huge, and this would be an easy way to accomplish it. * Get one that says it is UNLOCKED, or untethered to a specific provider.  * Get an ATA that works in your country, ring tones and voltages and all that. * There may not be 911 or emergency services available to you through this setup. * If broadband goes down, so does your phone. ( My provider has a voicemail fallback which sends you the missed / unanswered messages in .wav format in a email ). * Beware of snake oil salesmen reborn as Voip providers.  Check on the voip forums at DSLReports.  They are an excellent resource.

If you can do this for a while and are happy, ditch your land line.  THEN you can get an asterisk server ( or yate ) going - point it at your VOIP provider and the ATA to YOUR server.  I haven't done this, as it won't give me anything I don't already have with this setup.

Any questions  ? Gimme a call !

I've done a "how to" on this at [http://tech.quagmire.ca](http://tech.quagmire.ca)

---

### Post by linuxtechie on 2010-12-15
^ Thanks Ceyx... actually a cool one.

+LT

---

### Post by Ceyx on 2010-12-15
Glad you liked it.  I find this area ( voip ) so fractured....

If you ever get into it, let me know.  Perhaps we can trade secrets !

Ciao

---

### Post by neuralbliss on 2011-01-15
Howdy,

This is going to be a very vague, short and unscientific description of a solution similar to being discussed. In fact i'm already embarrassed, but it was such a crazy setup for free (minus the adapter) and I was so impressed with it, I'll try and remember as much as possible. It was an engineer co-worker with me at VMware.

He had a regular old home phone with and adapter to allow it to attach to his router/switch. He used an asterisk server, pbx server, google voice number and a free sip provider.  This was all free.  I believe the issue was that to use the sip service for free it would only allow incoming calls unless you paid.  So he was able to use his normal old house phone to make incoming and outgoing phone calls basically using asterisks as a script server to be a middle man between his google voice and SIP service.  He was using asterisks to do some forwarding on the back end.  Either way on the front end he could pick up his phone and dial out like normal and receive calls normally.  Of course when you answered or dialed out it took a while and it would ring a separate number as to merge the two services.

That's as best I can remember without sounding even more stupid!

---

