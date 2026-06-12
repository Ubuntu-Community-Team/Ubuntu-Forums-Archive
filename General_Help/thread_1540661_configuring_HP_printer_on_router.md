---
title: "configuring HP printer on router"
date: 2010-07-28
forum: General Help
---

### Post by kiddykoff on 2010-07-28
Hey, i'm having a problem trying to configure the network side of an HP color laserjet 2605dn. It's plugged into my router, but i don't know how to find the dang thing from my laptop.

I got a configuration sheet printed out with tcp/ip settings, but it's all greek to me. some notable things i see are

...
host name = NPI167BE9
Domain name = 
Bonjour printer name = HP Color LaserJet 2605dn (167BE9)
IP address = 169.254.151.44
...

Could someone help me out here? I had it set up on another computer and was able to print from my laptop, but i don't want to turn on the desktop and have to login everytime.

---

### Post by chamber on 2010-07-28
If you go to add new printer in the Printer Configuration and then select Find Network Printer.


Use the IP Address of the printer (169.254.151.44) in the host section and then follow the prompts from there.

You should be required to download a driver, select your make and model and you should be good to go.

Just tested this running Crunchbang in a VM connecting to a network HP Colour Laserjet 2600n and it worked fine for me.

---

### Post by kiddykoff on 2010-07-28
okay, i did that and folowwed the prompts, but wasn't sure if i should have changed the connection that it was set at. 

It was put on HPLIP option, but there was also: LPD/LPR queue '', LPD/LPR queue 'LPT1', LPD/LPR queue 'LPT2', LPD/LPR queue 'COM3', LPD/LPR queue 'LPT4', LPD/LPR queue 'COM4_PASSTHRU', LPD/LPR queue 'LPT5_PASSTHRU', LPD/LPR queue 'COM6_PASSTHRU'. I used the HPLIP option

when i searched for drivers it didn't give me any options, so i chose from a database. I chose the color laserjet 2605. I think that's what worked for me before.

I printed a test page and got a troubleshooter to help me. it said

The queue 'HP-Color-Laserjet-2605' is not enabled. The reason given is: '/usr/lib/cups/backend/hp failed'. (it then told me how to enable it)

i enabled and tried it again, but it has done anything still. the job is here on my end, but the printer is still at its ready state.

---

### Post by kiddykoff on 2010-07-28
i tried again from scratch, this time i went through this option AppSocket/HP JetDirect. i input the same host address, but the port number i didn't know, so i left it at 9100.

Everything else i did the same. It's still not working except now i'm getting "processing - printer warning" as the status for the job on my test page.

---

### Post by chamber on 2010-07-28
Have you tried adding it by just using the find new printer option?

See screenshot.

Can't help at the minute as my printer is no where near me.

---

### Post by kiddykoff on 2010-07-28
finding network printer is the first thing that i did.

just for clarification, the printer is connected directly to the router and my laptop is accessing that router through WLAN

---

### Post by kiddykoff on 2010-07-28
I just tried it through the suggested way again, but this time i'm looking at the properties of the printer. the printer state is Processing - Connected to printer... however it has been like this for 4 minutes. the printer still reads ready on it's display

update: after 5 minutes ther printer state says Idle - /usr/lib/cups/backend/lpd failed

---

### Post by sgosnell on 2010-07-28
Have you installed hplip?  

I've never had a problem with an HP network printer, they just work under Ubuntu.  I have had problems using Windows, but never with Linux.  I always just start at System/Administration/Printing, click on New, and have it find the printer, then accept the default settings it gives.  I haven't tried that specific model, but in general HP printers just work with Linux.  You might also try the HP website for a driver, but it shouldn't be necessary, at least in theory.

---

### Post by DarthScape on 2010-07-28
Well to start, how is the printer connected to the router: USB or Ethernet? Next, it looks like the printer is getting a self-assigned IP address (169.254...) therefore it is not really accessible by anything unless the rest of your network has self-assigned IP addresses.

---

### Post by kiddykoff on 2010-07-28
the printer is hooked up by ethernet. I'm sure that i have HPLIP installed because i've had this printer working by direct usb hookup and having it hooked up on a seperate machine acting as printer server.

It's just recently that i discovered a ethernet port on the printer.

---

### Post by sgosnell on 2010-07-28
Make sure you remove the USB printer from the system.

---

### Post by kiddykoff on 2010-07-29
> **sgosnell said:**
> Make sure you remove the USB printer from the system.

it's been removed, but i do have a printer that i use when away from home that hooks up by usb. should i remove that too? it's a different printer entirely.

---

### Post by sgosnell on 2010-07-29
No, a different printer should be no problem.  You do want to give the printer a static IP, though, to make sure it's always at the same IP.  Using hplip, you can use the host name, and connect regardless of the IP, but I prefer using a static IP.  You do this through the router settings.  Most routers allow you to set static IPs for clients, and I routinely do that for the devices on my network, including the printer and the computers at home.  It just makes things easier for me to remember, and there are fewer conflicts.

You may have a problem with cups.  Reinstalling it might help, it's quick and worth a try.  Do make sure you delete all pending print jobs, if any are left.  They will prevent new jobs from printing, even if the original problem has been solved.

---

### Post by kiddykoff on 2010-07-31
i think i'm able to connect to the printer, but i'm having an error in communication, so i don't think i'll need to assign a static ip + I couldn't figure it out with my netgear router on an additional note, the printer doesn't show up on my attached devices, but when i do a search for a network printer using the host name or the i, it shows up

I've gotten it to show up using the hplip-gui and on the system-config-printer. but when it comes to printing, it wants to give me that error message in the printer status.

Is there any packages that i should consider reinstalling?

---

### Post by kiddykoff on 2010-07-31
It seems that whatever method i do to setup the printer i get the same errors.

I've run this
```
kurtis@Turion:~$ /usr/lib/cups/backend/hp
direct hp "Unknown" "HP Printer (HPLIP)"

```
but it doesn't seem to help me any. i might just reattach it to computer and give up.

---

### Post by sgosnell on 2010-08-01
It definitely should show up on the router, if it has been given an IP address.  Can you open 169.254.151.44 in your browser?  That's a non-standard IP address, it should be either 192.168.x.x, where x is a number between 0 and 255, or 10.0.0.x, depending on the router.  It is certainly possible to change the addresses to something like you posted, but that's not usual.  Try finding the IP address of the router, and setting the IP of the printer to something close - identical for the first 3 numbers, higher for the last one.  This is another situation where static IP addresses can help or hinder.

---

### Post by kiddykoff on 2010-08-03
I already moved the printer to another computer and it's working there as long as that computer is turned on. 

I couldn't figure out how to get a static ip for it. I have a netgear router and it didn't give a simple option for it. I'll probably try again when the printer isn't in heavy use.

---

### Post by sgosnell on 2010-08-04
I don't have a manual handy for a Netgear, but it's in the settings, and it's not hard to set static IPs on them.

---

### Post by cmcanulty on 2010-08-04
I recently spent a ton of time setting up a network HP printer at our library for several ubuntu machines. Here is what worked for me under host type host name from config page not ip address, then I marked each computer to not share the printer but available for all also HP told me not to set a static ip address from router which didn't work for me but set it up from a HP web page which did work.

---

### Post by kiddykoff on 2010-08-04
> **cmcanulty said:**
> I recently spent a ton of time setting up a network HP printer at our library for several ubuntu machines. Here is what worked for me under host type host name from config page not ip address, then I marked each computer to not share the printer but available for all also HP told me not to set a static ip address from router which didn't work for me but set it up from a HP web page which did work.

I think that sharing it could have been a problem. but then again i deleted the printer settings everytime i tried to set it up again. hmm... maybe the setting was still enabled somewhere else.

I don't have the time to try it again though. I think if i try this again my family may start a riot.

---

### Post by kiddykoff on 2010-10-23
My family has just switched ISP's so i took another stab at this project. The old netgear router/modem was replaced by a linksys router and RCA modem combo.

I plugged in the printer to the router and added a new printer by using the find network printer. I used the default options and it just worked.

I have upgraded to 10.10 since then, so either linksys is better than netgear or something worked for me in 10.10. either way, i'll mark this as solved.

thanks for the help, all that posted.

---

### Post by clay_in_nj on 2010-10-23
I was surprised, a couple of Ubuntu versions back, that after the OS install I got an icon in the notification area telling me that my HP network printer had been detected and driver installed, automagically! :)

---

