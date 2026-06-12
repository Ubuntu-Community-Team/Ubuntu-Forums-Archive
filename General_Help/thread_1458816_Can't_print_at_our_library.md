---
title: "Can't print at our library"
date: 2010-04-20
forum: General Help
---

### Post by cmcanulty on 2010-04-20
I convinced our librarian to let me put Ubuntu on our public computers a year ago. However everyone is really upset as printing is a constant problem. Soon Ubuntu will go and windows will be back if I can't solve this soon. I have tried lots of tweaks with no luck. I am not a computer or Linux professional but am pretty knowledgeable on tech although a bit weak with command line tasks.Karmic  can print test pages but rarely pdf, office, or web pages. I constantly uninstall and reinstall the printer. We use a print server and several laptops share the printer. All run Ubuntu 9.10 and all are up to date. When I check the print queue all jobs are being held even though I have it set to no hold.Occasionally something will print.I also have an XP machine and an Apple but have about given up on ever getting them to print though the printer does get found by both of them.We are lucky that they let me put Ubuntu on these machines but unless this is solved soon Ubuntu will be history here. What I really need is to talk to someone while I am at the library and see is this can be fixed in a step by step manner. I am there Thurs by 1pm eastern time USA daylight savings time. Though I could be there by noon if that would help. We open at 3pm and after that it is really hard to get exclusive use of the computers.If anyone can call me there on Thurs we can set up a time. Also I could call out by Magic Jack phone if it would save someone a long distance call. The Magic Jack is quite unreliable.We are getting Charter with long distance in 2 weeks but everyone is on my case to get this fixed before that. I am a volunteer. Also if another day would work I could maybe schedule that but I do volunteer other places at set hours. Thank you and I really hope someone will take the time as I really like Ubuntu and hate windows. I don't want to go back to windows. I have done lots of reading, research,and web searches trying to solve this with no luck.reinstalling the printer on all the machines will maybe make it work for a few documents but not even that works much.

---

### Post by mike555 on 2010-04-20
More info would help, what make printer, server, etc.

---

### Post by cmcanulty on 2010-04-20
The printer is an HP Laserjet 2100m. The server I believe is a desktop either gateway or dell about 5 years old I'm guessing. It is a print server only, not a system server. I also wonder about no print server and just ethernet to the wired network? We can't attach directly to router or switch as they are in a utility room and the printer needs to be accessible to all.The printer works fine when it prints but something is definitely screwed up in the configuration. Possibly something I have done wrong.Although sometimes it prints fine. Pdf is a huge problem and seems to completely hang it up. Though it did pdfs fine with windows before we switched over. I am not sure what else you need to know. I think it is something wrong in my CUPS setup but just a guess.

---

### Post by cmcanulty on 2010-04-21
Please someone call me at the library tomorrow (Thursday April 22) 12-7pm edt best is 12-3 before we open 231-882-4037 or leave me a number to call. I really need this fixed so we can print at the library. We are all run by volunteers.This is a very small town.

---

### Post by Mark Phelps on 2010-04-21
> **cmcanulty said:**
> I convinced our librarian to let me put Ubuntu on our public computers a year ago. However everyone is really upset as printing is a constant problem...

Maybe they're upset because they don't share your hatred of MS Windows and simply want something that works -- including printing.

Did the printing work before and only now fails because this is a new printer? Or has this printing problem been the case all along?

---

### Post by cmcanulty on 2010-04-21
No it worked fine with windows and at first it worked with Ubuntu sometimes pdfs failed but now all jobs except test pages are held forever and won't release. Hold option is off though. I really need someone to talk me through this at the site tomorrow. It is a Ubuntu print server and several laptops that access it. They see the printer and when you try to print it sits in queue forever. I gave up on the mac and windows machines ever printing to it while it is attached to a Ubuntu machine, but we need the Ubuntu machines to print for our patrons.A miracle would be if all machines printed to it.I agree they just want something that works. Surprising that few other problems with Ubuntu but this is a big one and could be decisive.

---

### Post by marshag63 on 2010-04-21
Do you use the cups web interface?

If each computer can access the cups web interface for the printer, you might find out more info, i.e., like which and how many computers can administer the printer, etc.  

I suggest following the setup for 9.04 print server here:  [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

Cups:  
[http://www.cups.org/articles.php?L274+TFAQ+Q](http://www.cups.org/articles.php?L274+TFAQ+Q)

Also:

[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)


I wish you well.

MarshaG.

---

### Post by cmcanulty on 2010-04-23
OK after more study and screwing around with it here is some diagnostics. I tried to get at the printer error log but nothing came up even though I have it set to save all debugging info. Currently it is hooked to the print server by parallel cable. It is also cabled to wall port with ethernet. I have tried unplugging both of them one at a time and then nothing finds the printer. After reading above though maybe since it is parallel ported to a print server I should be not setting it as a network printer but as a local shared one. I really don't know.If I just have it ethernet cabled to wall I don't know how to access it to get it's IP address. I do have the print server set to a static ip address. I have a jet direct CD should I install that on the print server or all the client computers too. I doubt if it has a linux driver on the cd. After I delete all the printers on all the computers and reinstall starting with the server it works for a short while. Then numerous other printers start to appear in the print config utility on all the computers. All but the original install have names like 192.168 etc and then it won't print anymore. Jobs turn up in the print queue but they all just sit there with either processing or held next to jobs and they never print.It will really upset me if I have to turn the library back to microsoft for such a dumb reason as I can't figure out how to make the machines print. I print at home fine with my Ubuntu but it is a modern USB printer and not shared.If there is a way to set this up and have it stable I really need to know what I am doing wrong. Maybe it is just in error in some basic way that I have missed with lots of studying. Thank you and will someone please help! I think it is so cool to have our library on open source but only if we can print. We have to serve the public and I am a volunteer we have no paid tech staff.Thank you. Again if anyone can set a time to call me at the library and solve this one on one I think it could be fixed.All machines run on Ubuntu 9.10. Is it possible that the problem is networking with a parallel port printer (though it networked fine with XP on the machines).

---

### Post by conradin on 2010-04-23
1, setup printer so it has a static IP. 
2, setup all your computers to print to IP. 
Ill call in just a few moments.

---

### Post by pricetech on 2010-04-23
> **cmcanulty said:**
> . Currently it is hooked to the print server by parallel cable. It is also cabled to wall port with ethernet..

First, lose one or the other.  You have two paths to the printer, both on the network.  It's no wonder your clients can't figure out how to print.

That's probably the reason for all the strays getting added automatically also.

Unless you have a compelling reason to use a print server, use the printer as a network printer and be done with it.

---

### Post by cmcanulty on 2010-04-23
That is what I am trying to do but I don't know what else info I can give I am stuck and don't know what to do. If some one calls I need a few hours notice before as I live 8 miles away and have to bicycle in thank you very much. I am always there on Thurs 1-7pm edt but can arrange a time outside of thurs or earlier on thurs for anyone who can help on this. I feel really stupid that I can't solve this but I can't. I have read everything I can find on linux shared or network printing and am very mixed up. Here is the library phone number 231-882-4037 my home number to arrange a time is 231-882-4734. As I said above I am not a tech pro but a volunteer.

---

### Post by pricetech on 2010-04-23
I don't really need info as much as you do.  First, you'll need the IP of the printer.  Then you'll need to set the printer up on each workstation using that IP.

I'm assuming you don't have a compelling reason for a print server since it doesn't really sound like you do, so disconnect the parallel cable.

---

### Post by cmcanulty on 2010-04-23
OK I have the static ip set up for the print server but I can't seem to get an ip address for the printer as when I disconnect it from the computer it disappears.Or can I get an ip for the printer while it is hooked to the server? and can I set it as a static ip or not for the printer? I coulod arrange to be at the library tomorrow (sat) am from 9 to 1pm est USA if that would work for a call in.

---

### Post by kanikilu on 2010-04-23
I agree with the other suggestions here, if the printer has a JetDirect card, there's no sense in adding the extra layer of complexity by going through a print server, especially if it's the only printer on the network.

That being said, the first thing you need to do is determine what the IP address is of the printer. To check that on a HP LJ 2100, I believe you press the "Go" and "Job Cancel" buttons on the printer at the same time (check the manual if you have it) to print a configuration page.

When you have that, try to ping it, just to be sure it's working - or actually, put the address into a web browser on the same network, and I think you should be able to see the JetDirect web interface.

Once you determine the network link to be good, it should be a simple matter of adding the printer to each client:

- System -> Administration -> Printing
- Server -> New -> Printer
- Under Devices, click Other and in the box provided, type the printer's URI, which should be something like ipp://192.168.1.2 (<-- replace with the IP address of your printer)

---

### Post by conradin on 2010-04-23
Lolz, i just Called, A nice sounding Lady Says the printer issues are solved! +1:guitar:

---

### Post by cmcanulty on 2010-04-23
No they aren't it is the temporary fix that works for a few docs as I reinstalled everything again yesterday. When I press the printer buttons where do I see the address of the printer? It doesn't have an LCD panel on the printer itself.No one there has the slightest clue about tech except me, it is really pretty lame.For example when I was on vacation the XP librarians computer died and no one thought that duh maybe we should save it and try to recover some of our documents.

---

### Post by pricetech on 2010-04-23
Have you checked HP's support site ??  You should be able to find the information there.

You might also download JetAdmin.  It seems the last time I did I had to jump through some hoops to get it, but you might find it helpful.

Only works under windows though, as I recall.

---

### Post by kanikilu on 2010-04-23
When you press the two buttons (again, verify this in the manual, I don't have a 2100 around) it should print out two pages, the first is the printer configuration and the second is the JetDirect configuration.

The address you want should be on the second page, labeled as "IP Address", "Ethernet Address", "IPv4 Address" or something like that...I don't remember the exact terms they use, but it should be pretty obvious. It's not the gateway or subnet mask, so it should be the only other number that looks like "192.168.1.2" (for example).

---

### Post by cmcanulty on 2010-04-23
OK do I do that before or after I remove the parallel cable from the print server? OK I've arranged to be at the library from 850am to 1pm edt tomorrow Sat 231-882-4037 please someone call then and ask for Carol and maybe this can be fixed, thanks all. I really really want Ubuntu to succeed.

---

### Post by conradin on 2010-04-23
> **kanikilu said:**
> When you press the two buttons (again, verify this in the manual, I don't have a 2100 around) it should print out two pages, the first is the printer configuration and the second is the JetDirect configuration.


I have the manual, its the go button and job cancel button.

Ill call in sometime tomorrow then.

---

### Post by cmcanulty on 2010-04-24
Great thanks!

---

### Post by cmcanulty on 2010-04-24
Please call I have it connected to ethernet and installed ppd driver and now get endless streams of garbage pages that won't cancel. I am here at 231-882-4037 and have 6 machines to set up by 1pm thank you Carol

---

### Post by conradin on 2010-04-24
> **cmcanulty said:**
> Please call I have it connected to Ethernet and installed ppd driver and now get endless streams of garbage pages that won't cancel. I am here at 231-882-4037 and have 6 machines to set up by 1pm thank you Carol

what I would try here is powering down the printer, with the power switch, unplug the printer, press the power button again, (to dissipate internal voltages) wait 5 minutes, plug the printer back in, then, while pushing the power button also hold down the Job Cancel button until the printer initializes.

Just thinking, perhaps another post would be good for the library, to ask for local Linux user assistance.

---

### Post by blueridgedog on 2010-04-24
You would do well to cultivate a relationship with the local Linux Users Group:

[http://www.linux.org/groups/](http://www.linux.org/groups/)

You may be able to get assistance closer than you think.

---

### Post by cmcanulty on 2010-04-24
I got a call and got things setup except for a few things 1)how to keep printer as a static ip or is it already static (connected via ethernet to network) 2)how to translate the ip address from the printer into a url or location xp understands to add to the librarians computer 3) how to get mac to find it (we have one mac). Temporarly I have the printer left on to keep the address static it is 192.168.2.150

---

### Post by pricetech on 2010-04-26
Do you have the manual yet ??  Everything should be explained there.

Yes you need to set a static IP.

In XP, when you set up the printer you'll need to add a TCP/IP port with the IP address you set the printer to, then install the driver normally, or just use the existing driver if one is already installed.

I don't have an answer for how to set it up on a Mac since I don't have one and have never used one.  Maybe one of the MacHeads on the forum can help you out with that.  I suspect the procedure is probably similar though.

---

### Post by cmcanulty on 2010-04-27
OK I will try that when I go in Thurs for now we are leaving it on to keep the same addressthanks

---

### Post by conradin on 2010-04-27
What sort of router do you have? You may be able to configure your IP in the local setup. 

Assigning a URL to a printer is not necessary to print to IP.

---

### Post by egalvan on 2010-04-27
> The printer is an HP Laserjet 2100m. 

Does this printer have a separate network card?

HP network cards can be configured via the printer console,
using the printer display.
Or over the network.
Print out the printer properties...
find the section on the network card...
it will give you the information you need,,,
such as network address, type, etc,


So, does this printer have a display that is more than just lights?
Does it have an LCD-type display?

If yes, find the manual for the printer and the card...


Or, try to get XP to auto-discover the printer, using the network connection,
at times this actually works.

---

### Post by pricetech on 2010-04-29
OP said in a earlier post that the printer doesn't have a display.  I'm still not clear on whether it has an embedded Jet Direct or not, but he doesn't indicate that it's external.

The manual should give him all the information he needs on configuring and Web Jet Admin is still available for download if he needs it.

---

### Post by cmcanulty on 2010-05-03
I finally got the Ubuntus, Macs, and windows computers all printing. Thanks to everyone that helped me out.

---

### Post by pricetech on 2010-05-04
How about a rundown of exactly what you did in case someone has a similar scenario in the future.

---

### Post by cmcanulty on 2010-05-04
OK here are things that really were hard to know. First use the jet direct CD to set up the network printer. Use the ip address for location and it will fill in the rest. I got the ip address of the printer by pushing both buttons at once and then the config popped out-that was a crucial step. Then set the printer port as LP1 even though I was leaving the parallel cable off and only using the ethernet cable to a wall port (no computer directly hooked to the printer). Then and this is very weird set it s not shared. On the Ubuntu machines make sure printer is set as available to all. This is with a HP 2100M LaserJet printer but is probably similar for other printers. Oh and either set the ip address as static or leave printer always on so the ip address remains the same or else it won't connect when the ip address changes. I didn't set it as static as I am not familiar with router settings and it works fine with it left on all the time.I hope this saves someone the tons of time I wasted on this printer though now it works with windows XP, Windows 7, Ubuntu 10.04 & 9.10, and a Mac.

---

