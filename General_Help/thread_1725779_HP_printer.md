---
title: "HP printer"
date: 2011-04-10
forum: General Help
---

### Post by Nicolab on 2011-04-10
Hi 
I have recently bought a printer **hp desk jet d1663** but I can not print with ubuntu 10.04. The computer recognition the printer and it say printer ready to print but then it does not print. What can I do?

Thanks for any suggestion

Nico

---

### Post by benlyboy on 2011-04-10
Hi
 
I guess the first thing to ask is do you know the printer is working, it wouldn't be the first time something new didn't work right out of the box...

---

### Post by Nicolab on 2011-04-10
Yes it work I try to install it on a widows 7 and it worked. 
Thanks for your reply

Nico

---

### Post by benlyboy on 2011-04-10
So what is happening when you try to print?

Do you get an error message?

Have you tried a test page or just been trying to print from a application?

You may need to update the driver, but I wouldn't rush into this till you rule out everything else, as you say that ubuntu recognised the printer it would seem that the driver is ok.  

But if you do need to do this, this page may help.

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=buu00659&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=th&product=3837084]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=buu00659&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=th&product=3837084")

---

### Post by Nicolab on 2011-04-11
So what append is this:
ubuntu recognize the printer
when I try to print a document it sow the icon saying "one document is queued" then the icon disappears
and that is all.

what do you think?

---

### Post by Nicolab on 2011-04-12
> **benlyboy said:**
> So what is happening when you try to print?

Do you get an error message?

Have you tried a test page or just been trying to print from a application?

You may need to update the driver, but I wouldn't rush into this till you rule out everything else, as you say that ubuntu recognised the printer it would seem that the driver is ok.  

But if you do need to do this, this page may help.

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=buu00659&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=th&product=3837084](http://h10025.www1.hp.com/ewfrf/wc/document?docname=buu00659&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=th&product=3837084)

Hi I went to the web site and I followed the instruction to upgrade the drivers I followed the steps and now I have them in my desk top but I can't open it so I followed the suggestion to open terminal etc. etc. but of course it does not work any way what I typed is here below:

root@nicola-laptop:/home/nicola# cd Desktop
root@nicola-laptop:/home/nicola/Desktop# sh hplip-11.3a.run
sh: Can't open hplip-11.3a.run
root@nicola-laptop:/home/nicola/Desktop# 

what is wrong with this? is there any hope to run that document?

please help
thanks
Nico

---

### Post by leeagt on 2011-04-12
> **Nicolab said:**
> Hi I went to the web site and I followed the instruction to upgrade the drivers I followed the steps and now I have them in my desk top but I can't open it so I followed the suggestion to open terminal etc. etc. but of course it does not work any way what I typed is here below:
 
root@nicola-laptop:/home/nicola# cd Desktop
root@nicola-laptop:/home/nicola/Desktop# sh hplip-11.3a.run
sh: Can't open hplip-11.3a.run
root@nicola-laptop:/home/nicola/Desktop# 
 
what is wrong with this? is there any hope to run that document?
 
please help
thanks
Nico
 
Is the file you are trying to run executable ?
 
try chmod +x hplip-11.3a.run
then 
sh hplip-11.3a.run
 
Edit: try installing hplip-gui from the repositories

---

### Post by walt.smith1960 on 2011-04-12
Usually HP is bulletproof.  Here's one easy thing to check, it's an install problem with one Brother printer I have.  System -> Administration -> Printing.  Is your HP printer listed?  If so, right click on the printer icon and select "properties".  Does the Device URI look reasonable? e.g. if your printer is connected with a USB cable, the device URI should look like
```
usb://something
```  If it were networked it might be something like ```
dnssd://something
```There is a "find printer" button which may be helpful.  You can install HPLIP from synaptic. It won't be the latest version but it may be adequate for your purposes.

---

### Post by TexasRussian on 2011-04-12
I had a similar problem with a friends laptop trying to connect to a wireless printer, have you tried fiddleing around in the printer settings in Ubuntu? (System>Administration>Printing)

---

### Post by Nicolab on 2011-04-12
> **leeagt said:**
> Is the file you are trying to run executable ?
 
try chmod +x hplip-11.3a.run
then 
sh hplip-11.3a.run
 
Edit: try installing hplip-gui from the repositories

Thanks for the help but in does not work it say:

root@nicola-laptop:/home/nicola# chmod+xhplip-11.3a.run
chmod+xhplip-11.3a.run: command not found

Sorry what can i do I know I am not a genius in Computer so if you have any other suggestion please be patient.

Thanks
Nico

---

### Post by leeagt on 2011-04-13
You need to type it in exactly. (Notice the spaces between chmod and the +x and space after the +x and hplip
 
chmod +x hplip-11.3a.run

---

### Post by Nicolab on 2011-04-13
> **leeagt said:**
> You need to type it in exactly. (Notice the spaces between chmod and the +x and space after the +x and hplip
 
chmod +x hplip-11.3a.run

No way it does not run let me give you the properties of that file may be there is something wrong with the command.

Name hplip-3.11.3a.run
Type shell script (application/x-shellscript)
Size 21.3 MB (22324298 bytes)
Location /home/nicola/Desktop

maybe this can help to direct me 

thank you any way for your help

---

### Post by benlyboy on 2011-04-15
Sorry was away on business, and haven't looked in on this post for a while


I see you are having trouble installing HPLIP. Have you tried installing it from ubuntu software center?  Just put HPLIP into the search and then install 

Should be that easy :-)

---

### Post by Nicolab on 2011-04-17
Thanks I just install all the HPLIP available in the ubuntu software center and no way the printer inform me that the job is in process and after a while the job is finished, but no printing is done and yet with windows it does print. 
At this point I deduct that she "the printer" does not like me and she is upset because I am using Ubuntu. What do you think about this philosophy.

any other suggestions

Nico

---

### Post by walt.smith1960 on 2011-04-17
> **Nicolab said:**
> Thanks I just install all the HPLIP available in the ubuntu software center and no way the printer inform me that the job is in process and after a while the job is finished, but no printing is done and yet with windows it does print. 
**At this point I deduct that she "the printer" does not like me and she is upset because I am using Ubuntu**. What do you think about this philosophy.

any other suggestions

Nico

:) :)
I've felt like that a few times.  I had similar behavior when my Brother install routine installed as a USB printer even though there was no USB cable connected; the printer had a wireless network connection established.  The print job is sent to a device that didn't exist exist; the job just disappeared.  What do you see when you go to System -> Administration -> Printing?  Is your HP printer listed there?  If so, when you _right_ click the printer icon and select "properties", what do you see?  Here's what mine looks like:
[ATTACH]189291[/ATTACH]
If the device URI were messed up,  I'd have the same problem;  a print job being sent to a nonexistent address.  You may have something else going on but I know an incorrect Device URI will cause your problem.

---

### Post by nicole_c56 on 2011-04-17
I Have a HP Desk jet J1100 series, and I just installed ubuntu 10.10, on this Dell Dimension Desktop .Although Ive been reading other forums, I have tried other configurations and upgrades. But, when it's  printing the single white page, no ink or text. What can I do to get it to work like it did with windows and print normally.

---

### Post by benlyboy on 2011-04-18
mmm seems funny that ubuntu seems to think that the document has been printed. I think I would unplug the printer from the pc and see what happens when you try to print. If it still seems to print this would indicate that it is printing to something other than the printer,(maybe a file). How ever if it tells you the printer is unavailable then you know it is printing to your printer.

Just a thought have you tried rebooting the printer...the best way i have found to do this is to unplug it from everything including the power and leaving it a few minutes befor retring it...

---

### Post by Nicolab on 2011-04-18
> **walt.smith1960 said:**
> :) :)
I've felt like that a few times.  I had similar behavior when my Brother install routine installed as a USB printer even though there was no USB cable connected; the printer had a wireless network connection established.  The print job is sent to a device that didn't exist exist; the job just disappeared.  What do you see when you go to System -> Administration -> Printing?  Is your HP printer listed there?  If so, when you _right_ click the printer icon and select "properties", what do you see?  Here's what mine looks like:
[ATTACH]189291[/ATTACH]
If the device URI were messed up,  I'd have the same problem;  a print job being sent to a nonexistent address.  You may have something else going on but I know an incorrect Device URI will cause your problem.

This is what appear in the URI:
hp:/usb/Deskjet_D1600_series?serial=CN06ECB3MW05CT

do you think it is OK?

---

### Post by Nicolab on 2011-04-18
> **benlyboy said:**
> mmm seems funny that ubuntu seems to think that the document has been printed. I think I would unplug the printer from the pc and see what happens when you try to print. If it still seems to print this would indicate that it is printing to something other than the printer,(maybe a file). How ever if it tells you the printer is unavailable then you know it is printing to your printer.

Just a thought have you tried rebooting the printer...the best way i have found to do this is to unplug it from everything including the power and leaving it a few minutes befor retring it...
I try to print with the printer unplugged it say 1 document queued and if I click on the icon it open a windows and it is written  pending

---

### Post by CoolJohnB on 2011-04-18
I had the same problem with my HP printer I cured it by un-installing all the HPLIP drivers etc. unplugged the printer, plugged it back into the computer and hey presto it sorted itself out and gave me a working printer no problems.

---

### Post by benlyboy on 2011-04-18
Mmm seems strange that ubuntu seems to think the page has been printed. It might be interesting to disconnect the printer from the system and try and print.
If it still acts as if it has printed the page it may be printing to something other than the printer ( maybe it's printing to a file).
However if you get a message along the lines of "Printer is unavailable" then you can be pretty sure that it is printing to your printer.

Just a thought, but have you tried to reboot the printer. To do this and be sure I have found that you need to turn it off then disconnect it from both the USB and the power, leave it a couple of minutes before reconnecting it (just turning it off will not always reset everything)

---

### Post by Nicolab on 2011-04-22
> **benlyboy said:**
> Mmm seems strange that ubuntu seems to think the page has been printed. It might be interesting to disconnect the printer from the system and try and print.
If it still acts as if it has printed the page it may be printing to something other than the printer ( maybe it's printing to a file).
However if you get a message along the lines of "Printer is unavailable" then you can be pretty sure that it is printing to your printer.

Just a thought, but have you tried to reboot the printer. To do this and be sure I have found that you need to turn it off then disconnect it from both the USB and the power, leave it a couple of minutes before reconnecting it (just turning it off will not always reset everything)
By reboot you mean I go to System - Administration  -  Printing and then I delete the printer, then I connect the printer to the computer switch on the printer and let Ubuntu install it. Is it that what you mean by reboot?

If Yes I did and no way the same problem.
thanks any way for your help

---

### Post by walt.smith1960 on 2011-04-22
> **Nicolab said:**
> This is what appear in the URI:
hp:/usb/Deskjet_D1600_series?serial=CN06ECB3MW05CT

do you think it is OK?

I haven't checked this thread in a while, sorry.  Yes, that address looks fine to me.  Based on an experience I just had with a Canon scanner, you might try to create a new user just for this purpose and try to print from there or from an infrequently used account.  The Canon scanner got some messed up setting that I couldn't find.  Happily it was a rarely used account so I  deleted the problem account, created another and the scanner resumed functioning properly.

---

### Post by Nicolab on 2011-04-23
> **walt.smith1960 said:**
> I haven't checked this thread in a while, sorry.  Yes, that address looks fine to me.  Based on an experience I just had with a Canon scanner, you might try to create a new user just for this purpose and try to print from there or from an infrequently used account.  The Canon scanner got some messed up setting that I couldn't find.  Happily it was a rarely used account so I  deleted the problem account, created another and the scanner resumed functioning properly.
Thanks I did so but no good results do I need to reinstall the printer in the new user account?

---

### Post by apochry on 2011-04-23
Hi Nico,
do you have CUPS (Common UNIX Printing System) installed? If so you could try setting up the printer there. My HP Deskjet works just fine with it.

---

### Post by Nicolab on 2011-04-24
> **apochry said:**
> Hi Nico,
do you have CUPS (Common UNIX Printing System) installed? If so you could try setting up the printer there. My HP Deskjet works just fine with it.
Yes I have but how do I set the printer there can you help me in that?

thanks

---

### Post by apochry on 2011-04-24
Hi Nico,

first make sure your printer is connected (it's via USB in your case, isn't it?).
Go to your web browser and enter ```
localhost:631
```
Go to 'Administration'-Tab and hit 'Add Printer'. Than CUPS will search probably find your printer. This is what it looks like on my system:
 [img]http://imgur.com/08uek.png[/img]
The second one is the one I want. Select your right one and go on.
Than you should be asked for some details (Name /Description/etc.).
On the next page select the driver for your model. I have CUPS 1.4.4 and I saw that a driver named "HP Deskjet d1600 Series, hpcups 3.11.3a (a)" is provided. This one should work fine for your printer. Add the printer, select your "Default Options" and you are good to go.
Now try to print a Test Page. This is done under the 'Administration'-Tab --> 'Manage Printers' --> select printer to be managed --> 'Maintenance'-Drop-down menu.

I hope this will help.

Regards,
Izzo

---

### Post by Nicolab on 2011-05-01
> **apochry said:**
> Hi Nico,

first make sure your printer is connected (it's via USB in your case, isn't it?).
Go to your web browser and enter ```
localhost:631
```Go to 'Administration'-Tab and hit 'Add Printer'. Than CUPS will search probably find your printer. This is what it looks like on my system:
 [IMG]http://imgur.com/08uek.png[/IMG]
The second one is the one I want. Select your right one and go on.
Than you should be asked for some details (Name /Description/etc.).
On the next page select the driver for your model. I have CUPS 1.4.4 and I saw that a driver named "HP Deskjet d1600 Series, hpcups 3.11.3a (a)" is provided. This one should work fine for your printer. Add the printer, select your "Default Options" and you are good to go.
Now try to print a Test Page. This is done under the 'Administration'-Tab --> 'Manage Printers' --> select printer to be managed --> 'Maintenance'-Drop-down menu.

I hope this will help.

Regards,
Izzo
  ThanksI have followed the steps but I did not find the drivers hpcups 3.11.3a (a) but I found    	 	 	 	p { margin-bottom: 0.08in; }  Hp Deskjet d1600 series, hpcups 3.10.2 (en) therefore it did not work. any other suggestions.
thanks
Nico

---

