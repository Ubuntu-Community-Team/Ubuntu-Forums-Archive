---
title: "DSL  active after midnight"
date: 2010-03-23
forum: General Help
---

### Post by Silvernail on 2010-03-23
I don't know what tags to search for or keywords.

There are 2 computers and 1 wireless modem hooked up to my DSL router.

After midnight and I have turned my computer off the DSL modem router lights will start to flash like it is transmitting data. My daughters desktop and wireless laptop are sometimes turned off and sometimes not. When I unplug the wire to her house across the street the flashing stops, I wait about 45 seconds and plug it in and the flashing light start up again.

To chase this down:
What apps do I need to install?
Is there a Howto on digging around in your system?

Will someone direct me to information on this sort of thing?
TIA
Dave

---

### Post by DUKANE on 2010-03-23
I'm not following here. There is traffic coming from your daughter's computer...which could be on. Seems normal to me...

Maybe go for a deeper explanation of the issue.

---

### Post by Silvernail on 2010-03-23
When I get up at 5 AM to goto the bathroom the DSL modem and router are active. No one is awake and on either computers. How much transfer of data would  happen from a computer that is sitting idle?

---

### Post by TBABill on 2010-03-23
Depends on what it's setup to do. My Windows computers download updates after midnight (like 130am I think). Could she have an online virus scan setup to run nightly?  I am just taking guesses. Is she on a Windows machine? Could she leave something running even when not in use, such as a messenger program, applet (news feed) or something else that transmits and receives online info in the background? Or does she leave a P2P program open like Limewire even when not downloading? Those upload by user request if it's enabled that way on her machine.

Just some ideas...

---

### Post by linden940 on 2010-03-23
well think about the update checkers for all the programs you have installed...and if they are signed into lets say yahoo or msn or any of those


and to tell you the truth...unplug the dsl box and the "lights" on the router will still go on and off....EVEN tho its not on the net it still is giving and sending data to all the computers that ARE connected at that time....

if you feel someone or something is on your computer and or net/router box...go into your router and look at how many ip address that are on the router...if there are more than they computers that you have...someone else is on it.


and...if you DONT have a pass word on it....put a password on it....or your house will become the next coffee shop with people sitting outside or close by jumping onto YOUR router/web

---

### Post by capscrew on 2010-03-24
> **Silvernail said:**
> When I get up at 5 AM to goto the bathroom the DSL modem and router are active. No one is awake and on either computers. How much transfer of data would  happen from a computer that is sitting idle?

Don't guess.  Test!  Run [[COLOR="Indigo"]**_NMAP _**[/COLOR]]("http://nmap.org/")(Zenmap is the GUI interface) and see who is on you local network.  You can also run [[COLOR="Navy"]**_Wireshark _**[/COLOR]]("http://www.wireshark.org/")to see what data is being passed into and out of the LAN.

Both of these applications are in the repos.

---

### Post by DeMus on 2010-03-24
> **Silvernail said:**
> I don't know what tags to search for or keywords.

There are 2 computers and 1 wireless modem hooked up to my DSL router.

After midnight and I have turned my computer off the DSL modem router lights will start to flash like it is transmitting data. My daughters desktop and wireless laptop are sometimes turned off and sometimes not. When I unplug the wire to her house across the street the flashing stops, I wait about 45 seconds and plug it in and the flashing light start up again.

To chase this down:
What apps do I need to install?
Is there a Howto on digging around in your system?

Will someone direct me to information on this sort of thing?
TIA
Dave

This flashing goes on all night? Or just a short moment? Could be your provider checking the software in your modem and if it is old updating it. Or adjusting the settings for firewall, virusscanner or whatever you have installed in there. If the computers are off then they don't send or receive data. To be 100% sure about that, pull the plug of the power cable to the computers and see if the lights still flash.

---

