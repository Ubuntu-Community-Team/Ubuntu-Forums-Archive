---
title: "What to do if printer driver not available?"
date: 2009-11-24
forum: General Help
---

### Post by stuart-b on 2009-11-24
Hi Guys,

We are trying to get working two types of label printers, but have _no_ joy with any PPD or Linux drivers, and the printers do not install properly within Ubuntu (no driver).

They are Bixolon/Samsung printer(s), both the SRP-770ii and the SRP-350 (which Bixolon says works with CUPS, load of crap).

The label printers are attached to a Windows machine, but in order to add the printer to the linux server (and then allow  lpr commands to send a generated file to the printer) we require the driver(s) ?

So my question is:-

- Can we some how create a driver?  If so, how?  I saw something on the internet regarding driver generation.

- How can we send a printer file via LPR to the shared printer without needing a linux driver?

If you have a commerical product/service able to solve this problem, I will be interested also.

Thank you for your time,

Stuart

---

### Post by Arup on 2009-11-24
The best.....[www.turboprint.info](www.turboprint.info) works with all, you need to shell out $30. I had to for my stupid Canon printer.

---

### Post by stuart-b on 2009-11-24
Hi,

Thanks for your reply.

Unfortunately they do not support label/receipt printers for a POS environment, which is causing us the biggest problem.

---

### Post by Arup on 2009-11-24
Unfortunately Turbo Print is the only solution in Linux world.

---

### Post by stuart-b on 2009-11-24
Is it not possible to mount a samba printer from a Windows box and push a file to that Windows box without having the printer actually installed in Linux?

For example, say I have a file called   print_document.txt

Could I run a command such as

#ldr://10.0.1.100/printer print_document.txt

Is this even possible?  If so, it would solve my problem for the moment at least on one project.

Has anyone here got any experience with label/receipt printers with Linux?

Thanks,

---

### Post by Arup on 2009-11-24
[http://ubuntuforums.org/showthread.php?t=347730](http://ubuntuforums.org/showthread.php?t=347730)

See if this works for you.

---

### Post by stuart-b on 2009-11-24
Thanks, will take a look and get back to you.

---

### Post by stuart-b on 2009-11-24
Arup, this may work after some playing around for the machines with XP and the label printers.  Will give it a go tonight.

Regarding printing direct from Linux on to a receipt printer, I guess I won't have any luck unless I find a receipt print supporting Linux?

I've tried the generic drivers and having no joy.

This is really a PITA!

I appreciate your help.

---

### Post by Arup on 2009-11-24
I can well relate to that, I bought a costly Canon photo printer to find out much to my chagrin that Canon doesnt' make any Linux drivers so I had to get the Turbo Print drivers on top of that.

---

### Post by stuart-b on 2009-11-24
Arup,

Seems the best option for us is to sell the label printers we've bought and then buy Zebra printers and set up our application to generate a ELP2 file.

I've read the programmers manual and it seems straight forward enough, especially printing ASCII for basic receipts and labels.

The Linux CUPS system supports a generic "ELP2 Zebra" printer, so this seems the most logical way to go.

Then we will issue a raw command to the printer via lpd, sending the generated ELP2 file.

Oh well, got there in the end... seems the best solution, but not the cheapest. :)

Thanks for your time.

---

### Post by Arup on 2009-11-24
stuart-b,

Good luck.

---

### Post by mbeach on 2009-11-24
> **stuart-b said:**
> Arup,

Seems the best option for us is to sell the label printers we've bought and then buy Zebra printers and set up our application to generate a ELP2 file.


I was just about to respond to say that I use zebra printers for printing price tags in a retail environment and they generally work quite well - I've got them hooked up to little usb print servers which are typically what causes issues.

PM me if you want a good supplier and you happen to be in Canada.

edit:
I'm surprised you can't send raw data somehow to those printers with embedded escape sequences, as I thought you can with the Epson thermal receipt printers. It has been awhile since I had to do anything with those as they have been working for years without issue (the Epsons).

---

### Post by stuart-b on 2009-11-24
> **mbeach said:**
> I was just about to respond to say that I use zebra printers for printing price tags in a retail environment and they generally work quite well - I've got them hooked up to little usb print servers which are typically what causes issues.

PM me if you want a good supplier and you happen to be in Canada.

mbeach, thanks for your reply.

We are based in the UK.

The plan will be to either set up the label printers on the PCs via USB (Windows or Linux), then share the printer.  The Linux server which runs our software will then connect to the printer via SMB -> adding the printer as a generic ELP2 printer.  Then we will issue the command: ldr -o raw printer_share_name file.elp2 (or something similiar).     We then avoid the need to run network usb print servers (this might help you too).

Cheers,

---

### Post by mbeach on 2009-11-24
I would think if you could get the code manual from:
[http://www.samsungminiprinters.com/_eng/download_center/downloadsub.asp?p_uid=5](http://www.samsungminiprinters.com/_eng/download_center/downloadsub.asp?p_uid=5)
it would highlight what you might need to do - I'm trying to get it but it doesn't want to serve up the English version for some reason - I got the French one, but my my vocab is limited to asking how to get to the downtown. 

If I remember correctly, I have them setup with raw text drivers but they are connected directly to the network. I think you send the raw stream to the device, it will likely do what you want (I'm thinking now back to the days where I sent raw pcl streams to my cheque printers with the characters for the account line).

I suspect, especially if you have access to the pos source, that your routines for sending the labels will have to rely on some template, populate with the necessary information, and send the raw file to the device (on whatever path it takes to get there). You may have to set it to RAW instead of LPR in your windows setup in order to accomplish this. That is a bit of a guess. 

I'd approach it by connecting the printer directly to a linux machine, get some sort of output by copying some data directly to it, just to see if it is capable, then worry about how you are going to share it through windows.

---

### Post by stuart-b on 2009-11-24
Mbeach, 

Thanks,

Yes I have set it up on Linux first - then gone through the process of adding the printer.

I am currently working with an SRP-350 (samsung/bixolon) and have tried all manner of generic drivers/epson drivers, but most of it comes out in gobledey gook - just random characters.  

I've tried ESC/9 DOT matrix drivers, Epson, Text-only... all of it comes out crap.  The only one that sort of worked (very badly, not production usable) was 24 line Epson drivers.

I'm running an Ubuntu 9.10 server... latest SMB + CUPS... any ideas you have would be good, as I've just bought another Zebra label printer and I could do with getting the SRP-770ii working without forking out on Zebras to replace those...

---

### Post by Leberyo on 2009-12-08
I've got a very similar issue with an older (serial only) Citoh S4 tag printer.  Pulling my hair out to try to find a solution.  It just doesn't work though.  I've had to go back to windows to make it work.

---

