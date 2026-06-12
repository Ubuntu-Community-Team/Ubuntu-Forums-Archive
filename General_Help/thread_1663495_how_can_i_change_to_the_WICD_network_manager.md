---
title: "how can i change to the WICD network manager?"
date: 2011-01-09
forum: General Help
---

### Post by JuicyCouture on 2011-01-09
i know how to actually get it - but yesterday i was following some guys advice, on how to switch to it because i keep getting my connection dropped with the default network manager. he said to make sure i was plugged in via ethernet, purge network manager - then apt-get WICD. the problem is, not even ethernet works once network manager is purged.

so - before i try this i wanna know, can i just download WICD before hand, then purge network manager, then install WICD. OR, can i just install WICD now, then once i purge network manger it will move over to WICD as the default?

how should i go about changing to WICD? thaank you


[B]EDIT: NEW BONUS CHALLENGE PROblemS TO FIX!

okay that didnt fix my problem

it has to be a driver thing, its happened on multiple installs - on network manager and on WICD

it usually happens (or at least more often) when im streaming a live feed from a website, and it doesnt reset itself unless i turn the computer OFF (not restart) and back on

basically what happens is, with both the network manager and WICD - the wireless just cuts out and stops detecting any network at all, disconnected. i have tried terminating the process and restarting the applications via terminal or run command; i dont know what to do it just keeps happening. sometimes it wont happen for 2 days, sometimes it happens five times in one day. 

it really seems to be affected by what im doing on, sometimes i'll have multiple videos going and it starts to chug, and i know when its gonna happen - wifi cuts out. it doesnt DROP, it just stops working, detecting networks. 

like i said, even restarting doesnt fix this. i have to quit the application, turn the computer on and off - then boom its right back on when it comes back.

so strangeeee.

so far i've had 3 ubuntu problems in the week i've had it.

1. this
2. "couldnt update .ICEauthority" at login
3. and this made me have to reinstall yesterday - nothing i would install would run anymore, no errors, no processes - i just click the icons and nothing happens.

oi vey[/B]

---

### Post by isee on 2011-01-09
Is it not in Synaptic?  After you get the packages I believe you can have both NM and wicd installed, pick which one you want to log on with, and yes wicd will solve your dropped connection problems.

I just switched to wicd and pppoeconf on my desktop too, because NM would drop torrent connections, so never mind just dropping wireless, NM will drop wired signals too it seems.

PS  As far as I can tell there is no need to purge NetworkManager, I would just leave it alone and use wicd.

---

### Post by JuicyCouture on 2011-01-09
> **isee said:**
> Is it not in Synaptic?  After you get the packages I believe you can have both NM and wicd installed, pick which one you want to log on with, and yes wicd will solve your dropped connection problems.

I just switched to wicd and pppoeconf on my desktop too, because NM would drop torrent connections, so never mind just dropping wireless, NM will drop wired signals too it seems.

PS  As far as I can tell there is no need to purge NetworkManager, I would just leave it alone and use wicd.



you mean it asks which one you want to use in the log in screen? i log in automatically so how can i set it to default?

---

### Post by 73ckn797 on 2011-01-09
> **isee said:**
> there is no need to purge NetworkManager, I would just leave it alone and use wicd.

You may want to disable NM in Startup Applications so it will not try to run over WICD or create any conflicts.

---

### Post by JuicyCouture on 2011-01-09
> **73ckn797 said:**
> You may want to disable NM in Startup Applications so it will not try to run over WICD or create any conflicts.


is adding WICD through software center the same as synaptic? same versions?

---

### Post by isee on 2011-01-09
If it's in Synaptic, that is the way I would have done it.  It was a while ago.  I have a post about it somewhere.  Please research it a little more.   Please follow others advice also.  I think I 'm mistaken about both at the same time, probably either one or the other but both will be in Synaptic so you can switch there.

---

### Post by JuicyCouture on 2011-01-09
is there no way within ubuntu to pick which to use?

so we're just assuming that if i install WICD, and disable network manager from starting at login - that WICD will be the default?

---

### Post by isee on 2011-01-09
Here's where I first heard of wicd, and later it proved very good to know as it doesn't drop signals, and I think it has a better GUI also, just a better program IMO

[http://ubuntuforums.org/showthread.php?t=1244083](http://ubuntuforums.org/showthread.php?t=1244083)

---

### Post by isee on 2011-01-09
I think I was mistaken about that, the using both statement, due to some fooling around with wicd on my desktop.

I think if you install wicd through Synaptic, it uninstalls NM, and if you reinstall NM, it will uninstall wicd, like that.

Just I see no need to purge it.  You may find problems with wicd one day and want to switch again.  Just saying :)

---

### Post by JuicyCouture on 2011-01-09
okay one other problem that i could forsee happening

i diable network manager from the start programs, but WICD isnt on the list - how do i add WICD to startup applications if its not already listed?

---

### Post by isee on 2011-01-09
I didn't have to do anything like that.  I simply selected wicd in Synaptic for installation, and it like it tells you which packages it will install, it also tells you which packages it will uninstall, which will be the NetworkManager pakages.  Then when you reboot wicd is your new network manager automatically.  There will be a different icon in your panel, the NetworkManager applet will be gone, replaced by the wicd one.

To switch back you need to reinstall NetworkManager in Synaptic, which will then automatically work as you network manager when you reboot.

I really think that is correct.  If I had my laptop here I would check for you.  Sorry.

PS  I did all of this making sure I had access to a wired connection, in case I had wireless problems.  In fact if I remember correctly I was plugged in the whole time.

---

### Post by JuicyCouture on 2011-01-09
no you've been quite helpful thanks

i notice in synaptic sometimes, say i search for WICD there will be a bunch of them - i just want the top one that just says WICD right, not "WICD daemon" etc.

i think those are just files that go with it right, technical files

---

### Post by isee on 2011-01-09
Yeah just wicd.  The daemon and more will probably install also, but they will automatically be selected along with some others.  It should also tell you which it is uninstalling, you may want to look.  I think network-manager is the main NetworkManager file.

Do you have a wired connection?  I'm not too sure if you can do this wirelessly.  I'd plug it in just to make sure you have no wireless issues when trying to change.  Maybe Im just overly cautious.

---

### Post by JuicyCouture on 2011-01-09
> **isee said:**
> Yeah just wicd.  The daemon and more will probably install also, but they will automatically be selected along with some others.  It should also tell you which it is uninstalling, you may want to look.  I think network-manager is the main NetworkManager file.

Do you have a wired connection?  I'm not too sure if you can do this wirelessly.  I'd plug it in just to make sure you have no wireless issues when trying to change.  Maybe Im just overly cautious.


alright i did what you said (i am on wireless, it still worked)

now i have both icons in the system tray after a restart (it never said anything about removing network manager during the install)

[http://i514.photobucket.com/albums/t345/ryancouture/Screenshot.png]("http://i514.photobucket.com/albums/t345/ryancouture/Screenshot.png")

so now you're saying i should go in to startup applications and disable network manager?

---

### Post by isee on 2011-01-09
I think I do recall switching NetworkManager off in the startup applications.  Doing that might stop the NM icon from being in the panel (lol tray is a windows term) and then just start using wicd.  At any rate if something is wrong just re-enable it and reboot.

---

### Post by JuicyCouture on 2011-01-09
okay that didnt fix my problem

it has to be a driver thing, its happened on multiple installs - on network manager and on WICD

it usually happens (or at least more often) when im streaming a live feed from a website, and it doesnt reset itself unless i turn the computer OFF (not restart) and back on

basically what happens is, with both the network manager and WICD - the thing wireless just cuts out and stops detecting any network at all, disconnected. i have tried terminating the process and restarting the applications via terminal or run command; i dont know what to do it just keeps happening. sometimes it wont happen for 2 days, sometimes it happens five times in one day. 

it really seems to be effected by what im doing on, sometimes i'll have multiple videos going and it starts to chug, and i know when its gonna happen - wifi cuts out. it doesnt DROP, it just stops working, detecting networks. 

like i said, even restarting doesnt fix this. i have to quit the application, turn the computer on and off - then boom its right back on when it comes back.

so strangeeee.

so far i've had 3 ubuntu problems in the week i've had it.

1. this
2. "couldnt update .ICEauthority" at login
3. and this made me have to reinstall yesterday - nothing i would install would run anymore, no errors, no processes - i just click the icons and nothing happens.

oi vey

---

### Post by JuicyCouture on 2011-01-09
oh great it just happened again while i was playing armagetron

does anyone know maybe where i can different drivers for my wifi card? its an atheros 5100 or something like that. thats the only other variable.

this never happened once to me in 3 years with windows so its gotta be the driver now.

btw in WICD what do you guys have set for "WPA supplicant driver"

another thing i notice thats strange, and this has happened on windows before but not usually - on my network connections, for the wifi its picking up - theres ours "couture family" and right under it always a generic "linksys" unsecured one? ours is a linksys router and the only one around here. is it possible my router is giving off one secured and one non-secured connection?

actually hang on a tick...do you think that could be the problem? thats its confusing the two? i remember on windows 7, the only time i would see my family connection pop up, as well as my router - it was right after a problem with the connection then it sorted itself out.

---

### Post by isee on 2011-01-09
Sorry that didn't work for you.  Hopefully you can resolve your issue and THEN use wicd. :)

Good luck!

---

