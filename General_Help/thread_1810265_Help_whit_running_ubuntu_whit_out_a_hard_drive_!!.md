---
title: "Help whit running ubuntu whit out a hard drive !?!"
date: 2011-07-22
forum: General Help
---

### Post by Fmslick on 2011-07-22
Hello:D i have been running ubuntu on an off for a yr now & i need a bit of help!?! 
I have a laptop that i am using for my tv so it can connect to the  internet so i can get netflix:popcorn: & so on, but the hard driver is going out on it so i was thinking bout run ubuntu off of a cd but i need to know how long can i do that for & how to share the wifi whit the lan port on the laptop as it is running off of the ubuntu cd or can this be done?


EX:
FROM(router-TO-wifi)------[TO-(VA WIFI)-]------(laptop-/OUT/-lan-PORT)--------[TO]--------(tv)-VA Cat5

:confused:

---------------------------------
*EDIT*
The laptop is not going to move or be used in an way but to hook my tv up to the net like a gateway or a mini lan. 
EX: 
FROM(router-TO-wifi)------[TO-(VA WIFI)-]------(laptop-/OUT/-laptop-lan-PORT)--------[TO]--------(tv)-VA Cat5

lol i think i just lost my self?!

---

### Post by btindie on 2011-07-22
CD's are a little slow and can only be used the once which is problematic if you're making a custom distro. You'd be better off customising an Ubuntu live ISO and putting it onto a USB stick. You can also create persistent storage directly on the USB stick if you like.

[https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks](https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks)

---

### Post by ClientAlive on 2011-07-22
+1

Yeah, I think that if you need to save anything it would be better to run it off usb and create persistent storage. Otherwise, without persistent storage set up, running Ubuntu live will not save changes whenever you shut down or anything interrupts it.

---

### Post by Fmslick on 2011-07-22
> btindie	
cd's are a little slow and can only be used the once which is problematic if you're making a custom distro. You'd be better off customising an ubuntu live iso and putting it onto a usb stick. You can also create persistent storage directly on the usb stick if you like.

[https://help.ubuntu.com/community/in...20hard%20disk](https://help.ubuntu.com/community/in...20hard%20disk)

&
&
> clientalive	

+1

yeah, i think that if you need to save anything it would be better to run it off usb and create persistent storage. Otherwise, without persistent storage set up, running ubuntu live will not save changes whenever you shut down or anything interrupts it.

can i make a ubuntu live iso dvd, how windows can use a dvd as a usb stick?

I do not have a usb stick & i don't need to save any thing at all/the laptop never shut down an if by "interrupts it" you mean like the power going out or some then like that? well it has a new battery in it.:D

---

### Post by pqwoerituytrueiwoq on 2011-07-22
> **Fmslick said:**
> Hello:D i have been running ubuntu on an off for a yr now & i need a bit of help!?! 
I have a laptop that i am using for my tv so it can connect to the  internet so i can get **netflix**:popcorn: & so on, but the hard driver is going out on it so i was thinking bout run ubuntu off of a cd but i need to know how long can i do that for & how to share the wifi whit the lan port on the laptop as it is running off of the ubuntu cd or can this be done?


EX:
:KS(router/wifi)------[TO]------(wifi-/-laptop-/-lan)--------[TO]--------(tv):KS

:confused:
you are going to need a TON (probably 10 gigs min) of ram to pull that of with only a live cd and time also as you will need to install virtual box and windows to use that on every boot with out a hdd a hard drive in under 50$

if you give up netflix it is very doable

---

### Post by Fmslick on 2011-07-22
> **pqwoerituytrueiwoq said:**
> you are going to need a TON (probably 10 gigs min) of ram to pull that of with only a live cd and time also as you will need to install virtual box and windows to use that on every boot with out a hdd a hard drive in under 50$

if you give up netflix it is very doable


i do not use the laptop at all.. it is more like a gateway for my tv to get on the net, the laptop is on 24/7 & no-one use's it at all...

ps i edited the post up top

---

### Post by pqwoerituytrueiwoq on 2011-07-22
> **Fmslick said:**
> i do not use the laptop at all.. it is more like a gateway for my tv to get on the net, the laptop is on 24/7 & no-one use's it at all...
so it is playing the part of a wireless router?
set it to go into standby on battery
if it is being used like that even when the hdd fail as long as it does not loose power it will keep running like nothing happened thanks to cache

---

### Post by Fmslick on 2011-07-22
> **pqwoerituytrueiwoq said:**
> so it is playing the part of a wireless router?
set it to go into standby on battery
if it is being used like that even when the hdd fail as long as it does not loose power it will keep running like nothing happened thanks to cache

wireless router? Yes.. 

but no "standby on battery" it is just on & it is running win7 as of right now & if the HDD fails on it well idk if it is going to stay running an if the power duz go out an the battery gives out too i would like away to get it up & run whit our a HDD or usb stick, If i can +this type of stuff is fun to me. call me a Tinkernut :)

---

### Post by pqwoerituytrueiwoq on 2011-07-22
> **Fmslick said:**
> wireless router? Yes.. 

but no "standby on battery" it is just on & it is running win7 as of right now & if the HDD fails on it well idk if it is going to stay running an if the power duz go out an the battery gives out too i would like away to get it up & run whit our a HDD or usb stick, If i can +this type of stuff is fun to me. call me a Tinkernut :)
are you streaming the data to the laptop and using the tv as a monitor?
or us it being passed through the laptop so the network can get to something else
if it is the first one better hope the netflix chrome addon comes out before the hdd fails or you will have to get a new hdd for windows

---

### Post by Mark Phelps on 2011-07-23
> **Fmslick said:**
>  ... how windows can use a dvd as a usb stick?

DVDs can NOT be used as normal filesystems, even DVD+-RW drives.  

Information has to be "burned" to DVD media in the form of "sessions".  

The "RW" indicates that you can either (1) erase the DVD and rewrite it or (2) can append new sessions to the end.  It's not like a hard drive filesystem.

---

### Post by Fmslick on 2011-07-24
> **pqwoerituytrueiwoq said:**
> are you streaming the data to the laptop and using the tv as a monitor?
or us it being passed through the laptop so the network can get to something else
if it is the first one better hope the netflix chrome addon comes out before the hdd fails or you will have to get a new hdd for windows

are you streaming the data to the laptop and using the tv as a monitor? - NO
*
us it being passed through the laptop so the network can get to something else? YES.

This is why i think i don't need a HHD for the laptop. 
so now we got that out of the way how can i do this?

---

### Post by Fmslick on 2011-07-24
> **Mark Phelps said:**
> DVDs can NOT be used as normal filesystems, even DVD+-RW drives.  

Information has to be "burned" to DVD media in the form of "sessions".  

The "RW" indicates that you can either (1) erase the DVD and rewrite it or (2) can append new sessions to the end.  It's not like a hard drive filesystem.

Yes you can use a DVD as a USB stick, when i pop a dvd in to my windows7 (keep in mind) it ask me do you want to burn or run as a usb... ill post a pic if you like?

---

