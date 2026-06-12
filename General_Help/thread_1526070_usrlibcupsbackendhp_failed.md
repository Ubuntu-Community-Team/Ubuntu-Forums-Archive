---
title: "/usr/lib/cups/backend/hp failed"
date: 2010-07-07
forum: General Help
---

### Post by danielrs on 2010-07-07
I'm running Lucid and I have a HP color LaserJet 2840 printer connected via wifi. Until yesterday it was working, b now I get the the error "/usr/lib/cups/backend/hp failed"

Can anyone please help me debug this?

---

### Post by danielrs on 2010-07-08
bump

---

### Post by benson444 on 2010-07-08
I think that was the error I had a couple of days ago.

Try opening the printer settings (System -> Admin -> Printing), then right-click the printer and choose properties. Click on Policies, on the left, and make sure the State Enabled check box is checked.

---

### Post by danielrs on 2010-07-08
Yes, it is checked.

---

### Post by shaav on 2010-07-08
I'm having the same problem with my HP Laserjet 1020 (and it is checked).  In the syslog:
```

Jul  8 12:11:07 Morgan-Lnx hpijs[9093]: io/hpmud/musb.c 1121: unable to open hp:/usb/HP_LaserJet_1020?serial=JL2Z6VB
Jul  8 12:11:09 Morgan-Lnx hp[9062]: io/hpmud/musb.c 1121: unable to open hp:/usb/HP_LaserJet_1020?serial=JL2Z6VB
Jul  8 12:11:09 Morgan-Lnx hp[9062]: prnt/backend/hp.c 745: ERROR: open device failed stat=12: hp:/usb/HP_LaserJet_1020?serial=JL2Z6VB
Jul  8 12:12:26 Morgan-Lnx avahi-daemon[827]: Invalid query packet.
```

Update:

I reinstalled hplip from the package manager; it didn't work at first but then ran "hp-toolbox" and it did print the test page and appears to be working from other applications again.  In the "Status" tab of the toolbox it does show a "Device communication error" that was subsequently replaced by "Idle" 10minutes later.  Not sure what I did, but at least the toolbox shows error codes which may be of some help.

---

### Post by danielrs on 2010-07-09
I reinstalled hplip on synaptic and I still get the same error.

Maybe it was an update to cups, I used to have 3 computers working and now I have 4 that doesn't work (the 4th is a new computer). Is there any way i can get a list list of what was updated on the system?

---

### Post by uggeli on 2010-08-06
I got same error with HP PSC 1410 and I needed to do following:

1. install hplib-gui (to get hp-toolbox)

Then after trying to print testpage via hp-toolbox it still stopped to Queue stage. So...

2. I needed to go to "Printer Control" tab in hp-toolbox ad click "Start Printer", after that testpage printed out, and I was able to use printer in other applications also.


Don't know what caused this problem though, since printer was working ok earlier. Problems started after installing mpage (to be able to print multiple pages per sheet) and printed my first document with mpage. Everything went fine until paper jam. After that I wasn't able to print anymore, till now...

---

### Post by baddnady23 on 2010-08-06
I get the same problem every couple of weeks or so.  In order to work around it, i need to go into CUPS and remove the printer.  Then I need to reboot the printer, wait a while and then add the printer to CUPS again. Kind of annoying...

One thing of note is that when I go to reboot the printer, it it frozen on its control panel and I need to actually unplug it and plug it back in.  

I am using a HP OfficeJet 6500_E709n

---

### Post by danielrs on 2010-08-06
I'm sure it was a problem with an update because I never had this problem before on my computer, then I had to install this printer on a few other computers and it wasn't working in any if them (including mine) and a few weeks later magically they all started working without problems.

---

### Post by baddnady23 on 2010-08-10
Could be, but Im not sure.  Usually when it happens for me, it is just a very random occurance.  No recent updates, nonew software installed.  I use my printer everyday and it has even happened between printing two documents.  Just a bug I suppose, but I'm confident that over time it will be worked out.

---

### Post by danielrs on 2010-08-10
Usually random is a nice explanation, but this time it happened on 5 computers at the same time

---

### Post by baddnady23 on 2010-08-10
Ah then I think catastrophic is the word your looking for.  :) Def a problem with the server then.  Hopefully we can soon find a resolution!

---

### Post by RobertSwipe on 2010-08-14
This has started happening to me in the last couple of weeks. Never had a problem with printing before - it's always worked out of the box.

Using HP Deskjet 1300, and so far, all suggestions here have failed to get it going again. I've:
- Removed the printer, added it again
- Installed hplip-gui, stopped & restarted the printer
- Checked that the printer is enabled in cups

I'm sure it's an update that's caused this - I noticed a raft of cups updates a while ago but because this particular printer is only used a couple of times a month, it's only in the last week or two that I've been unable to print.

Next effort is to uninstall printer, move it to a new USB socket, reboot, reinstall and hope....

---

### Post by RobertSwipe on 2010-08-14
PS Just updated my profile - I'm actually using Lucid. :-)

---

### Post by bovinius on 2010-09-02
first check that you have enabled the printer :
[COLOR=Blue]System > Administration > Printing[/COLOR]
right click on you printer
click on '[COLOR=Blue]Set as Default[/COLOR]' if it is not already set as such
click on '[COLOR=Blue]Properties[/COLOR]'
click on '[COLOR=Blue]Policies[/COLOR]'
make sure the '[COLOR=Blue]Enabled[/COLOR]' box is checked.
click on '[COLOR=Blue]Apply[/COLOR]'
close out the box entirely and [COLOR=Green]try to print.[/COLOR]

if this fails then open a terminal and type in '[COLOR=Blue]hp-probe[/COLOR]'  without the quotes.
When asked,  enter the number that corresponds to your printer.
Wait about ten seconds and it will return the URI of your printer,
copy the line up to the end of the URI itself for example ...,
[COLOR=Red]hp:/net/Photosmart_C7200_series?ip=192.168.0.195[/COLOR]

goto [COLOR=Blue]System > Administration > Printing[/COLOR]  (again)
right click on the printer you want (again)
select '[COLOR=Blue]Properties[/COLOR]'
select 'Settings' if it is not already there
click on '[COLOR=Blue]Change[/COLOR]' at the Device URI box
paste in the URI as obtained from the hp-probe output
click on '[COLOR=Blue]Apply[/COLOR]'
close out the box entirely
[COLOR=Green]you should now be able to print[/COLOR]
*you should also be able to scan without a problem using xsane or simple-scan if your printer has a scanner.*

---

### Post by pwebster25 on 2010-10-12
I was so hopeful that this would work.  Unfortunately it didn't work for me.  Mine seems to think the printer is disconnected (an HP Color LaserJet cp2025dn).  It was working great.  I am in a windows school environment and the CLJ is connected on the network.  
My URI is: 
dnssd://HP%20Color%20LaserJet%20CP2025n%20(MMS%20Library)._pdl-datastream._tcp.local/
or
hp:/net/HP_Color_LaserJet_CP2025dn?ip=10.1.64.133

Neither works.  It seems to think it is disconnected.  Other machines can print to it (a couple windows machines and a karmic server).

Since it was working great and I also lost network print capability to a networked Brother HL5250DN at the same time I suspect it was a CUPS update or something.  My HP printer setup is a bit odd, as this is a laptop and is connected to an AD domain via Likewise Open.  So, my domain account goes back and forth to home and work every day.  I still use my domain account outside the domain at home.

At home I am connected to another HP printer Officejet 6500.  It works great in Linux as well.  However, since the computer can't find it while I'm at work, it might throw an error, causing something to go wrong with another printer further down the line.

I have reinstalled CUPS and HPLIP.

Any more ideas?  Not sure where I should report the bug?  HPLIP?  CUPS?

---

### Post by RoxieCarpenter on 2010-10-13
> **bovinius said:**
> first check that you have enabled the printer :
[COLOR=Blue]System > Administration > Printing[/COLOR]
right click on you printer
click on '[COLOR=Blue]Set as Default[/COLOR]' if it is not already set as such
click on '[COLOR=Blue]Properties[/COLOR]'
click on '[COLOR=Blue]Policies[/COLOR]'
make sure the '[COLOR=Blue]Enabled[/COLOR]' box is checked.
click on '[COLOR=Blue]Apply[/COLOR]'
close out the box entirely and [COLOR=Green]try to print.[/COLOR]

if this fails then open a terminal and type in '[COLOR=Blue]hp-probe[/COLOR]'  without the quotes.
When asked,  enter the number that corresponds to your printer.
Wait about ten seconds and it will return the URI of your printer,
copy the line up to the end of the URI itself for example ...,
[COLOR=Red]hp:/net/Photosmart_C7200_series?ip=192.168.0.195[/COLOR]

goto [COLOR=Blue]System > Administration > Printing[/COLOR]  (again)
right click on the printer you want (again)
select '[COLOR=Blue]Properties[/COLOR]'
select 'Settings' if it is not already there
click on '[COLOR=Blue]Change[/COLOR]' at the Device URI box
paste in the URI as obtained from the hp-probe output
click on '[COLOR=Blue]Apply[/COLOR]'
close out the box entirely
[COLOR=Green]you should now be able to print[/COLOR]
*you should also be able to scan without a problem using xsane or simple-scan if your printer has a scanner.*

Thank you bovinius! This totally worked for me for my HP Officejet Pro L7780. The intitial install via HP Toolbox asked me to set the wireless up first by usb connect but that did not work. What it did do was change my URI settings to usb. By setting that to /net/ with the ip address everything started working. Thanks for the save.

---

### Post by sisterdorothy on 2011-01-18
Bovinius, I installed an HP LJ 1320 in our workroom today, set it up and worked fine with 5 computers on our network. A few hours later, it wouldn't print.  I checked the things you suggested, and all seemed as they should be.  When I did 'hp-probe' in the terminal, though, it said no usb devices were found (on the computer where printer was installed/shared).  So I turned the printer off and back on, and then ALL the computers could print on the printer.  Kind of weird... thought one more experience might demonstrate just how weird this error is.

---

### Post by dsjstc on 2011-01-19
Are you in the "lp" group?

---

### Post by UbunutuNZ on 2011-01-24
I just had this problem. My printers usb cable wasn't plugged in. Goes fine now.

---

### Post by TodoInTX on 2011-07-29
I just had this problem connecting to an HP OfficeJet J4680 wireless printer.  Turning off and on the wireless network for the printer resolved the problem.

---

### Post by CrimpJiggler on 2011-09-05
> **pwebster25 said:**
> I was so hopeful that this would work.   Unfortunately it didn't work for me.  Mine seems to think the printer is  disconnected (an HP Color LaserJet cp2025dn).   I have this exact problem right now. Its on and off, sometimes I can print for about 5 minutes but then it stops working and it tells me the printer status is:
> /usr/lib/cups/backend/hp failedheres what it says when I run hp-probe:
> Enter number 0...2 for connection type (q=quit, enter=usb*) ? 1

Using connection type: net


--------------------
| DEVICE DISCOVERY |
--------------------

Probing network for printers. Please wait, this will take approx. 10 seconds...

warning: No devices found on the 'net' bus. If this isn't the result you are expecting,
warning: check your network connections and make sure your internet
warning: firewall software is disabled.
which doesn't make sense because I can detect the printer just fine with nmap. Did anyone here manage to fix this problem?

EDIT: I can stop and start the printer with hp-toolbox so it obviously can detect it so I don't know what the hell the problem is here.

---

### Post by pwebster25 on 2011-09-05
I ended up resolving my problem at work by installing the hp network printer on a ubuntu server I have connect to the network by ethernet and then sharing the printer out.  It then works fine on my ubuntu laptop (printing via the cups server).  It shouldn't work this way but it does.  I have a hunch that when my network tech set up the printer that he made it so that regular machines couldn't discover it on the network, as most users connect to it as a shared out install on a windows server.

At any rate it works for me this way.  Another alternative is that the ip address to print to this printer is not the same as the IP address that it identifies as its own.  I have experienced this with a Xerox networked copy machine where it's IP address was not the same as the IP address that it made public to print to.  I don't understand this but that is what seems to happen.

---

### Post by CrimpJiggler on 2011-10-05
Going into System > Administration > Printing and deleting the printer then readding it seems to fix the problem temporarily.

---

### Post by Wim Feijen on 2011-11-22
> **benson444 said:**
> I think that was the error I had a couple of days ago.

Try opening the printer settings (System -> Admin -> Printing), then right-click the printer and choose properties. Click on Policies, on the left, and make sure the State Enabled check box is checked.
Benson, thanks, that worked for me! 

Wim

---

### Post by MWt on 2011-11-28
I had a similar problem with HP LJ P2055dn working as a net printer via Ethernet. After trying to print anything the info from CUPS was e.g. [FONT="Courier New"]held since Mon 28 Nov 2011 09:36:39 AM CET "/usr/lib/cups/backend/hp failed"[/FONT].

As suggested by bovinius, I used hp-probe to check device URI's, and I changed the device URI from the original (automatically set up, was working quite well for some time)
[FONT="Courier New"]hp:/net/HP_LaserJet_P2055dn?zc=NPIC77DCD[/FONT]
to
[FONT="Courier New"]hp:/net/HP_LaserJet_P2055dn?ip=172.30.0.123[/FONT]
and now it works again (so far).

---

### Post by shayno90 on 2011-12-05
tail -f /var/log/cups/error_log
D [05/Dec/2011:12:44:40 +0000] [Job 81] Before copy_setup - %%BeginSetup
D [05/Dec/2011:12:44:40 +0000] [Job 81] STATE: -connecting-to-device
D [05/Dec/2011:12:44:40 +0000] [Job 81] STATE: -media-empty-error,media-jam-error,hplip.plugin-error,cover-open-error,toner-empty-error,other
D [05/Dec/2011:12:44:40 +0000] [Job 81] prnt/backend/hp.c 625: ERROR: 5012 device communication error!
D [05/Dec/2011:12:44:40 +0000] [Job 81] Backend returned status 4 (stop printer)
D [05/Dec/2011:12:44:40 +0000] [Job 81] Printer stopped due to backend errors; please consult the error_log file for details.
D [05/Dec/2011:12:44:40 +0000] [Job 81] End of messages
D [05/Dec/2011:12:44:40 +0000] [Job 81] printer-state=5(stopped)
D [05/Dec/2011:12:44:40 +0000] [Job 81] printer-state-message="/usr/lib/cups/backend/hp failed"
D [05/Dec/2011:12:44:40 +0000] [Job 81] printer-state-reasons=paused

Resolved based on a previous poster's advice of going to
System--->Administrator--->Printing

Right click on your chosen printer and make sure the 'Enabled' state is checked.

Printer finished processing all print requests straight away.

---

### Post by Rgibbons on 2012-01-28
> **shayno90 said:**
> tail -f /var/log/cups/error_log
D [05/Dec/2011:12:44:40 +0000] [Job 81] Before copy_setup - %%BeginSetup
D [05/Dec/2011:12:44:40 +0000] [Job 81] STATE: -connecting-to-device
D [05/Dec/2011:12:44:40 +0000] [Job 81] STATE: -media-empty-error,media-jam-error,hplip.plugin-error,cover-open-error,toner-empty-error,other
D [05/Dec/2011:12:44:40 +0000] [Job 81] prnt/backend/hp.c 625: ERROR: 5012 device communication error!
D [05/Dec/2011:12:44:40 +0000] [Job 81] Backend returned status 4 (stop printer)
D [05/Dec/2011:12:44:40 +0000] [Job 81] Printer stopped due to backend errors; please consult the error_log file for details.
D [05/Dec/2011:12:44:40 +0000] [Job 81] End of messages
D [05/Dec/2011:12:44:40 +0000] [Job 81] printer-state=5(stopped)
D [05/Dec/2011:12:44:40 +0000] [Job 81] printer-state-message="/usr/lib/cups/backend/hp failed"
D [05/Dec/2011:12:44:40 +0000] [Job 81] printer-state-reasons=paused

Resolved based on a previous poster's advice of going to
System--->Administrator--->Printing

Right click on your chosen printer and make sure the 'Enabled' state is checked.

Printer finished processing all print requests straight away.

I had the same problem, but mine was already enabled. I disabled it, click apply, then re-enabled it and clicked apply again. Suddenly everything started printing.

---

### Post by zenga11 on 2012-02-24
On Ubuntu 11.10 (oneiric), I do not have the *System--->Administrator--->Printing* menu and the system settings showed the printer as Off and could not switch On.  So reverting to a terminal window I did the following 

[FONT="Courier New"]$ **lpstat -p**
printer HP-Color-LaserJet-2605dn disabled since Fri 10 Feb 2012 12:31:50 PM MST -
	/usr/lib/cups/backend/hp failed
printer HP-LaserJet-Shared is idle.  enabled since Sat 18 Feb 2012 08:53:21 PM MST
$ **sudo cupsenable HP-Color-LaserJet-2605dn**
$ **lpstat -p**
printer HP-Color-LaserJet-2605dn is idle.  enabled since Fri 24 Feb 2012 12:06:47 PM MST
	ready to print
printer HP-LaserJet-Shared is idle.  enabled since Sat 18 Feb 2012 08:53:21 PM MST
$ [/FONT]

---

### Post by computerwiz908 on 2012-03-01
> **TodoInTX said:**
> I just had this problem connecting to an HP OfficeJet J4680 wireless printer.  Turning off and on the wireless network for the printer resolved the problem.

That fixed it for me on my J4680 as well. Thanks for the advice!

---

### Post by rubensmatos on 2012-03-17
I solved this problem clicking "Resume Printer" in the CUPS printer administration page.

See: [https://bbs.archlinux.org/viewtopic.php?id=85454](https://bbs.archlinux.org/viewtopic.php?id=85454)

---

### Post by Rrory on 2012-04-14
As a newbie with the very same problem. I deleted my printer on one computer and now it can't find the network.

I still have my printer HP 6500E709n on my other computer, but in Ocelot there is no sytems - admin anymore. So I'm confused as to what to do.

Can anyone help me; and keep it simple. I've never had this problem before my printer always worked great with ubuntu.
rory

---

### Post by Mjchopperboy on 2012-07-02
I had the same problem, and here is what I did : open the printing settings and right click printer and select "properties".
Once in properties, check the entered IP for the printer at the very end of the "device URI" text box. Check if it is the same on your printer (wired summary in printer options). If it isn't, change it in the textbox.
Note : This only works on printers with screens that are connected by network.

---

