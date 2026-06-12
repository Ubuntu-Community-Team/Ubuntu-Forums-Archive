---
title: "Can't print PDF files over network!"
date: 2012-05-11
forum: General Help
---

### Post by Romulo Carlos on 2012-05-11
Hello.

I just upgrade an computer to Ubuntu 12.04. So, it runs an update, and I installed Samba. We use this machine as scanner and print server. A HP J4660 All-In-One is connected via USB. We have a folder shared to everyone, no especial security is required.

I can print via Windows (Win7 Professional, 32 and 64 bits), as well connect via VNC to scan some documents and save them on the shared folder. BUT...

For some reasons, I want to use the print share via "net use" command, but I can't. When I type "net use lpt1: \\computer\printer /persistent:yes", the system give a message saying the command was ok. But when I print, the print job stuck with an error on the Windows computer. I have to cancel the print job.

So, for now we are using the "classic" way to print: we open the computer via "Start -> Run...", right click on the printer, and then click "Connect". Everything working. BUT...

We can print every type of document: photos, DOC/XLS, webpages... but we can't print PDF files!! When we print a PDF file (we use FoxIt Reader), the printer icon appear in the taskbar like a flash, and then disappers. And the printer stay stopped.

The only way to print PDF files is copying the PDF to the shared folder, access the Ubuntu machine with VNC, open the file with "Document Viewer", and then print. In other words: the Ubuntu machine can print everything, and the Windows machines can print all things except PDF files. Even small PDF isn't printed.

Sorry for the long post... but is a very strange problem. Any ideas?? Thanks a lot.

---

### Post by bottleman on 2012-05-11
Hi Romulo, I have the same problem.  

I recently set up an ubuntu 12.04 box with a printer.  After some tribulations (described [here]("http://ubuntuforums.org/showthread.php?t=1971847")), I did get Windows 7 clients printing through this shared printer.  

But oddly enough PDF files will not print from Windows 7! When I request a print, the printer queue icon appears in Windows 7 and it looks like everything is fine.  The printer icon then disappears.  Nothing is there in the CUPS print queue afterwards when I go to check it.  Other types of files print fine from Windows 7.  Linux clients can print PDFs fine.

Not a crisis type of problem for me, but an annoyance for sure.  Cheers..

---

### Post by Romulo Carlos on 2012-05-11
I can confirm to you: is a BUG: [https://lists.launchpad.net/linux-traipu/msg05097.html](https://lists.launchpad.net/linux-traipu/msg05097.html)

As you can see, there is a workaround for the bug. I have tested, and not work for me. Maybe for you it works...

Good look!

---

### Post by strictland on 2012-05-30
There is definitely something wrong with printing files over network in 12.04 LTS. In my case, from Windows 7 PC to Ubuntu Desktop 12.04 LTS (where my printer is hooked up to)

**I can print:** pictures, word documents and web pages just fine from Win 7 to Ubuntu.
**I _cannot_ print:** text files and pdf files of any size from Win 7 to Ubuntu.

However I can print anything directly from within Ubuntu 12.04 LTS.

Has anyone found a fix for this issue?

---

### Post by tazeat on 2012-09-05
Hate to bump an ancient thread, but I'm having the exact same issue. I can print web pages, but pdfs and text files are a no go. I've tried completely purging anything cups related and reinstalling and I've just got no where, has anyone found a fix for this?

---

### Post by tazeat on 2012-09-05
Has anyone figured this out?

All of the jobs seem to end up in /var/spool/samba however I don't see anything in any error log saying it failed. Also nothing shows up in the printer queue when you open it up in System Settings > Printers. 

My printer is hooked up to my ubuntu home "file server" and all of my windows clients in the household (about 10 devices) all regularly print to it, I guess I could just go out and buy a dedicated network usb printer hub, but this is ridiculous I should just be able to share it over samba like I have for the last 10 years...

---

### Post by davidmaree on 2012-09-13
Hi, I also have the same problem and have been trying to solve this for the past month in lubuntu. Everything prints from win 7 to linux printers except pdf files! I have two different printers attached, hp and brother and same problem. From linux pc pdf does print to both.

---

### Post by keithbam on 2012-09-15
Exactly the same problem here. 

Everything except PDFs print via network to Kubuntu 12.04 CUPS/SAMBA shared printer. Same symptoms  from both Windows 7 and Windows XP computers. PDFs print fine on Kubuntu machine itself. Nothing appears in Windows or CUPS print queues/jobs list and I do not recognize any interesting errors in CUPS error log. Printer is an old Kyocera. I tried a variety of printer drivers and they all produce the same results.

I tried the workaround and it didn't work for me.

---

### Post by tazeat on 2012-09-16
Hmm, I wish someone that knew what the hell was going on would poke their head in here. We should all put together a bug report and sign off on it so some of the devs can see this, I'm just not even really sure where to put it.

---

### Post by kallestrup on 2012-10-16
Hey everyone

Same here. No pdf printing via a pdf reader from Win to SambaPrint/Cups.

Semi-Solved: I use a browser for the PDF files.
Like this: file:///F:/docs/businesscase04.pdf or just press f: in the addressbar.

Hobe the works until some sambaexpert solves this issue.

-Kallestrup,DK

---

### Post by Roasting on 2012-10-20
Okay, here goes. After much mucking around with this over last weeks have finally made my Windows 7 laptop print pdfs on a HP Deskjet 460 connected to my media server running 12.04 Precise Pangolin (note: as others have found, the printing has always worked fine with my Vista machine, just problems with machine running Windows 7)

In short, after reading the following: 

"CUPS_printer_sharing#Sharing_via_Samba" over at Wiki.archlinux.org I decided to bin Samba printer sharing and go with IPP sharing as they recommend.

Steps I followed:
(Note - I deleted the Samba printer share in Webmin as first step, but assume this is not required & possibly a bit extreme!)
1) Hit "add a printer" in the control panel of Windows 7 machine
2) Selected "Add a network, wireless or bluetooth printer"
3) Clicked on "printer that I want isn't listed"
4) Selected "select a shared printer by name"
5) Typed in my CUPS printer address (an example: [http://192.168.0.136:631/printers/HP_Deskjet_460](http://192.168.0.136:631/printers/HP_Deskjet_460))
6) I was then asked for a driver to be selected so I selected the HP 460 driver.

Then I opened a pdf file, selected the network printer & crossed my fingers (for about the 200th time in last weeks)[-o< ...the printer squeaked into life & printed. A happy man.

Pls. feedback if this works for others. Also please be aware that I don't really know what I am doing, but over time have got the server pretty much doing what I want it to without completely "melting it" yet, so use the above at your own risk & good luck!

------------------------

N.B. When I initially printed, the colours seemed to be off, so I installed a generic driver - HP Color LaserJet 8500 PS (as advised on the archlinux wiki above - as the CUPS is running a HP Deskjet driver). This initially was not listed so I needed to go into the properties of the "printer" I had just created via Windows control panel, right click, "printer properties", "advanced" tab, "new driver" button, hit "windows update" button, make cup of tea while waiting for update, select driver from long list and hit finish.

It did look to make an initial improvement, however, whether this is really required I am not sure as it looks like my cartridge needs replacing. Will replace it later on and update this with results.

---

### Post by bpb_21 on 2012-12-01
Has this been officially solved yet?  I tried the fix posted earlier in the thread but it didn't appear to work.
I also tried the latest fix in this thread but it also didn't appear to work.
I also updated everything possible on my server; after trying the two fixes above, now nothing will print from my Windows 7 machine.
At some point I'm going to study the log files and get this working.  If I have any luck with that I'll post my results.  I do wish more attention could be paid to this bug (by people who -really- know what they're doing).  Printing PDF files isn't exactly an obscure task!  Any help is welcome.

---

### Post by t-readyroc on 2013-01-08
Any news on this?  Wondering if bpb has figured it out in the last month...

---

### Post by bpb_21 on 2013-01-09
> **t-readyroc said:**
> Any news on this?  Wondering if bpb has figured it out in the last month...

No, unfortunately not.  I've been preoccupied with other things and just resigned myself to only printing PDF files from my (Ubuntu) laptop.  Maybe I'll look at this again in the near future though.

---

### Post by CountMiscount on 2013-02-01
Hi,

just copy the  **following bold lines ** into the the smb.conf file under:

```

[printers]
...
**use client driver = yes**

[print$]
....
**use client driver = yes**

```and then restart samba:

```

sudo /etc/init.d/smbd restart
```at least, that did the trick for me....

---

### Post by CountMiscount on 2013-02-01
I solved this on my machine by:

[http://ubuntuforums.org/showpost.php?p=12486865&postcount=15](http://ubuntuforums.org/showpost.php?p=12486865&postcount=15)

---

### Post by DLew1988 on 2013-02-15
> **CountMiscount said:**
> Hi,

just copy the  **following bold lines ** into the the smb.conf file under:

```

[printers]
...
**use client driver = yes**

[print$]
....
**use client driver = yes**

```and then restart samba:

```

sudo /etc/init.d/smbd restart
```at least, that did the trick for me....

Thank you so much!
Just wanted to confirm that this works like a charm for me.

I'm using Windows 7 Professional to print to a 12.04 machine.

---

### Post by jac_tict on 2013-03-24
> **CountMiscount said:**
> Hi,

just copy the  **following bold lines ** into the the smb.conf file under:

```

[printers]
...
**use client driver = yes**

[print$]
....
**use client driver = yes**

```and then restart samba:

```

sudo /etc/init.d/smbd restart
```at least, that did the trick for me....

THANK YOU VERY MUCH!
It works!

---

### Post by troy7 on 2013-09-29
None of these solutions worked for me.  Before the change, my /var/log/cups/error_log showed:

[28/Sep/2013:11:51:28 -0500] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [28/Sep/2013:11:51:34 -0500] failed to CreateProfile: org.freedesktop.DBus.Error.NoReply[IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/smilies/biggrin.gif[/IMG]id  not receive a reply. Possible causes include: the remote application  did not send a reply, the message bus security policy blocked the reply,  the reply timeout expired, or the network connection was broken.

After applying last solution offered, I get:

E [28/Sep/2013:22:59:36 -0500] Failed to update TXT record for Samsung ML-2510 Series @ Linux8CPU: -2
E [28/Sep/2013:22:59:44 -0500] Failed to update TXT record for Samsung ML-2510 Series @ Linux8CPU: -2


Nothing prints in both cases.  Also, cups doesn't show a new job number in either case.  I can bring the pdf over to Xubuntu and print just fine.

---

### Post by mr.strickland on 2013-11-03
This method partially worked for me. I did some other things in CUPS that probably "fixed" the ***other*** issue I was having.

So I added the lines as advised, saved smb.conf file and restarted samba. Printing PDFs from Windows 7 client finally worked. I restart Ubuntu host to further verify, PDFs would not print again. Restarting samba would fix this. This would mean every time I booted my Ubuntu host, I would have to restart samba in order to print out PDFs from local Windows 7 PCs.

After hours of researching & fiddling with this &*#@, I find myself in CUPS admin panel via [http://localhost:631/admin](http://localhost:631/admin). Under Administration, I go to the Server section and click on "Edit Configuration File", I copy the original config file into a text document for safe keeping and click on "Use Default Configuration File" and save changes. I go back to Administration, then under Server section "Server Settings" I check the box that says "Share printers connected to this system"... save settings and close browser window.

I then go into my Windows 7 client and remove my printer and re-add (don't know why but just decided to). I proceed to print my PDF and it works. I reboot my Ubuntu host to verify again and noticed that printing PDFs doesn't work immediately after boot... I discovered that if I wait about 20 minutes after my Ubuntu host boots up, then printing PDFs from my Windows 7 client works as it should.

I don't mind having to wait for the 20 minutes after boot (since my Ubuntu host boots up early in the morning and print jobs don't get sent until people start coming in - about an hour after Ubuntu boots up), at least it finally works!

Have no idea what the 20 minute delay on printing upon boot up is all about (Windows? Ubuntu? CUPS?)... however after that initial 20 minute wait after boot is over, printing PDFs from Windows 7 clients to Ubuntu host worked seamlessly.

---

