---
title: "duplicate administrator this device is managed by another user currently"
date: 2011-09-09
forum: General Help
---

### Post by lifestreammm on 2011-09-09
Everytime I start up firefox now, I get this message:

"duplicate administrator    
this device is managed by another user currently!!"

It started when fooling around the "offline" option in my gmail account.
This offline thing had problems loading my inbox (it just froze - maybe this gmail-offline thing is not very compatible with firefox or ubuntu - haven't got a clue), so i started turning the offline-option off and on to see if I could make it work.

It didn't, and now I can't open any webpages.

I have a laptop,  with wired network, ubuntu 10.04

Thank you
Life

---

### Post by Bodsda on 2011-09-09
> **lifestreammm said:**
> Everytime I start up firefox now, I get this message:
 
"duplicate administrator 
this device is managed by another user currently!!"
 
It started when fooling around the "offline" option in my gmail account.
This offline thing had problems loading my inbox (it just froze - maybe this gmail-offline thing is not very compatible with firefox or ubuntu - haven't got a clue), so i started turning the offline-option off and on to see if I could make it work.
 
It didn't, and now I can't open any webpages.
 
I have a laptop, with wired network, ubuntu 10.04
 
Thank you
Life
 
That doesnt sound like a firefox message to me.
 
Reboot your router, and try again. Ensuring firefox is in online mode.
 
Bodsda

---

### Post by Wim Sturkenboom on 2011-09-09
Did you do any research? Google search for ["duplicate administrator"](http://www.google.com/search?hl=en&source=hp&biw=1203&bih=591&q=%22duplicate+administrator+%22&oq=%22duplicate+administrator+%22&aq=f&aqi=g5g-m1&aql=&gs_sm=e&gs_upl=527475l529505l0l529862l3l3l0l0l0l0l752l1210l4-1.0.1l2l0)

---

### Post by haqking on 2011-09-09
> **lifestreammm said:**
> Everytime I start up firefox now, I get this message:

"duplicate administrator    
this device is managed by another user currently!!"

It started when fooling around the "offline" option in my gmail account.
This offline thing had problems loading my inbox (it just froze - maybe this gmail-offline thing is not very compatible with firefox or ubuntu - haven't got a clue), so i started turning the offline-option off and on to see if I could make it work.

It didn't, and now I can't open any webpages.

I have a laptop,  with wired network, ubuntu 10.04

Thank you
Life

Sounds to me like at some point you logged into the router interface and somewhere it is caching the login and when you try to launch firefox it is still attempting to re-administer the router possibly ?

try a router reboot
refresh your browser cache with a ctrl+f5
or you have a browser with a homepage that auto connects to your router

if all else fails assuming you have a router backup config, reset to factory then flash back your settings. ?

---

### Post by lifestreammm on 2011-09-09
> **Wim Sturkenboom said:**
> Did you do any research? Google search for ["duplicate administrator"]("http://www.google.com/search?hl=en&source=hp&biw=1203&bih=591&q=%22duplicate+administrator+%22&oq=%22duplicate+administrator+%22&aq=f&aqi=g5g-m1&aql=&gs_sm=e&gs_upl=527475l529505l0l529862l3l3l0l0l0l0l752l1210l4-1.0.1l2l0")
Yes I did. Mostly I got hits talking about belkin-routers and wireless networks. I didn't think it useful for me. But then again I don't know very much about this.

Thank you Bodsda, I switched over to ubuntu, and looked in the help pages on how to reboot a router (I have no idea), didn't really find it. And just to see if the problem was still there I started firefox again. It worked fine.
??? 
I don't know why, though, my guess is: when I was in windows (I have a partitioned hard disk - one is ubuntu, the other is windows) I made sure my gmail-offline settings were disabled (they were), and I also deleted all old stored mail on my computer (that I didn't do before). I think that did it, because firefox also forgot my password in the loginscreen, so it seems it got rid of all files and cookies (I'm not sure if cookies is the right word). And by doing this getting rid of this duplicate signing-in, I think these cookies or whatever were doing that by themselves or something (this is my simplistic explanation). When I switched to ubuntu verything started fine (the offline settings of mygirlfriends gmail account as well).

Computers are bizarre. Or probably not bizarre, they're probably perfectly logical, but I wonder if thet haven't become that complex that we can't understand it anymore. 

Thank you Haqking for the help.

So, problem solved, but I don't know why.

Blessings!

---

### Post by haqking on 2011-09-09
> **lifestreammm said:**
> Yes I did. Mostly I got hits talking about belkin-routers and wireless networks. I didn't think it useful for me. But then again I don't know very much about this.

Thank you Bodsda, I switched over to ubuntu, and looked in the help pages on how to reboot a router (I have no idea), didn't really find it. And just to see if the problem was still there I started firefox again. It worked fine.
??? 
I don't know why, though, my guess is: when I was in windows (I have a partitioned hard disk - one is ubuntu, the other is windows) I made sure my gmail-offline settings were disabled (they were), and I also deleted all old stored mail on my computer (that I didn't do before). I think that did it, because firefox also forgot my password in the loginscreen, so it seems it got rid of all files and cookies (I'm not sure if cookies is the right word). And by doing this getting rid of this duplicate signing-in, I think these cookies or whatever were doing that by themselves or something (this is my simplistic explanation). When I switched to ubuntu verything started fine (the offline settings of mygirlfriends gmail account as well).

Computers are bizarre. Or probably not bizarre, they're probably perfectly logical, but I wonder if thet haven't become that complex that we can't understand it anymore. 

Thank you Haqking for the help.

So, problem solved, but I don't know why.

Blessings!

no worries, for future reference for router issues if in doubt reboot it.

rebooting is nothing to do with ubuntu or any other OS, it means restart the device

Best way is to hit power button and wait 10 seconds then power it back on :wink:

Resetting it means pressing a pen or paper clip into the little reset  button, however this assumes you have a back up of any settings you  changed from the factory defaults :wink:

The reason it is working now i am asuming is the login timeout from inactivity on the router interface, it has expired so now allowing you to resume to normality

well sorted anyways so glad you got it worked out.

please mark your thread as solved from thread tools to assist others in there search for solutions, cheers

peace

---

### Post by Bodsda on 2011-09-09
> **lifestreammm said:**
> Yes I did. Mostly I got hits talking about belkin-routers and wireless networks. I didn't think it useful for me. But then again I don't know very much about this.
 
Thank you Bodsda, I switched over to ubuntu, and looked in the help pages on how to reboot a router (I have no idea), didn't really find it. And just to see if the problem was still there I started firefox again. It worked fine.
??? 
I don't know why, though, my guess is: when I was in windows (I have a partitioned hard disk - one is ubuntu, the other is windows) I made sure my gmail-offline settings were disabled (they were), and I also deleted all old stored mail on my computer (that I didn't do before). I think that did it, because firefox also forgot my password in the loginscreen, so it seems it got rid of all files and cookies (I'm not sure if cookies is the right word). And by doing this getting rid of this duplicate signing-in, I think these cookies or whatever were doing that by themselves or something (this is my simplistic explanation). When I switched to ubuntu verything started fine (the offline settings of mygirlfriends gmail account as well).
 
Computers are bizarre. Or probably not bizarre, they're probably perfectly logical, but I wonder if thet haven't become that complex that we can't understand it anymore. 
 
Thank you Haqking for the help.
 
So, problem solved, but I don't know why.
 
Blessings!
 
Well, I'm glad its sorted. 
 
Computers are extremely logical, but only as logical as the developer who programmed them. Complexity is relative. Fitting new spark plugs could be second nature to a mechanic, but could be complex to an interior designer. Computers are complex to those who do not understand them, perfectly understandably... :)
 
Rebooting a router. A router is a little square'ish(usually) box that is connected to your PC(usually) which gives access to the internet(usually). Pulling the power cable out and sticking it back in is sufficient to reboot a router(always) :). 
 
Bodsda

---

### Post by lifestreammm on 2011-09-09
> **Bodsda said:**
> Well, I'm glad its sorted. 
 
Rebooting a router. A router is a little square'ish(usually) box that is connected to your PC(usually) which gives access to the internet(usually). Pulling the power cable out and sticking it back in is sufficient to reboot a router(always) :). 
 
Bodsda

Hahahahaaaa! Ok, I have to admit, that was simple. But for a layman like me, it sounded more complicated! (I'm in a library as well, so I don't have or can't see abox, let alone they would let me tamper with them :) )
lol

---

### Post by Bodsda on 2011-09-09
> **lifestreammm said:**
> Hahahahaaaa! Ok, I have to admit, that was simple. But for a layman like me, it sounded more complicated! (I'm in a library as well, so I don't have or can't see abox, let alone they would let me tamper with them :) )
lol
 
... Your in a library? 
Well, that kinda blows our theory of what was going wrong, into the water. But its working now, so all good :)
 
Bodsda

---

### Post by haqking on 2011-09-09
> **Bodsda said:**
> ... Your in a library? 
Well, that kinda blows our theory of what was going wrong, into the water. But its working now, so all good :)
 
Bodsda


ahh yes i think i know what happened.  his current IP was probably set to that of his networks router, when he initially connected it appeared he was tring to access the router then probably got updated via DHCP or whatever somewhow ;-) then he was able to resume...possibly..kinda LOL

oh well all sorted anyways ;-)

---

### Post by lisati on 2011-09-09
> **lifestreammm said:**
> So, problem solved, but I don't know why.
That's good to hear.

Here's my $0.02: It sounds to me a similar situation to when I've been blcoked out from administering my router when the IP address the machine I'm connected from has changed for some reason (e.g. switching from wired to wireless or vice versa). Usually easily fixed by restarting or replugging.

---

### Post by haqking on 2011-09-09
> **lisati said:**
> That's good to hear.

Here's my $0.02: It sounds to me a similar situation to when I've been blcoked out from administering my router when the IP address the machine I'm connected from has changed for some reason (e.g. switching from wired to wireless or vice versa). Usually easily fixed by restarting or replugging.


it appears he couldnt as he was in library and no control over the box ;-)

ahhh well resolved anyways

---

### Post by lisati on 2011-09-09
> **haqking said:**
> it appears he couldnt as he was in library and no control over the box ;-)


Missed that detail.... :D

---

